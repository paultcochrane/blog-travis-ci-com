---
title: "Where did the sudo go?"
created_at: Tue Mar 31 13:26:49 UTC 2015
author: Dan Buch
twitter: meatballhat
layout: post
permalink: 2015-03-31-where-did-the-sudo-go
---

<figure class="right small">
  <img src="/images/where-did-the-sudo-go.gif">
</figure>

To our wonderful community members and customers testing on Linux, we want to
make sure you're aware of some exciting changes we've been making.

In recent
months, we've made announcements about our [container-based
infrastructure](2014-12-17-faster-builds-with-container-based-infrastructure) as
well as having hinted at the [existence of
addons](http://docs.travis-ci.com/user/apt/) that [enable more
projects](2015-03-19-uc-berkeley-calsol-team-runs-on-travis-ci) to move to
container-based.

The next big step is to route *newly-activated Linux projects* to containers
under the following conditions:

* [No `sudo` usage is
  detected](https://github.com/travis-ci/travis-core/blob/7a360299c19011cbd3c0f2bf099a16600048e210/lib/travis/model/job/queue.rb#L44-L48)
in any of the custom build stages
* The date of repo activation is [*after* a configured
  cutoff](https://github.com/travis-ci/travis-core/blob/7a360299c19011cbd3c0f2bf099a16600048e210/lib/travis/model/job/queue.rb#L88)

At the time of this writing, the cutoff date is February 14th, 2015.  This means
that any Linux projects activated after February 14th that do not contain
explicit `sudo` (or `ping`) usage will be routed to the container-based
infrastructure.

## HOW COULD THIS HAPPEN?

Don't worry!  If you really truly need `sudo`, there's a very simple way to get
it back:

``` yaml
# Opt into fully virtualized infrastructure
sudo: required
```

That being said, we hope you will take a look at our [APT
addon](http://docs.travis-ci.com/user/apt/) to see if it
meets your needs.  The container-based infrastructure is on Amazon EC2 with
autoscaling, and so promises short to nonexistent queue wait times, as well as
offering better performance for most use cases.

If you have a use case that's not currently being addressed by an addon, please
reach out to support@travis-ci.org.

Happy testing!
