---
layout: post
title: "ChuckPad Online!"
description: ""
category: 
tags: [ios, objective-c, ruby, sinatra, chuckpad]
---

After over six months of development, **ChuckPad is online**! What's ChuckPad? It was Spencer's answer when I told him: "I'm bored. Anything I could build to help make your disseration kick ass?" Spencer now describes it as:

<blockquote style="margin-bottom: 1.2em;">
ChuckPad is a network-based platform for sharing code, modules, patches, and even entire musical works written with the ChucK programming language and other music programming platforms. ChuckPad provides a single repository and record of musical code from supported musical programming systems, an interface for organizing, browsing, and searching this body of code, and a readily accessible means of evaluating the musical output of code in the repository.
</blockquote>

You can check out a demo of what ChuckPad is capable of at [www.chuckpad.io][1].

ChuckPad has a bunch of components. The main [backend service][2] is a Sinatra server written in Ruby and hosted on Heroku. It was designed as a REST-based service with basic user (registration, login) and patch (creation, edit, delete) API endpoints. An [iOS client library][3] for the service was created and Spencer did the integration work for [MiniAudicle][4] (the ChucK IDE) and his dissertation project: [Auraglyph][5]. A Docker image running a [ChucK rendering service][6] with a Sinatra server exposing a simple API was also developed and deployed onto DigitalOcean. And the thing I'm most proud of as a quality-first engineer: [iOS unit tests][7] that exercises the iOS client library and -- wait for it -- [the Sinatra server][8]!

<div>
	<img class="rounded-corners" style="max-width: 800px; border: 1px;" src="/assets/images/posts/2017-01-22/chuckpad-diagram.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px;"><strong>ChuckPad!</strong></p>
</div>

We originally built ChuckPad to share ChucK code, but we decided to power it up and let it support any number of apps on a single server instance. If you're interested in joining the ChuckPad family and bring a social touch to your app, please reach out!

[1]: https://www.chuckpad.io
[2]: https://github.com/markcerqueira/chuckpad-social
[3]: https://github.com/markcerqueira/chuckpad-social-ios
[4]: http://audicle.cs.princeton.edu/mini/
[5]: http://auragly.ph/
[6]: https://github.com/markcerqueira/chuck-renderer
[7]: https://github.com/markcerqueira/hello-chuckpad
[8]: /2016/08/14/testing-sinatra-with-ios-unit-tests/
