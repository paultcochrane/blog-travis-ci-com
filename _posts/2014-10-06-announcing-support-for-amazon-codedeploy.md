---
title: Deploy from Travis CI to Amazon CodeDeploy
author: Mathias Meyer
twitter: roidrage
created_at: Mon 6 Oct 2014 18:00:00 PDT
layout: post
permalink: 2014-10-06-deploy-from-travis-ci-to-amazon-codedeploy
---
Today Amazon Web Services has launched a new service to deploy applications on their EC2 cloud. It's called **CodeDeploy**, and it follows similar and simple means of getting your code to production as Travis CI.

We're happy to fully support deploying your applications to Amazon SDS after a successful build.

**What makes CodeDeploy unique?**

Just like with your builds on Travis CI, your production runtime configuration is part of your source code repository, stored in an AppSpec file.

Steps to deploy an application to production and to set up the servers can be specified in scripts that are part of your source code repository.

On top of that, CodeDeploy lets you roll out applications gradually, on a subset of servers at a time, ensuring full availability of your site while the deployment is rolling out.

It offers a few different strategies to roll out an application on only half of your server fleet at any one time, or even just one by one.

Make sure to check out the [CodeDeploy site]() and [documentation]() to get a full glimpse on what it can do.

**How can I deploy to CodeDeploy from Travis CI?**

Integration with Travis CI follows the well-known schema of deploying your applications right after a build. Simply add a configuration section to your `.travis.yml` to start deploying:


    deploy:
      provider: codedeploy
      access_key_id: AKIA.....
      secret_access_key:
        secure: ...
      bucket: 'my-deployment-bucket'
      deployment-group: 'my-deployment-group'
      instance-group: 'my-instance-group'

For the full details, check our documentation on deployment using [CodeDeploy](http://docs.travis-ci.com/user/deployment/codedeploy).

Happy shipping!
