---
title: "Improved tag handling"
created_at: Wed 1 Oct 2014 18:00:00 CET
author: Piotr Sarnacki
twitter: drogus
layout: post
permalink: 2014-10-01-manage-private-dependencies-more-easily
---

When you push your tagged commits to a GitHub repository, you may
be surprised that we show tag as it was a branch in the UI. This is
a longstanding bug on our side and we would like to fix it. The problem
is, it will require us to introduce braking changes.

There is an option to whitelist or blacklist a branch in a `.travis.yml`
file. In order to do that you need to add a `branches` entry with
`except`, or `only`, or both, for example:

```yaml
branches:
  except:
    - /test-/
    - "experimental-branch"
```

Because tags are classified as branches, you can also use this entry
for filtering by tag.

After we fix the situation with missclassifed tags, it will no longer work
and you will have to use similar entry for tags, for example:

```yaml
tags:
  except:
    - /deploy-/
  only:
    - "deploy-production"
```

You may also need to adjust your scripts to use `TRAVIS_TAG` environment variable,
whereas now you can also use `TRAVIS_BRANCH`.

We're going to introduce these changes at 23rd of October, 2014.
