---
layout: post
title: "Bootstrap Mac Apps with Homebrew Cask"
description: ""
category: 
tags: [mac]
---

Macs are losing their grip on "you don't need to do a clean install of our OS every year." I find myself running into frustrating issues every year or so where I throw my hands up and just do a clean install of macOS.

Fortunately, bootstrapping a clean install of macOS with all the applications you use is pretty easy with Homebrew Cask. I already keep my [shell configurations on Dropbox][1] so I added a new file that installs the packages and applications I use. When I set up a new computer, I set up Dropbox first and then run ```brew.sh``` to install all the other applications. 

Easy! 

{% gist markcerqueira/5f676f8d2e365f713c5675494f505961 %}

[1]: /2015/06/10/pro-bash-profiling/