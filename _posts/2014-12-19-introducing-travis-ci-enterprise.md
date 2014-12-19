---
title: Introducing Travis CI Enterprise
author: Mathias Meyer
twitter: roidrage
created_at: Fri 19 Dec 2014 16:00:00 CET
layout: post
permalink: 2014-12-19-introducing-travis-ci-enterprise
---
![](http://s3itch.paperplanes.de/Travis_CI_for_Enterprise_2014-12-18_16-42-44.jpg)

Today we're excited to ship and launch [Travis CI Enterprise](https://enterprise.travis-ci.com), a self-hosted version of Travis CI that runs inside your datacenter.

Over the past months and years, we've been approached many a times by companies wanting to run Travis CI on their own premises, utilizing their internal [GitHub Enterprise](https://enterprise.github.com) installations.

Travis CI Enterprise supports GitHub.com and GitHub Enterprise, allowing you to bring all the features that make Travis CI great into your own datacenter, making it easy to scale out build infrastructure based on your company's needs.

**Runs on your infrastructure**

With Travis CI Enterprise, you can fully utilize internal and existing infrastructure. Whether you're using OpenStack, VMware, or bare metal servers.

It's optimized to run on EC2 as well, and it's fully based on the [new Docker build stack](http://blog.travis-ci.com/2014-12-17-faster-builds-with-container-based-infrastructure/) that we shipped earlier this week.

Running on EC2 allows you to scale out capacity and save costs based on demand throughout the day or week.

**Customize the build environment to your needs**

With Travis CI Enterprise, you can customize the build environment to reflect your specific needs. Whatever services and language versions you need to have installed by default, thanks to Docker, you can provide your own images, speeding up builds significantly, removing the need for any customization and slowdown during the build.

**Security**

Just like hosted Travis CI, our Enterprise version integrates with your existing GitHub instance. You can easily use it with **LDAP** directories, as login, authentication and authorization are strictly tied to the users you already have set up in GitHub Enterprise.

**Pricing**

The licensing is done per seats, where every license includes 20 users. Pricing starts at $6,000 per license, which includes 20 users and 5 concurrent builds. There's a premium option with unlimited builds for $8,500.

**How can I try it out?**

Send us an email, and [we'll get you set up with a trial](mailto:enterprise@travis-ci.com).

**Question and Answers**

*Does Travis CI Enterprise support Stash, Gitorious, or any other version control system?*

Travis CI Enterprise focuses on a tight integration with GitHub and GitHub Enterprise. While we don't have immediate plans to support other platforms, do get in touch if you have specific needs, as that gives us clues for our product roadmap.

*How is it installed?*

We ship you a set of two images, one containing the base installation, and another one that includes the job worker, which you can install on the machines you want to dedicate to running builds.

*Can I provide my own Docker image?*

Yes, you can. Travis CI Enterprise fully supports bringing your own set of images so you can tailor the build environment to suit your needs.

*Can I dedicate more resources to my Docker containers?*

By default, the containers run with 2 cores and 4 GB of memory. While that can't be customized just yet, it's something we're looking into adding in the future.

Want to try out Travis CI Enterprise on your infrastructure or on EC2? [Get in touch](mailto:enterprise@travis-ci.com), and we'll get you set up!.
