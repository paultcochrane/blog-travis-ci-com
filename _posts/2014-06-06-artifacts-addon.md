---
title: "Artifacts Revisited"
author: Dan Buch
created_at: Fri 06 June 2014 00:00:00 GMT
layout: post
permalink: /2014-06-06-artifacts-revisited
---

If whatever you're running on Travis CI produces artifacts, you'll no
doubt be thrilled to hear that we want to make saving these artifacts
super easy for you.

The first supported tool for doing this was
[travis-artifacts](https://github.com/travis-ci/travis-artifacts), a
handy gem-installable tool for shipping artifacts to Amazon S3.  This
was a great start, and solved the immediate need, but we knew we could
do better.

Among the problems we hoped to address were the lengthy installation
process of runtime dependencies and the lack of first-class support in
one's `.travis.yml`.

What we ended up building comes in two parts.  First, there is a binary
executable called `artifacts`.  This binary may be downloaded and used
directly by following the [installation
instructions](https://github.com/travis-ci/artifacts#installation).

In addition to this binary, an `artifacts` addon was tacked onto.
[travis-build](https://github.com/travis-ci/travis-build) so that you
can use it via your `.travis.yml`.  More details are available in [the
docs](https://docs.travis-ci.com/user/using-artifacts/), but a brief
example might look like this:

``` yaml
# .travis.yml
# ...
addons:
  artifacts:
    bucket: my-special-bucket
    key:
      secure: SyaIXy6OKDaYiew+...5vgAldy3jkmKA=
    secret:
      secure: X19eaiiFZobD3uCk...X8cY+ohT8WkQ0=
```

The bucket, key and secret parameters are equivalent to an S3 bucket
name, access key id, and secret access key.  These are currently
required parameters when using the artifacts addon, although we're
working on a solution in which the upload, storage, and retrieval of
artifacts is completely transparent.

The default paths that are sent to S3 are found via `git ls-files -o`.
If you want to upload any other paths, these may be specified as the
`addons.artifacts.paths` key a la:

``` yaml
# .travis.yml
# ...
addons:
  artifacts:
    # ...
    paths:
    # arbitrary shell commands are supported, but the output should be
    # converted to a ':'-delimited string.
    - $(ls /var/log/*.log | tr "\n" ":")
    # singular paths work fine, too
    - $HOME/some/other/path.log
```

We're looking forward to hearing what you think!
