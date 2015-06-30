---
title: Storage Strategies and Continuous Integration
permalink: /2015-04-14-storage-strategies-and-continuous-integration
layout: post
created_at: Mon 29 Jun 2015 15:05:00 CEST
author: Benjamin Kisliuk
---

This is a guest blog post by Benjamin Kisliuk.

----

ViOLa, which stands for the German title "Visualisierung und Optimierung von Lagerstrategien"
(Visualization and Optimization of Storage Strategies), is a project group formed by eight
master's degree students of the University of Osnabrueck, a city in the north-west of Germany.

Its goal was to implement a toolbox for examining various strategies for how to organize a
storage most efficiently.
Algorithms should be based on current research and examined for further improvement.
Supervised by Sigrid Knust, the professor for
[Combinatorial Optimization](https://www.informatik.uni-osnabrueck.de/arbeitsgruppen/kombinatorische_optimierung.html),
and two of her research fellows (Florian Bruns and Jana Lehnfeld),
the project started in April of 2014 and is due to end after one year of sorting and
organizing storages at the end of March 2015.

## First Projects and the Quality of Code

Nine months ago I would not have thought how quickly thousands of lines of code, tests and
documentation would pile up.
For most of us this was the first software project going on for
more than a few weeks and it is fair to say that it also was the first "real" application
of all the teachings of code quality, testing and planning we received so plentiful during our years
at the university.

Most of us already knew the blessings of code version tools so the decision to
make use of git with Github as the central platform to host our software fell quite easy.

But whereas git is a good tool for working in parallel on different areas of a software, probably every
developer around the world is familiar with endless hours and nerves spent on rerolling faulty
commits, merging conflicting branches and swearing over unit tests once nicely implemented but
forgotten to use before putting up a pull request.

Being able to work simultaneously on different
branches of the same software is a great thing, integrating those branches is not. Even when using
a powerful build tool as we did with using [Gradle](https://gradle.org/) to build and test our code, mistakes are going to
be made. Of course, all of this can be avoided by "just" being very professional, but having an
automated process watching one's back could make a lot of things a whole lot easier.

After all, software development is all about automatization, is it not?

This is where the idea of continuous integration comes into play.
It is hard to guess how
many hours we have saved by the nasty red button telling us to have one more look at the changes
we were going to merge, but letting Travis CI check on our pull requests right before merging
them reduced to just two the number of times we had to rework our master branch since the project started.

So what do we let it do specifically?

As mentioned, we use Gradle to build our software and execute the tests, so when committing something
new to GitHub, a Gradle build and test execution is started. Included here are plugins for [Jacoco](http://www.eclemma.org/jacoco/),
having a look on our code coverage and [SonarQube](http://www.sonarqube.org/), which examines the code for common flaws and quality
issues.

Worthy to note is, that our software - while mainly working within the Java machine - in part
relies on [Zimpl](http://zimpl.zib.de/)
and [SCIP](http://scip.zib.de/) to generate and solve problems formulated as ilp and mip - so the Travis VM
also has to install them to be able to run the according tests. It also generates our Javadoc
and tells us if there is something wrong. Although we were missing native a support for LaTeX documents
we worked around that by having Travis download the required packages so that even our documentation
is checked for errors before any merges. Obviously, the Travis cache comes pretty handy in reducing
the times all these downloads and installations have to be made. In the end, Travis enables us to
automatically use all these little helpers improving and ensuring our code's quality.

## At the End of the Day

After nine months, what is left to say?

Getting work done means using the right tools and the ones
we used in our project certainly were very right.
The results we achieved in our research, visible
in our implementation, would not have been possible to the extent reached today without Travis.

Software development is all about building stuff.
Having to unravel histories of changes to find and fix
a certain mistake which probably could have been avoided beforehand can be a pain.

This is why we want to close with thanking you, the Travis CI team, for supporting our work!
