---
layout: post
title: "Half-Baked Cookies in WKWebView"
description: ""
category: 
tags: [ios, android, objective-c]
---

Apple released WKWebView in iOS 8 to replace the problem-ridden UIWebView. [NSHipster][3] has a fairly comprehensive diff on the two classes, but the general gist is that WKWebView performs better, is more stable, and has cleaner APIs.

A really useful paradigm for using web views in native apps is to build things on the web, and then have multiple clients (e.g. iOS, Android, Mac, Windows) authenticate a web view and point to that website. It's pretty efficient: you build things once and reap the rewards across multiple platforms.

But it's not all sunshine and rainbows! See [WebKit bug 140191 - WKWebView provides no access to cookies][1]. The crux of the aforementioned system working relies on being able to authenticate the web view. Not having access to cookies makes authentication much, much more difficult. 

Fortunately, while that bug is approaching its 2 year birthday, there are plenty of ["solutions" shared on StackOverflow][2] on how to get around this problem. My personal favorite is by [user3589213][4] whose solution intercepts every navigation request, cancels it, and rebuilds the exact request but this time with the cookie inside it. Here's an Objective-C adaption:

{% gist markcerqueira/3bce0ec431dca7ca7d8c77ed679478cf %}

All this said, half-baked things keep engineers employed so I can't complain too much!

[1]: https://bugs.webkit.org/show_bug.cgi?id=140191
[2]: http://stackoverflow.com/q/26573137/265791
[3]: http://nshipster.com/wkwebkit/
[4]: http://stackoverflow.com/a/32196541/265791
