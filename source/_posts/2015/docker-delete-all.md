---
title: Docker How To Delete Everything
date: 2015-12-02
categories: Dev
tags: 
  - docker
  - dev
---

Just want fresh restart and delete all containers? Here is the code:

` docker stop $(docker ps -a -q) docker rm $(docker ps -a -q)`

If you want to delete all images too:  
` docker stop $(docker ps -a -q) docker rmi $(docker images -a -q)`
