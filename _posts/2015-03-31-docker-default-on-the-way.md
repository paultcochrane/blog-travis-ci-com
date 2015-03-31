---
title: "Linux on Docker by default is on the way!"
created_at: Tue Mar 31 13:26:49 UTC 2015
author: Dan Buch
twitter: meatballhat
layout: post
permalink: 2015-03-31-docker-default-on-the-way
---

In recent months, we've made announcements about our [container-based
infrastructure](/2014-12-17-faster-builds-with-container-based-infrastructure) as
well as having hinted at the [existence of
addons](http://docs.travis-ci.com/user/apt/) that [enable more
projects](/2015-03-19-uc-berkeley-calsol-team-runs-on-travis-ci) to move to
container-based.

Our Container-based infrastructure has the benefit of being on Amazon EC2 with
autoscaling and so promises short to nonexistent queue wait times, as well as
offering better performance for most use cases.

The next big step is to route *recently-activated Linux projects* to containers
under the following conditions:

* [No `sudo` usage is
  detected](https://github.com/travis-ci/travis-core/blob/7a360299c19011cbd3c0f2bf099a16600048e210/lib/travis/model/job/queue.rb#L44-L48)
in any of the custom build stages (we look for `sudo` or `ping` being used in
any of your build stages)
* The date of repo activation is [*after* a configured
  cutoff](https://github.com/travis-ci/travis-core/blob/7a360299c19011cbd3c0f2bf099a16600048e210/lib/travis/model/job/queue.rb#L88)

At the time of this writing, the cutoff date is February 14th, 2015.  This means
that any Linux projects activated after February 14th that do not contain
explicit `sudo` (or `ping`) usage will be routed to the container-based
infrastructure.

Our current plan is to continue to move the cutoff date further into the past in
one month chunks.  The exact timing of this change is not on a fixed schedule as
we're hoping to gradually adapt the available addons in response to feedback.

## Where did the `sudo` go?

If you were depending on `sudo` and we didn't detect it, don't worry! There's a
very simple way to get it back:

``` yaml
# Opt into fully virtualized infrastructure
sudo: required
```

<figure class="right small">
  <img src="/images/where-did-the-sudo-go.gif" />
</figure>

That being said, we invite you to look at our [APT
addon](http://docs.travis-ci.com/user/apt/) to see if it meets your needs.  

If you have a use case that's not currently being addressed by an addon, please
reach out to support@travis-ci.org.

Happy testing!
