---
layout: post
title: "Measuring Android WebView Content Size"
description: ""
category: 
tags: [android, technical]
---

Situation: you're loading content into an Android WebView that's embedded in another view (i.e. not a fullscreen WebView) and you want to ensure the WebView resizes to the height of the content it contains.

Easy, right? Loaded question: it's Android so you know the answer is absolutely not. StackOverflow answers provide many ways to **potentially** do this, but most don't work. I only found one way -- using some Javascript magic -- to reliably get the content height. 

{% gist markcerqueira/10b7ec3e526ec123429ac887a955b6b6 %}
