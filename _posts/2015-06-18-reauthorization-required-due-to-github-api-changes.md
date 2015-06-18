---
title: Re-authorization Required Due to Upcoming GitHub API Changes
created_at: Thu 18 Jun 2015 12:00:00 CEST
permalink: 2015-06-18-reauthorization-required-due-to-github-api-changes/
layout: post
author: Mathias Meyer
twitter: roidrage
---
As a customer of Travis CI, using our platform for private repositories, you've
probably noticed that you've had to log in and re-authorize with the GitHub
OAuth flow. This started earlier this week, and we wanted to explain why. While
the changes impact both platforms for private and public repositories, the
re-authorization only affects [our paid platform for private
repositories](https://travis-ci.com).

A few months ago, [GitHub announced a couple of breaking
changes](https://developer.github.com/changes/2015-01-07-prepare-for-organization-permissions-changes/)
to their API, some of them directly affecting our current synchronization
process of your repositories, organizations and access permissions to them.
[These changes will be in effect next
week](https://developer.github.com/changes/2015-06-10-breaking-changes-to-organization-permissions-coming-on-june-24/),
on June 24th.

As we've evaluated the changes, we realized that we needed another OAuth scope
to continue providing our service without any interruption. We've also been
working on changes to our synchronization with the GitHub API to make sure we're
prepared for the upcoming changes.

### Why is re-authorization required?

As part of the changes, a new scope was required to access certain
organizational information, in particular about what organizations you belong
to.

We use this information to synchronize permissions and repositories, so we can
show you repositories and their respective builds based on what you have access
to on GitHub.

The new scope we've added is `read:org`, which allows us to continue accessing
memberships in organizations that are kept private on GitHub. This is
particularly important for private projects and organizations, where it's common
for memberships not to be fully public.

We've started rolling the re-authorization request out early to make sure that,
after the changes are active on GitHub's side, we can continue to provide
uninterrupted service to you.

### What about our current OAuth scopes in general?

For private repositories, we still request the `repo` scope, which does give us
pretty wide access. For open source repositories, we've reduced the scopes
already to the bare minimum required for us to provide our service to you. The
ones we currently require are [outlined in our
documentation](http://docs.travis-ci.com/user/github-oauth-scopes/).

For private repositories, we're planning on reducing our requested permissions
in a similar way in the future, though the GitHub API doesn't yet fully provide
everything we'd need to drop the `repo` scope from our permissions, in
particular finer-grained scopes to read files over the API and to set up deploy
keys, both currently only made possible by the `repo` scope.

As a precaution, we'll be disabling automatic synchronization with GitHub for
two weeks, starting next Monday, to ensure that any issues that may come up will
only have a local impact rather than affect thousands of customers. If you're
missing any new repositories during that time, you can manually trigger the
synchronization on your accounts page.

The changes will be in effect next week, on June 24th, and we're working on a
few more preparations to reduce the possibilities of a negative impact on our
service. If you have any questions or issues, please [get in
touch](mailto:support@travis-ci.com).
