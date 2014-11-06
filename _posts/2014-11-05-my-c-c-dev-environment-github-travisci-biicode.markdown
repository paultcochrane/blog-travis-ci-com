---
layout: post
title: "My C/C++ Dev Environment: Github, Travis CI, Biicode"
date: 2014-11-05T17:14:04+01:00
---

# My C/C++ dev environment: Github, Travis CI, biicode #

Here at [biicode](https://www.biicode.com/?utm_source=Travis CI&utm_medium=guestpost&utm_campaign=Travis CI) we work with Travis CI almost everyday. We love it and any of us surely would recommend it to any dev looking for a neat continuous integration environment. However, we thought that Manu’s story was the best one to illustrate how much joy Travis CI has brought to us. This is [Manu](http://www.biicode.com/manu343726?utm_source=Travis CI&utm_medium=guestpost&utm_content=Manuprofile&utm_campaign=Travis CI)'s story:

As a self-taught programmer I was doing C++ in depth for the last four years. Graphics, physics engines, metaprogramming... I enjoyed the language, but the lack of proper tools for testing and source control integration was a pain. 

I usually release my personal projects as open source via my github account, so since the first day I really liked the integration Travis CI provides within github. You only have to configure your environment and run your own tests, scripts, etc. 

And that’s exactly the source of success of Travis CI for me: The environment setup. The setup via `.travis.yml` is so easy, and the fact you are really working with an Ubuntu machine allows you to do whatever you like.

## Travis CI and biicode ##

Here's when biicode enters the scene. biicode was a great discovery for my C++ programming workflow. [Just an include](http://web.biicode.com/features/cpp/?utm_source=TravisCI&utm_medium=guestpost&utm_content=features&utm_campaign=travisci)! No library download, horrible linking config, etc. Just include and run. And since Travis CI is a linux machine, setting up my github projects to "push" to biicode automatically after running my tests at Travis CI was a simple and natural task.

Biicode is not a platform to host code in a VCS style, is a platform to host libraries, building blocks. Think of it as the Ubuntu repositories and apt-get, but as it does it mostly from source code, more like Gentoo Portage. And the fact I can upload/update my "package" to biicode cloud automatically after running some integrity tests (automatically too) thanks to Travis CI is awesome.

## How I got hired thanks to Travis CI ##

The workflow with Travis CI was so awesome that I was working intensively on it for two weeks, configuring my projects to use biicode through Travis CI. During that period, my efforts got the attention of the biicode team, and they make me a job offer to continue with my work for them.

That was only the start. Now at biicode headquarters I can improve the workflow for me and the rest of biicode users testing it every day, providing feedback for biicode developers. 
Here at biicode we think that Travis CI is the perfect choice to automate the testing and deployment of biicode blocks, and we are working hard to make Travis CI and biicode interoperability easier and simpler each release. You can help us to improve the user experience, using Travis CI with your own biicode projects and asking us for any issue or suggestion.

## Try it! ##

We really recommend Travis CI for the day to day workflow of any C/C++ programmer. Git/Github for source control and hosting, Travis CI for automatic testing and building, and finally biicode for library sharing and deployment.

[Manu Sánchez](http://manu343726.github.io/portfolio/) from the biicode Team.

