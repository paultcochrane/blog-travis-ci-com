---
title: "Upcoming Build Environment Updates -- August"
created_at: Wed 20 Aug 2014 11:47:30 EDT
author: Hiro Asari
twitter: hiro_asari
layout: post
permalink: 2014-08-20-upcoming-build-environment-updates----august
---

We are working hard on getting build environment updates
more frequently.

## Update schedule

The updates will be rolled out to
**[travis-ci.org](https://travis-ci.org)** at **[14:00 UTC on the 26th of August](http://everytimezone.com/#2014-8-26,120,cn3)** and
to **[travis-ci.com](https://travis-ci.com)** at **[14:00 UTC on the 28st of August](http://everytimezone.com/#2014-8-28,120,cn3)**.

## Build Environment Updates

All environments will receive the following updates:

### Chromium browser

34.0.1847.116 → 36.0.1985.125

### CouchDB

1.5.0 → 1.6.0

### ElasticSearch

1.1.1 → 1.3.2

This change contains breaking changes: [1.1 → 1.2](http://www.elasticsearch.org/blog/elasticsearch-1-2-0-released/),
[1.2 → 1.3](http://www.elasticsearch.org/downloads/1-3-0/).

If you need to revert to ElasticSearch 1.1.1 because of these breaking changes,
remove the installed version and install 1.1.1:

```yaml
before_install:
  - sudo apt-get purge elasticsearch
  - curl -O https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-1.1.1.deb
  - sudo dpkg -i elasticsearch-1.1.1.deb
```

### OpenJDK 6

6b31 → 6b32

### OracleJDK 7

7u60 → 7u67

### MySQL

5.5.37 → 5.5.38

### PostgreSQL

1. 9.1.13 → 9.1.14
1. 9.2.8 → 9.2.9
1. 9.3.4 → 9.3.5

### RabbitMQ

3.3.4 → 3.3.5

### nvm

0.13.1

With the new nvm, specifying `0.10` will install
the most recent released version of `0.10.x`.
If you need a specific version, you must indicate it as
precisely as possible; e.g., `0.10.29`.

### Sphinx

1. 2.2.2-beta → 2.2.3-beta
1. 2.1.8 → 2.1.9

## Android VM

Android SDK is updated to 23.0.2.
`build-tools-20.0.0` is pre-installed.

## Haskell VM

Platform is updated to 2014.2.0.0.
GHC is updated to 7.8.3.

## Java VM (not JVM)

* Maven is updated to 3.2.3.
* Leiningen2 is updated to 2.4.3, which is now the default. See details [below](#leiningen-will-default-to-2x).

## PHP VM

Version updates include:

* 5.6.0rc4
* 5.5.16
* 5.4.32
* 5.3.29

We've also added 5.5.9 back. This is the version supported on Ubuntu LTS14.04.

## MongoDB

PPA changed to the official one from [MongoDB.org](http://www.mongodb.org/).
With this change, the default is now 2.6.4.
If you need a specific version, do the following for releases 2.6.0 and later:

```yaml
before_install:
  - sudo apt-get purge mongodb-org mongodb-org-server mongodb-org-shell mongodb-org-mongos mongodb-org-tools
  - sudo apt-get install mongodb-org=2.6.1 mongodb-org-server=2.6.1 mongodb-org-shell=2.6.1 mongodb-org-mongos=2.6.1 mongodb-org-tools=2.6.1
```

For releases older than 2.6.0, do:

```yaml
before_install:
  - sudo apt-get purge mongodb-org mongodb-org-server mongodb-org-shell mongodb-org-mongos mongodb-org-tools
  - sudo apt-get --no-remove install mongodb-10gen=2.4.10
```

Do note the difference in the package name.

## Firefox browser

This update includes update to the latest Extended Support Release (ESR),
31.0esr, which corresponds to Desktop Firefox 31.0.

## Leiningen will default to 2.x

With this update, the default version of Leiningen will be 2.4.3.
Leiningen 1.x will be available as `lein1`.

`lein` will point to Leiningen 2.4.3, but `lein2` will be available as before.

Those repositories which use `lein` need to be updated to invoke `lein1` instead.

## Go forth and test!

Happy testing!

Love,

Travis Team
