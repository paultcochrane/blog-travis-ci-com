---
title: "State of the Mac infrastructure on Travis CI"
created_at: Mon 20 Apr 2015 09:24:35 EDT
author: Hiro Asari
twitter: hiro_asari
layout: post
permalink: 2015-04-20-state-of-the-mac-infrastructure-on-travis-ci
---

In recent weeks, many of our Mac users have asked when they can
test their code written for Xcode 6.2 and 6.3 on Travis CI.

I would like to shed light on the status of our Mac infrastructure
in a bit more detail today.

As demands for our services on the Mac grew, we reevaluated our
Mac infrastructure, and decided that it was time to revamp
it.

<figure class="right small">
<img src="http://upload.wikimedia.org/wikipedia/commons/thumb/2/29/Virginia_tech_xserve_cluster.jpg/360px-Virginia_tech_xserve_cluster.jpg"/>
<figcaption>Photo (CC-BY-SA) 2008 by <a href="https://www.flickr.com/photos/cipherswarm/2414578959/">Christopher Bowns</a></figcaption>
</figure>

Our goals are:

1. Stable and reliable infrastructure for OS X builds
1. Faster updates to the build environments, including offering newer Xcode SDK updates

## State of the Mac Infrastructure

As we indicated in [a previous blog post](2015-04-09-this-week-in-travis-ci),
we continue to make great progress toward getting the new
Mac infrastructure ready for production use.
This is our Mac team's top priority.

We are testing the new infrastructure with the current images (Xcode 6.1 and 6.1.1)
as well as a beta image with Xcode 6.2.

While it is not easy to estimate,
we hope to roll out the new Mac infrastructure within a couple of weeks.

## What about Xcode 6.3?

Once we have the new infrastructure out, we will tackle
the Xcode 6.3.

There is a bit of unknown here, because Xcode 6.3 requires OS X 10.10 (a.k.a. Yosemite).
The new infrastructure service provider is running on a version of
virtualization software that does not officially support 10.10.
Offering it to our users may involve some extra work, but we will
do what we can to make it happen.

We will have another blog post to address this
in more detail before then.
