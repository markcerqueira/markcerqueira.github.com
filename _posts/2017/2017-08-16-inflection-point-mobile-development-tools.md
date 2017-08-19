---
layout: post
title: "The Inflection Point for Mobile Development Tools"
description: ""
category: 
tags: [android, ios, swift, objective-c, kotlin, java]
---

Having done a fair amount of development for both iOS and Android the most significnat inflection point in the development tools landscape came at Google I/O 2013 when Google announced a partnership with JetBrains to build a new Android IDE, Android Studio, on top of the IntelliJ IDEA platform. And since 2013 the landscape for Android development has been on the up-and-up while Xcode doesn't even fully support (see how long it took Xcode to support renaming a variable in Swift files) the hot new language Apple has been pushing: Swift.

<div>
	<img class="rounded-corners" style="max-width: 800px; border: 1px;" src="{{ site.images2017 }}/08-16/kotlin_convert.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px;"><strong>This is what supporting a new language looks like!</strong></p>
</div>

And in another example of a \"[programming language is an ecosystem not a simply a language][1]," Android Studio makes using the hot new language Google is pushing, Kotlin (also developed by JetBrains) super easy. There is literally a menu option to convert a Java file to Kotlin and if you copy Java code and paste it in a Kotlin file, it'll automatically convert it for you. It's not perfect as it doesn't always leverage all of Kotlin's idiomatic features, but it works and it lowers the barrier for people hesistant to dive into a new thing.

In the meanwhile, I encourage iOS developers to wait and pray for Apple to announce a parternership with JetBrains. 

[1]: 2017/03/10/rethinking-talk-programming-languages/