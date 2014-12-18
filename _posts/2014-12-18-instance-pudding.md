---
title: Instance Pudding Working Title
author: Dan Buch
twitter: meatballhat
layout: post
created_at: Thurs 18 Dec 2014 18:00:00 UTC
permalink: 2014-12-18-instance-pudding
---

<!--
* chatops at Travis in general
* legacy infrastructure and scaling difficulties
* moving capacity to EC2
* initial scripts for managing EC2 capacity
* introducing pudding
  * initial goals
  * basic features
  * open sourcing the things
  * heroku button
  * what we're adding/removing in the future
-->

This is a very exciting time for infrastructure and automation at Travis CI. As you may have noticed in a recent [blog
post](2014-12-17-faster-builds-with-container-based-infrastructure), we've begun moving some of our Linux build capacity
to EC2.  With this change comes new challenges and opportunities, and we've been busy building up tooling around how we
interact with the infrastructure.

Before delving too much into what we've built, it's worth mentioning that we like to talk to each other.  A lot.  I'm
personally very thankful for this, as a remote employee, since it means I'm able to lurk in our various [slack]()
channels or read through the backlog and have a decent idea of what's going on.  In addition to conversations my
(amazing!) teammates are having, I get to see activities from [github](), [pagerduty](), [librato](), and
[papertrail](), among others.  This is all part of our belief in the power of [chatops]().

Those familiar with chatops will know that it's not all about having alerts and such coming into the stream of
conversation.  Executing tasks from chat instead of context switching to a console and reporting that you've run some
commands is important both for visibility and knowledge sharing, not to mention being incredibly handy when all you've
got is your phone.

In preparation for moving Linux builds onto the EC2 infrastructure, we decided that the existing tools for managing EC2
instances simply weren't going to cut it.
