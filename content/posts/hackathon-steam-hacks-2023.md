---
title: My STEAM Hacks 2023 experience
date: 2023-10-20
tags:
  - hackathon
description: 
draft: false
resources:
  - name: featured-image
    src: featured.jpg
---
*If you want to learn more about the technical details of how I built the app, please read the article here*



Today, I want to share my experience with you about the project I worked on during the Steam Hacks 2023 competition. Although my team did not win any major awards for this project, it was an incredible learning opportunity for me, particularly in terms of coding. Moreover, I also gained valuable insights into the collaborative process through working with my amazing new friend from Son La - Minh Chau.

## Background information about STEAM Hacks 
STEAM Hacks is a national hackathon organized by [STEAMS for Vietnam](https://steamforvietnam.org/) in collaboration with Ha Noi University of Science and Technology. It offers two tracks, **Hipster** and **Hacker**, catering to UX/UI designers and developers respectively.

![](https://i.imgur.com/s6u5jak.png)

*Although I initially had confidence in joining the Hacker Track, I ultimately decided to participate in the Hipster Track. This choice was driven by my desire to have better overall project management skills and to further enhance my UX/UI abilities. However, it turned out that I still had to write code for the team despite being in the Hipster Track. (you would know the reason later on this article)*

The hackathon consists of three rounds. The first round (Breaker Challenge) is an individual challenge with separate tracks: **Hipster** and **Hacker**. Each track would receive support by various workshops, covering the knowledge required to participate to the competition. At the end of the first round, participants from each track are required to submit an assignment that showcases their newly acquired knowledge. For **Hipsters**, this involves designing an e-commerce landing page with a high-fidelity wireframe created on Figma, along with user personas and user journey details related to their product. **Hackers** must submit a functional website developed using Flask framework and incorporating some form of "AI" feature.

150 participants from both tracks are then chosen for Round 2: Innovation Spirit, where they form teams of 2 **Hipsters** and 2 **Hackers** and choose from four tracks: Sustainability, Education, Mental Health, or Community. Only 15 teams advance to the final round, The Hacking Day, with 7 team awards and 2 individual awards. It seems like I came close to being recognized as one of the best **Hipsters** since I was invited for an interview among the Top 5 Best **Hipsters**, but I couldn't make it in the end though 😢 (interestingly, the recipient of the Best Hipster Awards was none other than Minh Chau, a fellow member of my team)

## My initial idea for both first and the next two round
After placing as a Top 10 Finalist in last year's Samsung competition, I couldn't help but feel a sense of dissatisfaction with my product. It lacked certain features I wanted to include, and there were numerous unresolved issues with the app's development. This drove me to participate in this competition, with a focus on creating another application to finish an overall optimized system for reducing e-waste. In the initial round, where I had to design a landing page for an e-commerce site, I immediately decided to develop a marketplace for trading refurbished devices. This solidified my determination to craft a comprehensive product idea for the subsequent rounds, even though I wasn't certain of advancing beyond round 1.

![](https://i.imgur.com/DC4cze5.png)

Recognizing the importance of further developing this idea, I dedicated significant time to meticulously designing wireframes for the project. However, due to personal circumstances, I found myself dangerously close to missing the round 1 deadline. Thankfully, only by submitting the final version just 30 minutes before the cutoff did I manage to make it on time (Pheww). You can access my completed assignment [here](https://drive.google.com/file/d/17_A1r65voE-_KqU7um1DyBIPl7loKEmG/view). This also qualified me for entry into the next round. Additionally, I had the honor of being recognized as one of the top five Best Hipster participants in the competition because of my performance on this round.

![](https://i.imgur.com/rTrjPDY.jpg)

## Round 2 - The bond and conflict arise
Upon receiving the email notifying me about the results and next steps, I also discovered that my old friend - Tu Linh - had also participated in the competition and qualified for the second round. The only difference was that he had chosen to join the Hacker track. After a brief discussion, I decided to join him along with two others: his friend Huy, and a randomly recruited girl named Minh Chau. While the three of us were from Hanoi and Minh Chau hailed from Son La, it was her who took the initiative throughout our collaboration (and also contributed the most). That was also the reason why she became a leader for my team. Well, she is really good at project management and business analytics, but underperforming in software development. That also the time I became the Software Development Lead 

![](https://i.imgur.com/u8s4Tp3.jpg)

The initial meeting went smoothly as we all introduced ourselves and comfortably shared our ideas from the first round for brainstorming purposes. While I don't want to come across as boastful, it became apparent to me that my assignment was the only one with the potential to win major awards. Huy and Linh from the Hacker Track supported my viewpoint. They agreed that my already beautiful interface and adherence to guidelines would significantly reduce the time spent on front-end development. However, Minh Chau had some reservations. She did like my idea, but she stated that it just so "ordinary" and "unsafe". After several more meetings filled with debates and discussions, we eventually reached a consensus on what we should create for rounds 2 and 3: a counterfeit product verification system.

You might be wondering, is that all? Why were you so easily compromised? Well, I did attempt to negotiate with her. However, as mentioned earlier, choosing the idea of creating a marketplace for refurbished devices would result in my team being disqualified from the STEAM Hacks competition if they discovered any correlation or signs of idea copying from my Samsung product last year. On another note, my primary motivation for participating in this competition was not solely to complete my Samsung product but rather to acquire and expand my knowledge and skills.

## On the development process
Wow, what a nightmare that was. I can't even begin to describe how unproductive the environment was compared to our typically smooth and comfortable team discussions. I don't want to point fingers or be too hard on myself, but it's clear that none of the Hacker members on our team were pulling their weight. It's not entirely their fault though; they excel in competitive coding, but they weren't adequately prepared for web development or a hackathon like this. So, I found myself having to join them in tackling the code development.

Furthermore, our team was currently facing a conflicting idea with our leader regarding the counterfeit product verification system. Unlike other student projects that typically involve education or mental health, this idea feels challenging for us to create something meaningful. Initially, our leader proposed using AI to detect fake patterns or incorrect labels, but our team lacks the competence in developing AI-related features. Additionally, implementing such a system seemed impossible and unproductive due to the vast variety of products and their unique fake versions. Moreover, there are also concerns about implementation costs and potential returns.

Well, turns out, every cloud has a silver lining. Firstly, despite my limited technical knowledge, I embraced the opportunity to learn backend development on my own, driven by a strong determination and purpose. This made me feel alive and empowered. Specifically, I was fortunate to have access to the [FlutterFlow](https://flutterflow.io/) Education program, which enabled me to quickly learn and utilize their user-friendly software for creating meaningful applications. This greatly reduced our front-end development time and expanded my knowledge of this powerful tool. Furthermore, I acquired proficiency in Flask to develop an API backend application that automatically serves ML models trained through the [Teachable Machine](https://teachablemachine.withgoogle.com/) platform. This saved me the tedious task of manually researching and collecting data for training models. In short, this challenging experience has taught me invaluable skills and knowledge.

Coming back to the idea conflicting issue, because I initially had doubts about the leader's counterfeit verification concept, I decided to develop the refurbished marketplace feature alongside it. However, I also noticed her dedication and effort towards this idea, despite its nearly impossible implementation. So I had to come all the way to redevelop the application. Finally, on the last day, things became even more intense than before as we submitted our application just five minutes before the deadline. Although there were still flaws and room for improvement, we managed to qualify for the next round - the Hacking Day...

![](https://i.imgur.com/j8VNQZP.png)

## Final revision & new trajectory
Entering the final round was unexpected for us. Our product was only halfway developed and didn't efficiently solve our problems. When we received the results for the second round at midnight, we celebrated together briefly before diving into a meeting for planning and improvement. During this meeting, we had a tense debate as Chau and I wanted to continue finishing the project for the learning experience, while Linh and Huy would only participate if we had a chance of winning a major award. After much discussion, we agreed to aim for the Pitching Award.

I was extremely busy during this time as I had to focus on my IELTS practice and essay writing. Additionally, I indulged in my habit of tinkering with tech devices and took the opportunity to develop my own server using an old case my mom had brought home. However, returning to the topic of STEAM Hacks, after resolving our conflicts, we came up with a new idea to improve the process of verifying counterfeit products. This involved implementing barcode scanning and utilizing NLP instructions. We discovered that solely using images to identify fake products was not as effective as incorporating physical interactions such as smell or embossed marks. This idea also stemmed from my recent knowledge about NLP and [LangChain](https://www.langchain.com/) that I coincidentally learned about just a few weeks ago. And so, without further ado, our journey continues.

Our journey began just three days before the Hacking Day, thanks to my procrastination. The day before the final, we had a meeting scheduled with our counselor and advisor. It was embarrassing because our team had barely finished the final version of our product. However, this gave us an opportunity to ask our advisor important questions regarding the challenges we were currently facing. As I delved deeper into NLP and specifically LangChain, I discovered that it was poorly developed and relied heavily on tokenization. After a lengthy discussion, we also learned some valuable techniques for optimizing it. And in the same day, we were able to complete our underperforming product, making it ready for the presentation scheduled for the following day.

On the day of our presentation, nothing out of the ordinary occurred. However, one memorable moment stands out in my mind. Our team made the decision to demonstrate the live usage of our application. Unfortunately, it didn't go as planned and resulted in uproarious laughter from the audience. Despite this setback, we were able to complete the presentation without further complications (although our question and answer session left much to be desired). Although our team did not receive any awards in the competition, we still managed to capture a photo with smiles all around.

![](https://i.imgur.com/E17gMsG.jpg)
