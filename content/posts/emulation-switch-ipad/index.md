---
title: Run Nintendo Switch Games on iPhone at 60FPS – Free, No Jailbreak Needed
date: 2025-04-03
tags:
  - emulation
description: 
draft: false
resources:
  - name: featured-image
    src: featured.jpg
---
If you thought the biggest gaming news was the upcoming Switch 2, think again. The emulation community has made a breakthrough: you can now run Nintendo Switch games on your iPhone or iPad at buttery-smooth 60FPS—all offline, with no jailbreak, no shady VPNs, and zero sketchiness.

{{< raw >}}
  <div>
<iframe width="100%" height="480" src="https://www.youtube.com/embed/vATS81L9vWA" title="MeloNX Nintedo Switch Emulation on Ipad Mini 7 - Mario Kart Gameplay" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
  </div>
{{< /raw >}}

---
## The JIT Struggle
Just-In-Time (JIT) compilation is a method used by emulators to dramatically improve performance by converting code into machine instructions while the program is running. Normally, an emulator has to interpret every single instruction one-by-one, which is slow. JIT speeds things up by compiling larger chunks of code in real time, allowing games to run closer to native speeds.
However, Apple has strict security policies that prevent unauthorized JIT execution on iOS devices. There are some workarounds like JITStreamer or SideJITServer but they all require an internet connection. StikJIT and StosVPN now bypass this restriction by enabling JIT locally, without external servers, making offline Nintendo Switch emulation possible on iPhones.
Here's the difference between no JIT vs JIT-enabled when running emulator on iOS.

[PPSSPP On iOS 17 (NO JIT vs JIT) iPhone XR](https://www.youtube.com/watch?v=zgdzy7q_dkU)

### What’s the Deal with StosVPN?
Before you panic—no, this isn’t some sketchy data-harvesting VPN. **StosVPN doesn’t connect to external servers**; instead, it sets up a **self-contained VPN server** on your own device. That means:
- **Zero** external connections
- **Zero** privacy intrusions
- **Zero** extra battery drain
It’s a win-win, and it all runs through **MeloNX**, an iOS port of the Ryujinx emulator, sideloaded via **SideStore** and **LiveContainer**.
🔗 **List of compatible games:** [MeloNX Compatibility List](https://melonx.org/compatibility/)

---
## Essential Tips Before You Begin
1. **Disable Low Power Mode** – Emulation needs full power.
2. **Keep required apps running in the background** – The setup is delicate; one wrong move can break it.
3. **Use Shared Folders for file transfers** – Dragging gigabytes of game files via Google Drive, USB? No thanks—use [mounted shared folders](https://www.wikihow.com/Access-a-Shared-Folder-on-an-iPhone-or-iPad).
![](https://i.imgur.com/N4qPi89.png)

---
## Installing SideStore
1. **Check prerequisites (no need to install Wireguard VPN as we will replace it with StosVPN) and pairing file instructions:** [SideStore Docs](https://docs.sidestore.io/docs/getting-started/prerequisites)
2. **Generate a pairing file:**
    - Download `jitterbugpair.exe`
    - Run it and transfer the `*.mobiledevicepairing` file to your phone
![](https://i.imgur.com/zrAO6vQ.png)

3. **Install SideStore:**
    - Install **AltServer** [Windows Guide](https://docs.sidestore.io/docs/getting-started/windows)
    - Hold **Shift + Click** the AltServer tray icon and sideload the SideStore IPA
4. **Final Tweaks:**
    - Install **StosVPN** from the App Store and enable it    
    - Open SideStore, pair it with the pairing file    
    - Refresh the app and remove previous AltServer certificates
![](https://i.imgur.com/T9DBMOM.png)

---
## Installing LiveContainer
SideStore limits the number of installed apps to three, but **LiveContainer** bypasses this restriction. Here’s how to install it:
1. **Download the LiveContainer IPA** from [HugeBlack’s fork](https://github.com/hugeBlack/LiveContainer/) Actions tab (requires GitHub account)
2. **Open SideStore with StosVPN enabled** and add LiveContainer IPA.
3. **In LiveContainer Settings:** Tap "Patch SideStore/AltStore" to reinstall it with tweaks.
4. **After installation:** Reopen SideStore/AltStore.
5. **Return to LiveContainer:** Tap "Test JIT-Less Mode"—if it says "Test Passed," you’re good to go.
6. **Install a second instance of LiveContainer** via the main LiveContainer app.
7. **In LiveContainer Settings: Set JIT Enabler to StikJIT (Another LiveContainer).**
![](https://i.imgur.com/IMz9BrU.png)

---
## Installing MeloNX & Enable StikJIT & Increasing RAM Limits
Apple limits apps to using only half of the device’s RAM, but **GetMoreMemory** by HugeBlack bypasses this restriction.
1. **Download MeloNX & memory entitlement:** [MeloNX Repo](https://git.743378673.xyz/MeloNX/MeloNX#readme) and **StikKIT IPA** from [StikJIT GitHub](https://github.com/0-Blu/StikJIT).
2. **Go to the Apps tab, add the latest StikJIT, MeloNX and memory entitlement** IPA files, and convert it into a shared app (hold -> settings).
4. **Enable file picker & local notifications in MeloNX settings.**
![](https://i.imgur.com/WZShBKo.png)

5. **Run memory entitlement and log into your account to enable the entitlement for:**
    - LiveContainer
    - LiveContainer2
    - MeloNX
    - If errors occur, clean up Keychain and try again.
![](https://i.imgur.com/7cBMAJR.png)

1. **Reinstall LiveContainer & LiveContainer2** to apply the configuration.
2. **Reinstall SideStore from the app (do not just refresh it).**
3. **Upload the pairing file in StikJIT on LiveContainer2 and enable "Auto Quit After Enabling JIT."**
![](https://i.imgur.com/tfLnIbt.png)

5. **Run MeloNX via LiveContainer1.**
---
## Adding keys, firmware, games on MeloNX
First-time setup:
1. Launch MeloNX via LiveContainer
2. Choose your `prod.keys` and `title.keys` files
3. Select your Switch firmware `.zip`
4. Go to settings and **enable extended RAM**
![](https://i.imgur.com/1JVjXah.png)

You're done! Just tap MeloNX from LiveContainer whenever you want to play, even offline. Add games (.NSP or .XCI) by tapping the ➕ button.

I won’t go into detail on how to acquired keys, firmware, and games since this involves piracy. 
As far as I know, aside from downloading illegally, you can extract your own keys and firmware from your own Switch. 
For, uh, testing purposes, here’s a little base64: 

```
S2V5cyAmIEZpcm13YXJlOiBodHRwczovL3Byb2RrZXlzLm5ldC8NCkdhbWVzOiBodHRwczovL25zd2dhbWUuY29tLw==
```

Some useful tips I’ve come across:
- Always download both the **game** and its **update file** for the best performance.
- Large files may get stuck during transfers due to MeloNX’s lack of a proper file transfer UI.
---
## Credits & Sources
This guide was compiled from various sources and contributions:
- **HugeBlack:** Developer of LiveContainer and GetMoreMemory
- **0-Blu:** Developer of StikJIT
- **MeloNX Team:** Creators of the MeloNX emulator
- **SideStore Team:** For enabling sideloading on iOS
- **Various GitHub Repositories & Documentation:**
    - [SideStore Docs](https://docs.sidestore.io/docs/getting-started/prerequisites)
    - [LiveContainer GitHub](https://github.com/hugeBlack/LiveContainer/)
    - [StikJIT GitHub](https://github.com/0-Blu/StikJIT)
    - [MeloNX Repo](https://git.743378673.xyz/MeloNX/MeloNX#readme)
- **r/EmulationOniOS** community, especially this post 
	- [How to install MeloNX and get it working with fully offline JIT activation. A step by step guide. : r/EmulationOniOS](https://www.reddit.com/r/EmulationOniOS/comments/1jq29ag/how_to_install_melonx_and_get_it_working_with/)
---
## Final Thoughts
Running _Tears of the Kingdom_ on an iPhone sounds like science fiction—but it’s real. Once it’s all set up, you’ll be gaming at full speed, offline, on hardware that was *should* be meant for this.
Even crazier? This lays the groundwork for full-blown VM emulation. Some users are already running macOS Sonoma on iPad using UTM.

![](https://i.imgur.com/N3brNGL.png)