---
title: "UC Berkeley CalSol Team Runs on Travis CI"
created_at: Thu 19 Mar 2015 08:00:00 EDT
author: Christopher Ngyuen
twitter: berkeleycalsol
layout: post
permalink: 2015-03-19-uc-berkeley-calsol-team-runs-on-travis-ci
---

This is a guest blog post from Christopher Nguyen, a member of the embedded systems group of
[CalSol](http://calsol.berkeley.edu/), the UC Berkeley Solar Vehicle Team.

CalSol uses Travis CI to test their embedded software that powers their solar vehicle
to explore the future of engineering.

<a href="https://www.flickr.com/photos/calsol/14559143237/"><img src="http://farm4.staticflickr.com/3872/14559143237_f7a110a64d_z.jpg"/></a>

(Photos reproduced with permissions)

-------------

Embedded systems are hard.
You're often on bare metal, fighting against memory constraints and a lack of specific documentation.
And the bugs. The bugs are terrible.
As the systems you build on the bare metal become serious, complicated, use-specific, there will be bugs, and
they will require more than a `printf`, and at minimum a logic analyzer to squash.
You may find that the bug isn't code at all, but a burnt out port causing funky noise in the io.
Often you'll find hours wasted chasing bugs through the system.

BUT sometimes there is a bright spot in the workflow.

Here at CalSol we've started down the long path of test-oriented code in building our solar racecars,
and this has meant that it is now possible to start using great tools like Travis CI and start putting in practice continuous integration.

Before Travis CI, the only sanity checks on pushes to the code base were watchful eyes.
In practice this often meant overlooked 3am pushes that sometimes wouldn't even build, let alone run on the boards on the Zephyr (the current solar racecar we're building).
Overburdened ~~university students~~ software and electrical engineers should not be doing the job of computers.
That's what computers are for!

<a href="https://www.flickr.com/photos/calsol/14558919670/"><img src="http://farm6.staticflickr.com/5557/14558919670_d177ea6b75_z.jpg"/></a>

In order to get GCC ARM embedded toolchain working on Travis CI's container-based infrastructure we first make sure that
certain 32-bit libraries are setup so that we can run the GCC ARM embedded toolchain.
(The GCC ARM embedded toolchain is 32-bit while the Travis CI environment is 64-bit.)
So in our `.travis.yml` file we put

```yaml
addons:
  apt_packages:
    - lib32bz2-1.0
    - lib32ncurses5
    - lib32z1
```

Now we have all the dependencies we need for the linux environment to identify and run the 32-bit executables in the GCC ARM embedded toolchain!
For the piece de resistance, (getting GCC ARM embedded toolchain onto our environment), we simply wget the appropriate file and unzip.

So in our `.travis.yml` file we add:

```yaml
install:
  - wget https://launchpad.net/gcc-arm-embedded/4.9/4.9-2014-q4-major/+download/gcc-arm-none-eabi-4_9-2014q4-20141203-linux.tar.bz2
  - tar -xf gcc-arm-none-eabi-4_9-2014q4-20141203-linux.tar.bz2
```

We can now compile embedded code on Travis CI!
(Remember that if you want to call `arm-none-eabi`, you will either need to add the location of where you unzipped the toolchain to the `PATH` variable or reference directly its location.)

Long story short, we're now using Travis CI to build our code using the GCC ARM embedded toolchain, and working towards fully running and testing it using our virtualizations of our boards.

We are very grateful to the crew at Travis CI for helping make our lives a little easier, and the job of making a winning solar racecar even more enjoyable.

If you'd like to support CalSol, you can donate here http://give.berkeley.edu/fund/index.cfm?f=FU1032000
