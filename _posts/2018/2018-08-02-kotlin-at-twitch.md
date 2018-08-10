---
layout: post
title: "Kotlin at Twitch"
description: ""
category: 
tags: [technical, kotlin, java, twitch]
---

A little over a year ago, Kotlin was announced as an official language for Android at Google I/O 2017. Adoption of new technologies in existing ecosystems can be challenging: sometimes intertia-filled engineers resist the changing times, sometimes leadership believe so strongly in a "if it ain't broke don't fix it" mentality, and sometimes the build processes just make adopting new stuff incredibly impractical. 

The Twitch Android team bucked those challenges and started shipping Kotlin as soon as Kotlin became a first-class citizen on Android. A few weeks ago our codebase sailed smoothly into becoming a **majority** Kotlin codebase! 

<div>
	<img class="rounded-corners" style="max-width: 900px; border: 1px; margin-bottom: 0px;" src="{{ site.images2018 }}/08-02/kotlin.png"/>
	<p class="caption-text" style="line-height: 1.0em; margin-bottom: 24px;"><strong>Kreygasm</strong></p>
</div>

In under a year we've leveraged Kotlin to refactor and reduce technical debt, reduce the number of null-checks, eliminate NullPointerExceptions (but introducing some `Intrinsics.checkParameterIsNotNull`), write a Kotlin DSL-based UI testing framework, marvel in awe of how few Kotlin lines one needs to do things that take many in Java, and increase the quality of our app for us -- the developers -- and our customers.

It's also worth noting that, a year ago, everyone on the team considered themselves Kotlin newbies. Our success with Kotlin was not an accident. Our successful adoption was a result of a combination of Jetbrains being amazing at building IDEs and programming languages, helpful developer tools (all hail [Code -> Convert Java File to Kotlin File][2] and [Kotlinify code][3]), an already thriving developer community that quickly dove into Kotlin. Most (cheesily) importantly it required some patience and trust amongst the team to take on something new, unknown, and exciting.

Excited by the power of memes and helping us close in on the mythical Android codebase with no Java? Twitch is hiring! Is dealing with subpar IDEs like Xcode more of your flavor? We're also hiring for our iOS team that is well on its way to being a majority Swift codebase! My [Twitter][1] DMs are open; slide on into them!

[1]: https://twitter.com/markmcerqueira
[2]: {{ site.base_url }}/2017/08/16/inflection-point-mobile-development-tools/
[3]: {{ site.base_url }}/2018/03/08/excellent-tooling-teacher/
