---
title: "This week in Travis CI, 2015-04-09"
created_at: Thu 09 Apr 2015 10:22:00 CET
author: Hiro Asari
twitter: hiro_asari
layout: post
permalink: 2015-04-09-this-week-in-travis-ci
---

Things are moving fast at Travis CI.

Some changes are visible (six(!) new members of our growing team
and the UI improvements--more on this below), and some are not so visible (like emphasis on
the new container-based infrastructure, and behind-the-scenes API improvements).

We want to let you know what Travis CI is up to with these
regular updates.

## UI improvements
You have undoubtedly noticed the recent changes to our web pages.
The overall theme is flatter; the focus of these updates to make
information easier to find, along with some eye candies like favicon (sorry, Safari users, you won't see them)
which changes according to the build/job's status.

We have also beefed up the landing page.
If you are logged in, please sign out, and see it for yourself!

![](/images/landing-page.png)

These changes are great on their own merit, but we are not done yet.
These lay foundations for future updates we have planned.

We plan a more detailed blog post.
Stay tuned!

## Containerized future
As we just [announced](/2015-03-31-docker-default-on-the-way/), recently
activated repositories will run on containers by default, unless they are
explicitly opted out with `sudo: required`.

The container-based infrastructure provides a better overall experience,
with shorter wait and more capable VMs.

## KVM in the works
We are also working hard on bringing KVM to our infrastructure.
This has some interesting ramifications:

1. Builds can use Docker processes
2. Hitherto unattainable features such as FUSE are now possible

Currently in early alpha stage, this setup is showing some promising results so far.

## Rails Girls Summer of Code
[Rails Girls Summer of Code](http://railsgirlssummerofcode.org/) returns for the third straight year.
[Anika Lindtner](https://twitter.com/langziehohr), [Sven Fuchs](https://twitter.com/svenfuchs),
[Laura Gaetano](https://twitter.com/alicetragedy),
and [Sara Regan](https://twitter.com/sareg0)
are hard at work to make this another smashing success.

If you have not done so, I encourage you to donate today!

## 2015-04 Build environments updates
Among [many small updates announced](http://docs.travis-ci.com/user/build-environment-updates/2015-04-09),
the highlight is MySQL 5.6, provided by Ubuntu packages from [dev.mysql.com](http://dev.mysql.com/downloads/mysql/).

While MySQL 5.6 brings you many new features, if you need to stay on 5.5, be sure to follow the instructions
given in the announcement above.

## Miscellaneous bug fixes and new features
These don't merit special mentions or a separate blog post, but are interesting nonetheless.

1. Ruby VM now respects `.ruby-version` file, and uses the Ruby runtime defined in it.
2. A new build phase `before_cache` is added. You can use this phase to prepare the cache before it is checked for updates.
    This is useful for cases where a utility touches a small file, which would mark the entire cache as new without interference.

## Until next time…
We will talk soon, but until then, happy testing!
