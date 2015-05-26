---
title: "Xcode 6.3 Beta general availability"
created_at: Tue May 26 16:44:41 UTC 2015
author: Dan Buch
twitter: meatballhat
layout: post
permalink: 2015-05-26-xcode-63-beta-general-availability
---

I'm happy to announce the general availability of our Xcode 6.3 beta.  This
program is long overdue, but we're feeling confident about the stability of the
offering thanks to the invaluable feedback from many private beta customers.

Opting into the beta will require the following in one's `.travis.yml` in
addition to either being a multi-os configuration or a language that is routed
to OS X by default:

``` yaml
osx_image: beta-xcode6.3
```

**Please note**: the config string is `beta-xcode6.3`, although the exact
version is Xcode 6.3.1.

## The details

Getting Xcode 6.3 to work on our virtualization platform would not have been
possible without the help of our amazing infrastructure partners at
[MacStadium](http://macstadium.com/).  As Xcode 6.3 requires OS X 10.10
Yosemite, this meant we had to choose between running Yosemite in an unsupported
configuration on vSphere 5.5 or upgrading to vSphere 6.

Thanks to the agility and responsiveness of our MacStadium friends, half of our
vSphere 5.5 cluster (less than 2 weeks old at the time) was reprovisioned into a
new vSphere 6 cluster in under 3 days.

## Next steps

Being able to run Xcode 6.3 on Travis is nice, but as said before it's long
overdue.  We're already hard at work on being able to offer future Xcode
versions as early as possible, as well as breaking the coupling between OS X VM
images and Xcode versions so that we can offer more than "current" and "beta" at
a given time, and allow customers to pin to the exact version(s) they need.

The current plan is to investigate the feasibility of on-demand Xcode version
installation, then to move all remaining OS X capacity to our vSphere 6 cluster.

We'll be sure to announce early and often when these new features and changes
land.  Happy testing!
