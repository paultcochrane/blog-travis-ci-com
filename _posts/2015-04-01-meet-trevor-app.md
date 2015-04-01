---
title: "Meet Trevor. A hybrid mobile app for Travis CI"
created_at: Wed Apr 01 13:22:49 UTC 2015
author: Emmanouil Konstantinidis
twitter: iamemmanouil
layout: post
permalink: 2015-04-01-meet-trevor-hybrid-app
---

Alright, so [Trevor](http://www.trevorapp.com/). A hybrid app ([App Store](http://itunes.apple.com/app/id962155187) and [Google Play Store](http://play.google.com/store/apps/details?id=com.iamemmanouil.trevor) that brings Travis CI to your phone and tablet. What's behind the scenes? A hybrid app based on [Ionic Framework](http://www.ionicframework.com/) and of course the great [Travis CI API](http://docs.travis-ci.com/api/).

[![Meet Trevor](/images/2015-04-01-meet-trevor.png)](http://www.trevorapp.com/)

#### Ionic is awesome and gets event better
The app is made with Ionic Framework.  In case you haven't heard of Ionic before, it basically wraps [Apache Cordova](http://www.cordova.io/) (yes you can use all the goodies/plugins that come with Cordova) and it's written in [AngularJS](http://www.angularjs.com/). In once sentence we could say: "Create hybrid mobile applications that look like native, having great performance by writing Javascript along with HTML and CSS of course".

I've used Ionic for a couple of projects(work and personal projects) and while it's already awesome it keeps getting **better and better** (soon to become stable, reaching version 1.0). It all starts with the installation of Ionic through [NPM](http://www.npmjs.com/). Once installed you can then start one of the three default templates provided.

    ionic start myApp blank
    ionic start myApp tabs
    ionic start myApp sidemenu

Then all you have to do is start adding elements (big list of ionic directives), add states-controllers, bit of CSS and there you go! It's an app ready to be published!

#### The Travis API: great docs, awesome results
Most of the projects that I'm working on at [DabApps](http://www.dabapps.com) involve a mobile app and a web server([Django](http://www.djangoproject.com/) & [Django Rest Framework](http://www.djangorestframework.com/) and from my experience with APIs I can only say that the Travis API is just perfect.  I'm using Travis CI for about a year and when I first read the [API documentation](http://docs.travis-ci.com/api/), it was pretty clear on how to get everything from accounts to repos, builds, logs etc

    # Get my repositories and latest builds
    curl -X GET https://api.travis-ci.org/repos/ekonstantinidis

    # Get the builds for a particular repository
    curl -X GET https://api.travis-ci.org/builds?repository_id=2855496/builds/

Since Trevor started as an experiment (Friday night,  let's give it a try), I believe the app would not be in the stores if the API wasn't that clear. It all started with the login (which was the *toughest* part since it involved authentication with Github) but once I got the Travis token, I was then able to get my accounts, repositories, builds and pretty much everything Travis' web interface provides.

#### The future of Trevor
A new version has been already submitted and includes many many changes. New improved design (inspired by the new awesome Travis UI), ready for Travis CI for Education, many fixed bugs and of course it's more stable and faster. Plans include even more features being added like access to both Travis CI for Open Source and Travis Pro at the same time, push notifications and more! Download it for [free](http://www.trevorapp.com/) and watch for the upcoming updates!