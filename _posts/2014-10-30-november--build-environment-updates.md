---
title: "November 2014 Build Environment Updates"
created_at: Thu 30 Oct 2014 08:27:40 EDT
author: Hiro Asari
twitter: hiro_asari
layout: post
permalink: 2014-10-30-november--build-environment-updates
---

---------

## Update

.org rollout has been postponed by a day due to a bug in our worker code.

## Note on PhantomJS 1.9.8

There are reports of problems with PhantomJS 1.9.8 (which is reported as https://github.com/ariya/phantomjs/issues/12697).
This manifests in error messages such as:

```
Cannot decode JSON from PhantomJS runner
```
or
```
Cannot decode JSON from PhantomJS runner: 795: unexpected token at 'Unsafe JavaScript attempt to access frame with URL about:blank from frame with URL...
```

You can downgrade to 1.9.7 with the following commands:

```
sudo rm -rf /usr/local/phantomjs
curl -L -O https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-1.9.7-linux-x86_64.tar.bz2
tar xjf phantomjs-1.9.7-linux-x86_64.tar.bz2
sudo mv phantomjs-1.9.7-linux-x86_64 /usr/local/phantomjs
```

---------


# Update Schedule

The new updates will be rolled out to
**[travis-ci.org](https://travis-ci.org)** at **[15:00 UTC on the 4th of November](http://everytimezone.com/#2014-11-4,180,cn3)** and
to **[travis-ci.com](https://travis-ci.com)** at **[15:00 UTC on the 6th of November](http://everytimezone.com/#2014-10-14,180,cn3)**.

The updates will include the following:

## All Environments

* PhantomJS 1.9.7 → 1.9.8
* Ruby 1.9.3-p547 → 1.9.3-p550
* ElasticSearch 1.3.2 → 1.3.4

## Andorid VM

* build-tools-21.0.2, android-21, android-20

## Erlang VM

* IPv6 support is available

## Java VM

* Oracle JDK 7u60 → 7u72, 8u05 → 8u25

## PHP VM

* 5.4.31 → 5.4.34, 5.5.17 → 5.5.18, 5.6.1 → 5.6.2

## Python VM

* 3.4.1 → 3.4.2

## Ruby VM

* Ruby 2.1.4, 2.0.0-p576 → 2.0.0-p594
* JRuby 1.7.15 → 1.7.16.1

## Questions or comments?

If you have questions or comments, please get in touch via [email](mailto:support@travis-ci.com)
or [GitHub issues](https://github.com/travis-ci/travis-ci/issues).

Happy testing!

Love,

Travis CI Team
