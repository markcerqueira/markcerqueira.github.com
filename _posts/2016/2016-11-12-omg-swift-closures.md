---
layout: post
title: "OMG Trailing Swift Closures"
description: ""
category: 
tags: [ios, swift, evernote]
---

I've been cheating on Android lately... And messing around with iOS! And by messing around I mean doing iOS at Evernote; I developed the recently released [Sign in with Google][1] feature for iOS!

When I left iOS in 2012, Objective-C was king, but now a new challenger has emerged: Swift! The other day while messing around with some Swift I discovered **trailing closures**. It's not a huge thing, but the beauty of it totally blew my mind. If you have a function that takes a closure as an argument and the closure is the last argument you can write the closure OUTSIDE the function's closing parentheses! 

Here's a simple example with a function that takes a closure, calling that function with the closure as a regular argument, and passing the closure as a trailing closure. 

{% gist markcerqueira/c35914171658c2bb256c43fe5819c113 %}

It's pretty minor but I was giddy when my coworker showed me this trick! If you don't know about trailing closures this looks like black magic so be sure to let all your friends know about this!

[1]: https://blog.evernote.com/blog/2016/11/03/sign-in-with-google-its-faster/