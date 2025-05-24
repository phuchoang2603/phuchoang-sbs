---
title: Migrating and Rebuilding My RKE2 Kubernetes Cluster on Proxmox
description: 
date: 2025-05-21
tags: 
  - self-hosted
  - devops
  - kubernetes
draft: false
resources:
- name: "featured-image"
  src: "featured.jpg"
---
*Here's the link to my previous blog post on this journey: https://phuchoang.sbs/posts/terraform-ansible-proxmox-k8s/*

Over the past few days, I tried deploying an RKE2 Kubernetes cluster on my home Proxmox setup. My initial setup worked, but it quickly became apparent that things weren’t stable or sustainable. RKE2’s auto-deployment behavior, the embedded etcd database, and service load balancing all caused performance and manageability issues. It wasn’t “buggy” in the literal sense, but definitely felt rigid and inefficient — not something I would consider a best-practice deployment for a long-term homelab setup.

So I decided to start refactoring the cluster.

---

## Switched to a 3-Node Control Plane

Originally, I had 2 RKE2 server nodes. I replaced this with 3 to ensure quorum and enable proper leader election and failover. Kubernetes' control plane components like etcd and the scheduler require a majority of nodes to reach consensus, and an odd number ensures this can be calculated unambiguously. With 3 nodes, the cluster can tolerate the failure of one control-plane node while maintaining availability.

---

## Changed IP Scheme from `/24` to `/16`

The original setup used the `192.168.69.0/24` subnet. It worked, but quickly felt limiting when I started scaling VMs and reserving address blocks for DHCP, load balancers, and Proxmox infrastructure.

So I restructured the network to use the `10.69.0.0/16` subnet, divided as:

- `10.69.1.0/24`: Static IPs for Proxmox, K8s nodes, internal services
    
- `10.69.2.0/24`: DHCP range (start at `.2.512`, limit 256)
    
- `10.69.3.0/24`: Reserved for Kubernetes LoadBalancer services
    

Proxmox itself was reconfigured to use `10.69.0.1` as its IP and DNS server. Broadcast and netmask were updated accordingly to reflect the expanded range. This gives me much more flexibility to scale and isolate various components without running into IP conflicts.

---

![change-ip](https://live.staticflickr.com/65535/54535321190_8bf58464bf_b.jpg)

---

## Gave Up on External Database (Kine)

At one point I considered replacing etcd with an external database using Kine, hoping it would be lighter on disk I/O. After some reading — [this post](https://martinheinz.dev/blog/100) was helpful — I decided it wasn’t worth the added complexity. Kine is a workaround for etcd, not a full solution, and introduces its own overhead and caveats.

---

## Migrated from MetalLB to kube-vip

I wanted to simplify and consolidate IP assignment across control plane and service load balancers, so I switched from MetalLB to [kube-vip](https://kube-vip.io/docs/usage/cloud-provider/). It’s now handling both control plane VIP and LoadBalancer services.

To do this:

- I disabled MetalLB entirely (by commenting out its deployment in the Ansible roles I use).
    
- Enabled `svc_enable: true` in the kube-vip manifest to allow service load balancing.
    
- Followed the [official kube-vip cloud provider installation guide](https://kube-vip.io/docs/usage/cloud-provider/#install-the-kube-vip-cloud-provider) to deploy its controller.
    

So far, it works more reliably and integrates cleanly with RKE2’s native load balancer behavior.

---

## Ingress Controller + TLS: nginx vs traefik

I initially tried deploying nginx as my ingress controller with cert-manager for TLS. The plan was to route external access through HTTPS and use ingress rules for reverse proxy and load balancing.

That didn’t go smoothly:

- I first attempted to use Traefik (RKE2’s default), but configuring it through HelmChart CRDs was too opaque and hard to control.
- Then I switched to nginx via a HelmChart manifest — but forgot to rename the `.j2` file to `.yaml`, which caused the Helm controller to silently fail.
- When I finally got the HelmChart to load, cert-manager couldn’t be fetched via remote repo URLs. I had to download the `.tgz`, base64 encode it, and inject it via the `chartContent` field manually.
- Even after that, cert-manager DNS-01 validation failed until I updated my DNS nameservers to use Cloudflare explicitly. The default nameserver (`/etc/resolv.conf`) pointed to an internal resolver, which tried to resolve external domains like `acme-staging-v02.api.letsencrypt.org.my-domain.local` — resulting in failed lookups.
- In the end, I found out that I need to specify the DNS server when initialize in Terraform
    

Eventually, I circled back to Traefik — mainly because I’m planning to integrate Authentik for application authentication, and Traefik makes that easier to manage with native middlewares and plugin support. I found [this issue](https://github.com/rancher/rke2/issues/5928) showing how to re-enable Traefik in RKE2 by simply setting the appropriate value in the HelmChart manifest — something that’s still not properly documented.

For cert-manager, I’m likely reverting to basic manifest deployments rather than using HelmCharts. It’s simpler and more transparent.

---

## Longhorn for Storage

I also deployed [Longhorn](https://longhorn.io/docs/1.8.1/deploy/install/) for persistent storage. I added:

- A new Terraform module to provision extra VMs for storage
    
- A mirrored Ansible role similar to my existing `add-agent` role, but with `Longhorn=true` labels
    
- Installed `iscsi` and `nfs-common` on each Longhorn node
    

I tested Longhorn access through Traefik and cert-manager to confirm that HTTPS access worked as expected.

![](https://live.staticflickr.com/65535/54541161701_cee5d47fa4_b.jpg)

---

## What’s Next

I’m now looking into deploying Argo CD for GitOps-style CI/CD. With kube-vip, Longhorn, cert-manager, and Ingress all functional, the core of the cluster is ready. Automating deployments with Git is the next step.