---
title: "Xcode 6 update postmortem"
created_at: "Wed 21 Oct 2014 17:00:00 UTC"
author: Henrik Hodne
twitter: henrikhodne
layout: post
permalink: 2014-10-22-xcode-6-update-postmortem
---

We would like to apologise to everyone who was affected by the issues related to
our Xcode 6 rollout. This update revealed a lot of issues in our workflows, and
we've been working hard to find ways to improve these rollouts in the future.

## What happened?

On September 24th, we made our first attempt at rolling out the Xcode 6 update.
We had planned to make this rollout earlier, but due to some issues with
connecting to our template VM that we use to prepare images, we were unable to
get this update out earlier. As soon as we rolled out this image, we noticed
that we were no longer able to boot VMs, rolled back and started to investigate.
We quickly localised the error to be caused by the image no longer being on the
VM hosts, and started re-distributing the images.

We were going to make a second attempt at rolling out the image on September
25th, but we had just had a capacity upgrade and needed to wait for the image to
get distributed to the new machines. On September 26th this was done and we made
a second attempt at rolling out the image. This time VMs were booting, but we
were unable to connect to them. After trying a few different things, we
discovered that our capacity update had introduced some new versions of our
virtualisation software, which took another couple of days to diagnose and fix.

On October 1st, we found a fix for this issue and rolled out an image that had
Xcode 6 and was booting just fine. Soon after rolling out the image we started
receiving reports that iOS simulators were no longer launching properly. We
realised that this was a change in Xcode 6 that caused us to be unable to launch
the iOS simulator over an SSH session, which is how we run our build scripts
(several Apple Bug Reports have been filed for this, [this][radar] is one that
has been reposted publicly). We tried out different workarounds for this, and
ended up having to write our own workaround that we verified and deployed on
October 6th.

[radar]: http://openradar.io/18321293

## Why did it happen?

There were several things that caused these issues.

- Historically we have only had the ability to have a single image live on our
  OS X cloud. This meant that we were unable to test Xcode 6 until it was
  publicly released, and we were also unable to roll back and test the
  workarounds in a staging environment as we needed the image to be live to test
  the workarounds.
- Our OS X infrastructure partner is located on the U.S. West Coast, while the
  Travis CI team members working on this issue are located in Northern Europe,
  which means there's a limited window of time when both are online to roll out
  new changes, causing any new rollout to usually take a day to complete.

## What are we doing to improve?

We now have the ability to internally test new images without making them the
production image. This has several side effects:

1. We can now test new versions of Xcode as soon as Apple releases the beta
  versions, which we are going to do.
2. It also means that we can test the build environment updates before rolling
   them out.

Using these new abilities, we plan on changing the way we roll out our
environment updates, see the next section for more details on that.

We're also working on distributing the knowledge about the OS X infrastructure
more among the team to prevent the time zone issues and to have more people on
hand when things go wrong.

## A new way to roll out build environment updates

These updates have always caused a lot of issues for everyone who depends on
Travis CI. One of the main reasons for this is that once we made the new image
live, there was no way to roll back unless we rolled back the image for
everyone. Starting with the next update, we're changing how these rollouts work:

1. Announce the update on our blog, along with a list of what has changed and a
   way to opt in to the updated build environment by adding a setting to the
   .travis.yml.
2. Collect feedback from everyone who tests the new environment, and roll out
   changes to the beta image.
3. Once we are happy with the beta image, make it the default production image.
4. If there are any major issues we missed, roll back.

We believe that this way will be much smoother for everyone. We're currently
working on an update that updates to Xcode 6.1 and iOS 8.1, which we'll roll out
in this manner. Expect a blog post with more details about that soon.
