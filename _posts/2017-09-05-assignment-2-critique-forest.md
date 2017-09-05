---
layout: post
comments: true
title: "Assignment 2 Critique - Forest"
date: 2017-09-03
categories: [assignment, cs3216]
tags: [assignment, critique, forest, productivity]
---
As part of Assignment 2: Application Seminar, I will be reviewing the productivity app, Forest.

## Summary of in-class presentation by Team Forest

During class on Monday, Team Forest presented a well-researched analysis of Forest's strength, weakness and business model. Here I will summarize the main points from their presentation:

  Strengths of Forest: Clean UI, Gamification
  Weaknesses of Forest: Better social feature (e.g. Whatsapp message & productivity challenges), widgets and notifications to improve customer retention
  Business model: Direct correlation between smart phone addiction and Forest app usage, however the paid app business model may not be the most ideal monetization strategy. Instead Forest could consider a freemium model in order to win over users on free productivity apps.

I found the team's conclusion that freemium could be more suitable than paid app model to be extremely insightful. While seemingly counter-intuitive at first glance (isn't it better to make customers pay first and regret later?), their analysis is done in context of the productivity apps space. Many productivity apps, even those that computationally heavy functions (comparative to Forest) such as Meekan, Quip, Canvas, Postify, TinyScan, SyncSpace, as well as similar stay-focused apps, such as Be Focused, Daily Habits and Focus Matrix (on iOS), are currently all available for free. Some of these apps have premium features than can be unlocked by paying customers, or may adopt business models similar to Trello/Asana/Slack that offer enterprise price plans. With a solid product, it is possible to make more profit by offering a "sneak peak" to users and tempting them to switch to a paid subscription.

## My thoughts on Forest

Because I was stingy and didn’t want to buy the Forest app on my phone **black moon face** I tried using the Chrome extension version of it. According to the description, I should be able to blacklist some websites and my tree will be killed if I visit websites on my blacklist. However, the blacklist feature is not very discoverable. Until now I still don’t know where to configure my blacklist…

![screenshot: Forest]({{ site.url }}/assets/media/Forest-1.png)

While I agree with Forest’s mobile-first approach because of prevalent smartphone addiction and obsession today, I also feel that Forest has a pretty good use case in the comparatively more “traditional” browser space to help people stay focused on work or study while staying away from certain blacklisted sites. The value proposition of the blacklist-based browser version is slightly different from a mobile approach, in that users first recognize what websites are those that consume a lot of time and attention but do not contribute to productivity (for my case, it would be Facebook, YouTube and Gmail). This is the first step to breaking a habit of visiting those sites and getting distracted while doing work! Forest app on browser helps a lot in this respect.

After seeing Forest, I think I gained more ideas for building gamification apps. Watching a tree grow is one of those oddly satisfying things you know? And this concept could be harnessed to motivate users to accomplish difficult tasks. One idea would be a new feature added to CodeCrunch. Sometimes when working on programming assignments, it is very tedious to keep fixing your code based on the test cases that CodeCrunch says you failed. Some gamification idea could be, have a cat meow a song to you when you pass a couple of test cases. When users increasingly pass more test cases, you get two cats meowing a longer song; finally, when all test cases pass, you have a choir of cats meowing Celebration to you! You get the idea!

## More thoughts (rambling, technical)

I was very impressed by the team’s analysis of the Forest app’s technical implementation, using a combination of React Native, SQLite, Node.js and Express. This bears a (albeit small) resemblance to the popular web dev stack, MEAN stack (MongoDB, Express, Angular, Node.js). In comparison to the MEAN stack, the Forest team’s choice of React Native over AngularJS + NativeScript, and SQLite over MongoDB, are both sound choices that I agree with.

While generic database-driven apps might favor NativeScript due to the fact that UI is typically not resource-intensive enough to justify a more platform-focused approach, React Native’s speed of rendering and execution allows developers to create performance-focused cross-platform apps that can run on the same code base, yet still leverage platform-specific components at will. Source: [Back&](http://blog.backand.com/angular-2-nativescript-vs-react-native/) In my opinion, Forest’s selling point lies more in aesthetic appeal (clean interface and trees are satisfying to look at) i.e. awesome UI, rather than heavy-lifting involving data. In this sense, React Native emerges as a more suitable option when looking to implement lightweight rendering as well as good native device integration (to contribute to good UI/UX regardless of device used) which are criteria relevant to Forest’s appeal and value proposition.

Similarly, a lightweight local (client) storage like SQLite is well-suited to Forest, which is server-less in design and is lightweight enough to store all tables and data into a single file on host machine. A NoSQL alternative such as MongoDB would only be suitable if data was unstructured and data to be replicated/distributed for the app to better scale. The team showed that it is important to make architecture decisions based on the app’s value proposition and the user’s need, rather than blindly follow trends.
