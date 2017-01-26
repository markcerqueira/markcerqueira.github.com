---
layout: post
title: "Testing Sinatra... With iOS Unit Tests"
description: ""
category: 
tags: [ios, objective-c, ruby, sinatra, automation, chuckpad]
---

I spent last week on vacation... hacking with Spencer on integrating [ChuckPad Social][1] into [MiniAudicle][2] for iPad. The week's work involved building out the iOS library to interact with the Sinatra-based backend. While building that, I realized I was doing a lot of repetitive tasks (e.g. creating a user, uploading patches, updating patches) which could be automated with some testing.

I never got around to writing unit tests for the backend so I could've written those, but why do that when I could **write iOS unit tests to exercise both my iOS code and the Sinatra backend**? That's way more efficient! And since [2016 is the year of automation][4] for me, let's add more automation!

It was super easy to set up iOS unit tests; the Android developer in me cried a river. I set up the tests so they ran against an instance of the ChuckPad Social service running on my local machine. iOS even has a nice mechanism -- XCTestExpectations -- for testing asynchronous things. Below is a snippet of the tests. You can see all tests in the [hello-chuckpad][3] repository.

{% gist markcerqueira/2d4197539f3b335436219e19074c8186 %}

These tests gave me some assurances that both my iOS library code and the Sinatra backend were behaving as expected on both ends. It also let me more rapidly iterate on the codebase and catch bad behavior (a.k.a. "bugs I wrote") before I passed the code on to Spencer. Writing these tests was time definitely well spent!

[1]: https://github.com/markcerqueira/chuckpad-social
[2]: http://audicle.cs.princeton.edu/mini/
[3]: https://github.com/markcerqueira/hello-chuckpad/tree/master/unit-tests
[4]: /2016/01/01/automating-2016/
