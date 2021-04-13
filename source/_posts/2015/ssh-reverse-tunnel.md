---
title: SSH Reverse Tunnel
date: 2015-02-16
categories: Network
tags: 
 - ssh
 - network
---

The SSH has many advance usages. The reverse tunnel is a good example and a very useful one. It answers the question: if a user can ssh from a server A to a server B, can the user ssh back from B to A, even A is behind a router? In my case, it is very helpful. I have a desktop in the office, but the office VPN has not been set up yet. How can I ssh to my office desktop from home? The answer is SSH reverse tunnel, using a server with a public IP as a jumper. Followings show how did I do it.

<!--more-->
As a start, we need to ssh from the server A (office desktop) to server B (the server with a public IP). It has more parameters than common SSH, to enable reverse tunnel:

` ssh -R 19999:localhost:22 my_username_on_server_b@serer_b`{lang="bash"}

The port 22 is the office desktop ssh server port. The standard is 22, valid for most of cases. The 19999 is going to be used to ssh port on server B.

Next I 'll show how do I ssh back from the server B to my desktop. It's pretty simple:  
` ssh -p 19999 my_username_on_server_a@serer_b`{lang="bash"}

Note how do we use the port 19999. Another important thing is this time we use my\_username\_on\_server\_a. In many cases a user uses a same user name on both servers, however, mine are different.

After that I already jump to my office desktop . However, it is possible that the ssh connection from the first step gone. How can I fix it while I am at home? At first I thought I needed a cron job to keep reconnecting, till I found the [autossh](http://www.harding.motd.ca/autossh/ "Autossh"). The usage is very simple:

` autossh -M 19990 -f -N -o "PubkeyAuthentication=yes" -o "PasswordAuthentication=no" -R 19999:localhost:22  my_username_on_server_b@serer_b`{lang="bash"}

Now I have a stable connection. Unless the office has a power off, I am pretty safe now.
