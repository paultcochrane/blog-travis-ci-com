---
title: "Upcoming VM Updates"
created_at: Wed 16 Jul 2014 14:46:36 CEST
author: Hiro Asari
twitter: hiro_asari
layout: post
permalink: 2014-07-16-upcoming-vm-updates
---

New VM updates are coming.

It has been a while since our last VM update in [late April](http://blog.travis-ci.com/2014-04-28-upcoming-build-environment-updates/);
it is time for the next round of VM udpates.

## Update schedule

The updates will be rolled out to
**[travis-ci.org](https://travis-ci.org)** at **[06:00 UTC on the 23rd of July](http://everytimezone.com/#2014-7-23,-360,cn3)** and
to **[travis-ci.com](https://travis-ci.com)** at **[06:00 UTC on the 30th of July](http://everytimezone.com/#2014-7-30,-360,cn3)**.

## Build Environment Updates

Build environments receive several updates.

### Android VM

We've introduced [Android support back in May](2014-05-07-android-build-support-now-in-beta),
and you have been busy testing it out.
Google has since released a new SDK, and it is now time for us to catch up.

This update includes SDK 23 support and other component updates.

### Go VM

Default is now 1.3.

Version 1.2.2 is available.

### Node.js VM

Default is now version 10.28.

### Perl VM

Version updates include:

* 5.20.0 and 5.21.0 are added, 5.17 and 5.19 are dropped.
* 5.18.2 and 5.20.0 are now also provided with the `-Duseshrplib` compile option under the names
  `5.18-shrplib` and `5.20-shrplib`, respectively.

### PHP VM

Version updares include:

* 5.6.0rc2
* 5.5.14
* 5.4.30

We also added LDAP support.

### Python VM

Following updates are included:

* Python 2.7.3
* Python 3.4.1
* PyPy3
* PyPy 2.3.1

### Ruby VM

* MRI 1.9.3-p547
* MRI 2.1.2
* JRuby 1.7.13
* Rubinius 2.2.10 (Available as `rbx`; no longer needs to be specified as `rbx-2`)


### Services Updates

In addition, following updates are available on all VMs:

* CouchDB update to latest stable (1.5)
* Cassandra 2.0.9
* Sphinx version updates (2.0.10, 2.1.8, 2.2.2-beta; 2.1.8 is default)
