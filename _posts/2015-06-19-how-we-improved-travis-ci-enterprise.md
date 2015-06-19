---
title: How We Improved the Installation and Update Experience for Travis CI Enterprise
created_at: Fri 19 Jun 2015 14:30:00 CEST
author: Mathias Meyer
twitter: roidrage
layout: post
permalink: 2015-06-19-how-we-improved-travis-ci-installation
---
Building out the [on-premises version of Travis
CI](https://enterprise.travis-ci.com) has brought some interesting
challenges for us. Beyond making changes to our codebase to talk to GitHub
Enterprise and allows hosting Travis CI in a custom setup, a lot of work went
into packaging and the installation process.

But these aren't the only challenges of turning a SaaS product into something
that's easy to run on your own infrastructure. There's updating,
trouble-shooting when there's an issue (especially hard when the infrastructure
is unreachable to us), moving an installation, creating, checking, validating
and keeping track of license keys, monitoring, logging, backup strategies, and
so on. The list of things you need to keep in mind feels almost endless.

We've had experience with most of these things from running Travis CI in
production for our hosted platforms, but we wanted to make the installation
process as simple as possible. Our platform is a fairly complex set of
components and apps, which aren't easy to run on your own, but easy for us to
operate and deploy.

We bundled up all of Travis CI into two Docker images, a challenge on its own,
but we wanted to make it as easy as possible to download and install it.

Initially, we gave our customers a shell script to run on the machine that would
host their Travis CI Enterprise instance. We'd provide them with a manually
generated license key, and they'd be set up within a relatively short period of
time.

But it still left us with the tasks of managing the license keys and finding a
means to update running setups. The latter in particular is an interesting
challenge when you create an on-premises version of a SaaS product.

The process above took us to get our first couple of customers set up with
Travis CI Enterprise. But just from the first experiences, we've been collecting
an ever-growing list of things we want to improve around making it easier to
ship and maintain Travis CI Enterprise for our customers.

Just around the time we started planning and prioritizing some of the open
issues, we were introduced to [Replicated](http://replicated.com), a new
product that gives SaaS products like ours a platform to easily build and deploy
an on-premises version.

Their team has set out to tackle an interesting problem, and even their earliest
releases promised to make our lives a lot easier to get our on-premises product
into more customer hands much faster than we could before.

They've solved issues that we've had yet to solve at that point: backup
management, audit logging, support bundles to make supporting our customers
easier, updating existing installations and license management, to name a few.

After the installation, Replicated provides our customers with a management
interface, giving them a quick overview of the system, including monitoring
data, the currently running version, and notifications about new versions.

![](http://s3itch.paperplanes.de/Travis_CI_Enterprise_Installer_2015-06-18_16-45-04.jpg)

New releases of Travis CI Enterprise can now be shipped to customers as they
need it, and usually requires them to follow the notification telling them about
a new version and install it.

Replicated has allowed us to make our installation process a lot easier and,
beyond that, have built tools that we ourselves would've had to build. Tools
that a lot of startups need to make the jump from a SaaS offering into the very
different world of Enterprise.

The video below shows the process from all the way to a running installation:

<iframe width="600" height="345" src="https://www.youtube.com/embed/ViN-qkcovL0"
frameborder="0" allowfullscreen></iframe>

Want to try out the experience yourself and run [Travis CI
Enterprise](https://enterprise.travis-ci.com) on your own infrastructure? Shoot
us an [email](mailto:enterprise@travis-ci.com) and we'll get you set up in no
time, thanks to [Replicated](http://replicated.com).
