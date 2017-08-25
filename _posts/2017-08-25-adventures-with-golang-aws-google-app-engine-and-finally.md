---
layout: post
comments: true
title: "Adventures with Golang, AWS, Google App Engine and finally..."
date: 2017-08-25
categories: [blog, cs3216]
tags: [project, programming, backend, cloud]
---
Taking a leap of faith, my project team has decided to use Golang on our server-side for assignment 1: Facebook application! As Backend Engineer of the team, this meant that I needed to get up to speed with developing as well as deploying for Golang (so my front-end engineer can actually start using my APIs). At the end of the mid-point submission today, there were certainly some notable achievements... as well as some interesting experiences... *black moon emoji*

## Why Golang (or Go)?

![gif: Golang]({{ site.url }}/assets/media/golang.gif)

Go was designed with scalability in mind and scaling up an application often means running many server-side sub-tasks concurrently. Built-in features such as goroutines (think threads, but super lightweight and easy to implement) and channels also mean that our application will be able to handle concurrency easily when it scales up in the future.

Unlike Python, Go compiles to binary instead of being interpreted every time the application is run. This increases code execution performance. Go applications also support cross compiling and can be distributed to run on any machine. This can be useful when deploying to production servers and other teammates' local machines using the executable binaries, as Go doesn't even need to be installed.

Go is a simple and easy to understand programming language, which greatly increases its readability given the small language specs document. Moreover, Go's powerful error checking is able to detect unused variables as well as imports to keep your code as well as application lean and simple. The compiler detects errors such as missing packages and invalid operations during the build process, saving us much development time from searching for bugs.

## That being said...

![logo: EB]({{ site.url }}/assets/media/eb.png)

Despite following several Golang deployment tutorials found on Medium, a few tech blogs and event the official AWS docs (http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/go-environment.html), the deployment did not work according to plan :( Specifically, the docs instructed us to use one of the two following ways to deploy a Golang app to Elastic Beanstalk:

  - Provide a source bundle with a source file at the root called application.go that contains the main package for your application, or
  - Provide a source bundle with a binary filed called application.

(Process of deploying "hello world" Go app begins)

We repeatedly received the error of "unable to launch application as the source bundle does not contain a Buildfile, Procfile or an executable". Referring back to the docs, we saw that complex Go apps require those files to specify the commands to build and run the application. However, simple apps like ours shouldn't, and moreover, the problem was not solved even after we added both a Builfile and Procfile...

## Then came Microsoft Azure... :')

![logo: Azure]({{ site.url}}/assets/media/azure.jpg)

Yay! We found that the onboarding process for Azure App Service was both **smooth** and **simple**, as opposed to Google App Engine and AWS, both of which we experimented with prior. Azure App Service was also **well-documented** (which thus also serves as a personal reminder to me on the importance of good documentation, maybe more on this next time)!

Ok... despite ranting about AWS... our database was still deployed on AWS RDS Free Tier (one big plus is that it's *free*~). The data that our app needs to store is structured, relational and joins-heavy. Following these requirements, we have chosen to launch a MySQL instance on AWS RDS :)

## More next time on backend dev & infrastructure related topics ^^

Cheers~ and have fun chionging assignment 1 everyone!
