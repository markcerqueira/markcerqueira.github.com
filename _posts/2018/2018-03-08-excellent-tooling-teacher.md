---
layout: post
title: "Excellent Tooling is a Great Teacher"
description: ""
category: 
tags: [technical, kotlin, java]
---

I'm a [big believer][2] in programming languages living in an [ecosystem][1] and not in a [vaccuum chamber][3].

Today's thought takes me back to my on-site interview at Evernote. Given I had both iOS and Android experience (but had done Android more recently) I interviewed with some Android engineers and one iOS engineer. During the interview I was asked if my Objective-C code would look Java-esque; in short, was I still capable of writing idiomatic Objective-C code.

Writing Kotlin today that interview question comes up again and again in my mind. I still feel like I'm writing Java but in Kotlin and learning how to make it more idiomatic as I go along. Learning comes from a bunch of places like coworkers, Kotlin documentation, and example code but another great teacher has been Android Studio.

<div>
	<img class="rounded-corners" style="max-width: 700px; border: 1px; margin-top: 24px;" src="{{ site.images2018 }}/03-08/kotlin-0.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 15px;"><strong></strong></p>
</div>

Here's some Kotlin code I wrote recently. It's not the best way to accomplish what I'm doing in Kotlin. Android Studio inspections to the rescue! Within a second of writing this code I got some green squiggle marks under the `for`. Command-enter and then selecting `Replace with count{}` gave me this:

<div>
	<img class="rounded-corners" style="max-width: 900px; border: 1px; margin-top: 24px;" src="{{ site.images2018 }}/03-08/kotlin-1.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 15px;"><strong></strong></p>
</div>

Yes I could pore through documentation and blog posts about writing idiomatic Kotlin but there's nothing more frictionless than having your development tool give you a hand when it sees you're writing Kotlin in a Java-esque way. Thanks Android Studio for teaching me about `count`!

[1]: {{site.base_url}}/2017/08/16/inflection-point-mobile-development-tools/
[2]: {{site.base_url}}/2017/03/10/rethinking-talk-programming-languages/
[3]: {{site.base_url}}/2017/10/10/jvm-overloads-in-kotlin/
