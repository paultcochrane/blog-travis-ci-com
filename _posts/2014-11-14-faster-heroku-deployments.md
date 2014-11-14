---
title: Faster Heroku Deployments
author: Konstantin Haase
twitter: konstantinhaase
created_at: Fri 14 Nov 2014 13:00:00 CET
layout: post
permalink: 2014-11-14-faster-heroku-deployments
---

<figure class="small right">
  ![](https://cloud.githubusercontent.com/assets/30442/4494777/04a43ab0-4a55-11e4-8e9f-f6e274153f51.png)
</figure>

If you are deploying to [Heroku from Travis CI](http://docs.travis-ci.com/user/deployment/heroku/), you might have seen a warning pop up in your build logs lately: We are changing the default strategy from "anvil" to "api".

But what does this mean? Up until recently, Travis CI could deploy to Heroku by two different means: Anvil and Git. We call these "strategies" and you can switch between them by setting the `strategy` option in your deploy section. Both strategies have their issues.

The Git strategy does what you would do locally: `git push` your application to Heroku. It would generate a new SSH key for your Heroku account on every single deploy (and subsequently remove it again). This would trigger a new email, potentially for all builds on Travis CI.

On the other hand, the anvil strategy uses an [unofficial build server](https://github.com/ddollar/anvil), which accepts archives of the application you want to deploy. All it needs is API access (via a token or username/password). However, it comes with a few dependencies, which makes it slower than the git strategy. But worst of all, it is deperecated and will be shut down in the near future.

Lucky for us, the awesome folks at Heroku have been busy finding a solution for this. And they didn't just come up with one, but two approaches 

## The Build API

Heroku launched their [Build API](https://devcenter.heroku.com/articles/build-and-release-using-the-api) a while ago. We have had support for it since October 2nd, but users had to manually set the strategy to "api" in their .travis.yml.

**Starting on Monday, November 17, this will be the new default strategy.** Internally, all Travis CI will be doing, is bundle up the current project directory as a tarball and upload it to the Heroku API. It will then stream the buildpack compilation logs back from the Heroku API to the Travis CI web interface.

In theory, the only change this will cause from an endusers perspective are faster deployments.

## HTTP Git

More recently, Heroku has made it possible to do a git push [over HTTPS](https://devcenter.heroku.com/articles/http-git). This eliminates the need to generate an ssh key to be able to deploy via git. We have an implementation ready, and it will replace our current "git" strategy, also on Monday.

## Reverting to SSH or Anvil

If these changes will somehow break your deployments, you can set the strategy option in the deploy section of your .travis.yml to "anvil" or "git-ssh" respectively.

    deploy:
      provider: heroku
      strategy: anvil

However, most importantly, you should [get in touch](mailto:support@travis-ci.com?subject=Heroku%20Deployments). **Both the git-ssh and the anvil strategy will be discontinued in the near future.**

## A strategy for the future

Ideally, with this update, you as our user should never have to worry again about the different options we might have for deploying to Heroku. Things should *just work*™. We will monitor this change in the coming weeks and gather user feedback. If it is all to our pleasing, we might remove the strategy option entirely in the future.