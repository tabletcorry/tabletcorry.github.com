---
layout: post
title: "Jenkins, Forking, and You"
date: 2011-12-07 21:10
comments: true
categories: 
- Jenkins
---
Jenkins (circa 1.434) has an interesting, if frustrating, bug that can hit you 
when you are using a significant amount of memory on your build nodes.

Basically, Jenkins needs to fork (several times actually) whenever a build 
starts. 
In and of itself, this is not a problem, but when Jenkins is using >50% of the 
available RAM, things change a bit.
All of the sudden, you will start to see unpleasant messages like:
`Cannot run program "/usr/bin/git" (in directory "/path/to/jenkins/project"): java.io.IOException: error=12, Cannot allocate memory`
Considering the normal RAM usage of git, this is not a likely situation.

The only solution at this point is to restart Jenkins and hope that its baseline
memory usage is <50% of your ram.
