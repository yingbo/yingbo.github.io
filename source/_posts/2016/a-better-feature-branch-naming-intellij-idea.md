---
title: A Better Feature Branch Naming in Intellij IDEA
date: 2016-10-19
category: Dev
tags: dev-tools
---

Intellij Idea has a very nice feature: you can customize feature branch name. When create a new task, the Intellij IDEA will help you create a new (git) branch. The default name of the branch is the task number, e.g. *FOO-1* for Jira, or *\#1* for gitlab. 

However, we can make the branch name better by adding the task summary to it. It will be like FOO-1-add-a-new-feature. To configure it, goes to Preferences-\>Tools-\>Task and change the *Feature branch name format* to {id}-{summary}
