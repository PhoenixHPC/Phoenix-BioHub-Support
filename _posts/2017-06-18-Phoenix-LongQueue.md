---
layout: post
title: Use long queue with Phoenix
categories: journal 
tags: [phoenix, news, intro]
comments: true
image:  
  feature: cards.jpg
  teaser:  cards-teaser.jpg
  credit:
  creditlink: "adelaide.edu.au/phoenix"
---

Phoenix is now support "longq" partition, which has the wall-time expanded to 7 days as opposed to the standard 3 days on "batch" partition. Nevertheless, it is a good idea to avoid excessive use of longq. One is because the long wall-time processes are vulnerable during system/node down time; long wall-time tasks also take longer for a scheduler to reserve appropriate resources (i.e. longer, sometimes substantial longer waiting time). Instead, a recommended approach would be either adopting "divide and conquer" strategy or implementing "checkpoints" for your pipeline (many software already provides such a function, just a matter of enabling). Checkpoints in short provides a snapshot of the application status, which can be used to reconfigure the application and restore the process from where left off. Phoenix Team is actively developing a system wide implementation of checkpoint, which in turn will automatically checkpoint the running jobs and provide an opportunity to automatically resubmit jobs once hard wall-time has been reached. Please keep an eye out for the development in this space.

