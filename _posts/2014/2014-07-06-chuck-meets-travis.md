---
layout: post
title: "ChucK Meets Travis"
description: ""
category: 
tags: [ci, chuck]
---

Ge, Spencer, and I sometimes talk about our dreams when we're playing StarCraft. During the small windows of time when we're not playing StarCraft, we're all making some sort of headway towards our dreams. Today, one of those dreams has come to pass. <strong>ChucK is now set up for continuous integration on Travis.</strong> Every commit to ChucK triggers Travis to check that ChucK compiles and passes a suite of unit tests.

<div>
	<img class="rounded-corners" style="max-width: 600px; border: 1px solid #000000;" src="/assets/images/posts/2014-07-06/madness.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 20px;"><strong></strong></p>
</div>

Who's Travis? Travis is a free (for public repositories) hosted continuous integration service. With zero knowledge of Travis (but plenty of tears shed dabbling in release engineering at Smule), it only took an hour to get everything set up and running. You add one file to your repository (.travis.yml) and set up your scripts in there; it's straightforward and **just works**. They say you get what you pay for, so I feel kind of bad because Travis is so good I feel like someone is getting robbed. How good is it? It builds and tests pull requests! Gone are the days where you would have to meticulously review the changes you were about to pull into your project. If Travis THINKS it's okay, you KNOW it's okay. But, perhaps double-checking isn't a bad idea!

<div>
	<img class="rounded-corners" style="max-width: 700px; border: 1px solid #000000;" src="/assets/images/posts/2014-07-06/travis_1604.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 20px;"><strong>travis.yml file that supports both Linux and Mac</strong></p>
</div>

Travis has a multi-platform feature that's in beta, and we're already taking full advantage of that to run our tests on both Linux (Ubuntu 12.04) and Mac (Mavericks 10.9.2). When Travis  adds more platform and OS configurations, we'll run (not walk) to get those configurations set up. And while the current 150+ tests are a great start for unit testing, we're looking to expand testing to make it more thorough and exhaustive. ChucK has a pretty awesome user community that is good at pushing ChucK to the limits (and occasionally breaking it), so we see a future filled with more tests, and consequently a greater and more stable (i.e. more stable than incredibly stable) ChucK. 

Want more? Check out [ChucK on Travis](https://travis-ci.org/ccrma/chuck), check out [ChucK on GitHub](https://github.com/ccrma/chuck), read all about ChucK on its  [webpage](http://chuck.cs.princeton.edu/), or [join the ChucK community](http://chuck.cs.princeton.edu/community/). **Happy ChucKing you motherchuckers! **