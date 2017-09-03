---
layout: post
comments: true
title: "Google Analytics Fun"
date: 2017-09-03
categories: [blog, cs3216]
tags: [project, analytics, business, marketing]
---
Mad rush towards the final submission deadline for assignment 1! This is the first time I've worked with web development within such a short timeframe and with a fully functioning end product in mind (as opposed to proof-of-concepts we typically build for hackathons). As part of assignment 1, I've also got the opportunity to work with Google Analytics for the first time. From thinking about the use case to which we can apply Google Analytics (and make sense in doing so), to look at documentations and open-source modules that can help us integrate Google Analytics seamlessly into our application, it was definitely a fresh experience!

## Why Use Google Analytics?

![logo: GA]({{ site.url }}/assets/media/ga.png)

Software is never built in isolation from users. Therefore users' interactions with software that we create ought to be of concern to us, whether you are a programmer, a product manager, a designer, a business and marketing guru...

Based on my research on Google Analytics and its use cases, I found that the most common way to use Google Analytics to bring business value include: finding out where visitors are coming from (helpful for market segmentation, targeted marketing and advertisements and customizations perhaps), through which channels visitors are discovering the site (helps in evaluating marketing efforts e.g. Facebook Ads, other social media channels etc.), and keywords used by visitors in search engines in eventually accessing our site (helpful in improving SEO).

## Seems like Google Analytics is useful for business. Why should a programmer care?

Up till this point, it seems like most benefits of Google Analytics concern the business. Why should programmers still care about Google Analytics?

To me, the most obvious reason would be that programmers today cannot work in complete isolation from the business. Being about to apply analytics and obtain data across different platforms (for example, if you launched a product on both web and mobile), view (customized) reports and data in a digestible manner, track goals and so on, are important in helping programmers make decisions on platforms and features. For example, if we can find patterns in how web and mobile users differ in their interactions with our site (for example, in terms of the pages they visit), it could signal deeper issues concerning user interface and responsiveness of our site. Both are important points to note if we want to create software with not just great features, but also great features that can be fully utilized by our users. Tracking performance and usage can also help programmers better identify and focus on features that matters and make a big impact on user satisfaction.

## By Developers, For Developers

![diagram: GA]({{ site.url}}/assets/media/ga-diagram.svg)

My overall experience with Google Analytics (so far) has been that documentation (https://developers.google.com/analytics/) is up-to-date and easy to understand, with a couple of libraries and SDKs that developers can utilize for tracking depending on your platform of interest (web, android, iOS for example). For my peers who are also using React on the frontend, you might find react-ga (https://github.com/react-ga/react-ga), an open-source React Google Analytics module, to be useful. Just npm it :-)
