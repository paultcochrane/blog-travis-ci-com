---
title: New Linter, now with Super Powers
created_at: Thu 20 Mar 2014 17:17:48 CET
author: Konstantin Haase
twitter: konstantinhaase
layout: post
permalink: 2014-03-20-new-linter-now-with-super-powers
---

We have just replaced [our web linter](http://lint.travis-ci.org/) with a complete rewrite. It is now using our brand new [travis-yaml](https://github.com/travis-ci/travis-yaml). This means instead of being very rudimentary and not well maintained, it is now quite powerful when it comes to spotting issues in your [build configuration](http://docs.travis-ci.com/user/build-configuration/).

![](/images/weblint.png)

You can also use this tool to check your [repository directly](http://lint.travis-ci.org/sinatra/sinatra) (including [branches](http://lint.travis-ci.org/sinatra/sinatra?branch=1.2.x)), and [gists](http://lint.travis-ci.org/gist/9639067) directly.

### Future Plans

Having a new linter was just a byproduct of creating the [travis-yaml](https://github.com/travis-ci/travis-yaml) library. We plan to use this small gem throughout our system. That way we will have one central definition for the `.travis.yml` format.

First, we need to get 100% coverage of the currently supported configuration options, though.