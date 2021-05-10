---
title: Python how to list files under a directgory
date: 2011-05-10
categories: 
 - Dev
 - Python
tags: 
 - dev
 - python
---

There are so many ways, but in python 3 looks the most popular way is using pathlib. Here is an example to list all
files starting with `bar` under dir `/foo`

``` python
[x.absolute() for x in pathlib.Path("/foo").glob("bar*")]
```