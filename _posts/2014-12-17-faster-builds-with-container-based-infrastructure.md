---
title: Faster Builds with Container-Based Infrastructure
author: Mathias Meyer
twitter: roidrage
layout: post
created_at: Wed 17 Dec 2014 16:00:00 CEt
permalink: 2014-12-17-faster-builds-with-container-based-infrastructure
---
Stability and reliability in your builds is the one thing we aimed to give since
Travis CI came about. But we haven't always been able to live up to this
expectation. Network issues, insufficient build capacity (for open source
projects) which in turn lead to long wait times for your build to start,
constrained CPU and memory resources in the builds environment, lack of caching
for open source projects. As most our current Linux stack runs on a private
  cloud, we've also had issues adding capacity, as we had to go through the
  process of ordering and waiting for more capacity.

Today we're happy to announce our new build infrastructure, which addresses some
of these issues.

## What benefits does this new infrastructure have?

**Builds start in seconds**

Rather than wait for builds to start for a long time, your builds now start in
less than 10 seconds. Assuming that capacity is available (which is now a lot
easier for us to scale), you'll see your builds going from being scheduled to
starting in only a few seconds.

**Faster builds**

We've been helping projects move over to this new stack, and we've seen much
better build times for most of them. The mileage may still vary based on how
heavy your builds are on I/O, but most projects should see an improvement. We'd
love to hear from your if you don't or if you see slower build times.

**More available resources in a build container**

The build containers in our legacy build infrastructure has had 1.5 cores (with
burst capacity) and 3GB of memory. The CPU resources are now guaranteed, which
means less impact by noisy neighbors on the same host machine. Build times
throughout the day should be much more consistent on the new container stack.

**Better network capacity, availability and throughput**

Our new stack is running on EC2, which means much faster network access to most
services, especially those hosted on EC2 as well. Access to S3 is now also a ton
faster than on our legacy stack.


**Caching available for open source projects**

The best news for open source projects is that our build caching is now
available for them too. That means faster build speeds by caching dependencies.
Make sure to read the docs before trying it out.

For Ruby projects, it's as simple as adding `cache: bundler` to your their
`.travis.yml`.

**Easier to scale**

This might not be a direct benefit to our users and customers, but it is one for
us. We can now respond to demand much quicker and increase our build capacity in
mere minutes. That allows us to ensure that open source projects are less likely
to hit capacity peaks and wait in line for too long until they run.

## How can I use it?

Using our new container-based stack only requires one additional line in your
.travis.yml:

``` sudo: false ```

## What are the restrictions?

**Using `sudo` isn't possible (right now)**

Our new container stack uses Docker under the hood. This has a lot of benefits
like fast boot times and better utilization of available machine resources. But
it also comes with restrictions imposed by security.

At this point, it's not possible to use any command requiring `sudo` in your
builds.

If you require sudo, for instance to install Ubuntu packages, a workaround is to
use precompiled binaries, uploading them to S3 and downloading them as part of
your build, installing them into a non-root directory.

**Databases don't run off a memory disk**

On our legacy and legacy legacy stack, both MySQL and PostgreSQL ran off a
memory disk to greatly increase transaction and query speed. This can impact
projects depending on their use of transaction, fixtures and general database
usage, but the impact generally shouldn't be negative.

## Tell me about this new stack?

Over the past year, we've been working on [Travis CI
Enterprise](https://enterprise.travis-ci.com), our on-premises solution for
GitHub Enterprise customers. Part of working on this stack required us to think
about how to best run on custom infrastructure like internal OpenStack, VMware
and other virtualization setups, and even on bare metal hardware.

Our legacy stack runs on a proprietary, managed cloud with APIs not available in
our customers' datacenters. Both for packaging our entire stack for
installation, but also for running builds in isolated environments, we started
looking at Docker as an alternative about a year ago.

Our new stack can run on pretty much anything we or our customers would like it
too. That allows for custom Travis CI Enterprise installations on EC2, Digital
Ocean, Linode, Rackspace, or fully in-house infrastructure.

We've verified a few options upfront, but EC2 turned out to have the better
performance and more reliable network.

Our new stack for hosted private and open source projects is running on EC2
inside of Docker containers. We've seen great performance both in the network
and with compute resources, and the direct access to S3 makes build caching a
lot faster.

## I have more questions...

**Can I provide my own Docker containers?**

The build environments we're currently using on our Docker-based setup provide
the same services, programming languages and tools offered by our legacy stack.
We've been keeping them on par as much as possible.

The lack of `sudo` does make it hard to install custom libraries and services,
running them on privileged ports, or simply using `apt`. The question for
providing your own images is a natural one.

We're not there yet in allowing you to bring your own, but it's something we
have in mind for the future.

**Can I build Docker containers as part of my build?**

Same as the above. It's not currently possible, mostly for security reasons, but
is something we want to address in the future.

**Can I run Docker inside Docker?**

Running Docker containers as part of your build currently isn't possible because
of questions related to security due to the underlying container technology. We
have things planned to address this in the future.

## Containers everywhere

This is only the beginning of offering a better, faster and more reliable builds
on Travis CI. We have a lot more things planned to improve stability, but we're
excited to ship this today.

Give it a spin and let us know what you think!
