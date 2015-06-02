---
title: "This Week in Travis CI — May 29th, 2015"
created_at: Fri 29 May 2015 09:13:02 EDT
author: Hiro Asari
twitter: hiro_asari
layout: post
permalink: 2015-05-29-this-week-in-travis-ci
---

We have some exciting news this week!

## New Mac infrastructure is going into production

As we discussed in a [previous blog post](/2015-04-20-state-of-the-mac-infrastructure-on-travis-ci/),
we have been working hard to bring the new Mac infrastructure to production.

Last week, we began gradually routing Mac builds to the new setup, starting with
random 10% of the incoming jobs.
This was increased everyday while we monitor the performance and for any problems encountered.

As of today (2015-05-26), all our Mac builds are running on the new infrastructure.

The switch to the new platform should be invisible to you for the most part.
When your job is running on the new infrastructure, the VM's name is shown like this:

```
Using worker: worker-jupiter-brain:…
```

If you do encounter problems on the new infrastructure,
please <a href="mailto:support@travis-ci.com">get in touch with us</a>.

### Xcode 6.3

With the above work done, we were able to focus our attention on bringing the long-awaited
Xcode 6.3 support to Travis.

We are happy to say that we have announced this in [a separate blog post](/2015-05-26-xcode-63-beta-general-availability/).

## The "Owner" page

We continue improving our web UI as well.

You can now navigate to the owner page (e.g., [https://travis-ci.org/travis-ci](https://travis-ci.org/travis-ci))
and see the list of repositories belonging to the organization/user.

![Owner Page](https://cloud.githubusercontent.com/assets/25666/7687475/8b7c2b96-fd6b-11e4-8438-cf4af2ff6e9e.png)

Here, you can see the build statuses of the owner's repositories at a glance.

We are not done yet, either.
More useful features are planned on the onwer page in the coming weeks.

## Build environment updates

Our last build environment updates included ambitious changes
that caused issues described below.
We attempted to fix them as the reports rolled in, but
we were unable to overcome them.

### What went wrong with MySQL 5.6?

There is [a long standing GitHub issue calling for MySQL 5.6 upgrade](https://github.com/travis-ci/travis-ci/issues/1986)
and we had high hopes to address it.

When it went into production, we received reports of MySQL not 'starting'.
Well, the server *was* running, but the client was unable to connect to it over
UNIX socket.

In some cases, specifying the TCP connexion (`127.0.0.1` as opposed to `localhost`) worked,
but in other cases, we could not work it out.

The problem was that the socket mysteriously disappeared after the server started.
We pushed a hot fix to restart MySQL every time as a workaround, but this, too,
proved ineffective in the end.

We are working on making it available in the future with least
disruptions possible.

### Were there any other critical issues?

#### Cassandra 2.1.2

There was also an update to Cassandra 2.1.2.

Frankly, we neglected to research what this upgrade meant.
This included incompatible changes in the configuration files that
rendered the service unusable.

Those of you who rely on Cassandra had no way to run builds.

We will remain on 2.0.x for the time being.

#### Java 6 and Maven 3.3

Maven 3.3 requires Java 7, and builds running on Java 6 had
no way to build.

We are looking into having multiple versions of maven available,
but this may not happen for the June updates.

### What are we going to do now?

The stable build environment is the foundation of a CI service.

To improve the update process, we plan to expand our tests to include "beta" period,
during which users can test the next generation image on the selected few
language VMs and report issues.

We will have a more detailed announcement on this soon.

### Next build environment update

The next planned update in June will include a smaller list of changes, primarily focused on language runtimes.
It will be announced in the [usual channels](http://docs.travis-ci.com/user/build-environment-updates/).

----

Happy testing!

The Travis CI Team
