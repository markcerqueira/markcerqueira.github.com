---
layout: post
title: "Kotlin Kills the Arrow Anti-Pattern"
description: ""
category: 
tags: [technical, kotlin, java]
---

I read a great [article on the Arrow Anti-Pattern][1] the other day. Shortly thereafter on the same day I also thought about Kotlin and boom! I realized something I've known all along: **Kotlin kills the Arrow Anti-Pattern**!

Consider this Java method:

{% gist markcerqueira/f540ac5c65b135bf98d27a10f78eadc0 %}

The anti-pattern here is the series of ```if``` checks (for null) that make this code look like an arrow. With Kotlin's safe call operator (```?```) and Elvis operator (```?:```) we can write that method in a single line!

{% gist markcerqueira/ba834b6c5b420d6a4894fbf019f0ec2d %}

Boom! The arrow is dead! While checking nullness is not the only case arrows can emerge, null checking is a pervasive painpoint in Java so these operators make our lives much better. 

[1]: http://wiki.c2.com/?ArrowAntiPattern