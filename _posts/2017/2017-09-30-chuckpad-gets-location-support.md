---
layout: post
title: "ChuckPad Gets Location Support"
description: ""
category: 
tags: [ios, objective-c, ruby, sinatra, automation, chuckpad, testing]
---

It's been a few months (ages when talking about code bases) since I've done any work on the ChuckPad [Sinatra server][1] and [iOS API wrapper][2] but this week I added support:

* Setting location (latitude and longitude) on patches
* API to fetch a random set of patches from around the world

There's nothing super exciting about this, but what is noteworthy was how easy the [testing system][3] I had set up made adding new functionality. I configured the Sinatra server, made changes to the iOS API wrapper, and wrote some tests to exercise the new functionality on the client and server. This allowed me to verify the system worked end-to-end. Bonus points to the tests I had previously written catching some things I broke when making the changes.

We can file this under `#EngineeringExcellence`.

[1]: https://github.com/markcerqueira/chuckpad-social
[2]: https://github.com/markcerqueira/chuckpad-social-ios
[3]: {{site.base_url}}/2016/08/14/testing-sinatra-with-ios-unit-tests
