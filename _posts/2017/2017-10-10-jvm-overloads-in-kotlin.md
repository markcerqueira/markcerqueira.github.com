---
layout: post
title: "@JvmOverloads in Kotlin"
description: ""
category: 
tags: [technical, kotlin, java]
---

`@JvmStatic` and `@JvmField` are well-known annotations that can be used in Kotlin files to expose companion object methods and constants. But the other day I had an "oh wow" moment with `@JvmOverloads` so now it has joined the pantheon of great JVM annotations provied by Kotlin. Consider this method in a network utility written in Kotlin:

{% gist markcerqueira/5278d5f8ce6e9cd60ff80a17a37e1d44 %}

From a Kotlin file you can call this method in many ways:

{% gist markcerqueira/420654cb714cc45d2e0d1c4caf9fc139 %}

But from Java you're a little more restricted. Without the `@JvmOverloads` annotation from a Java file you would need to call the method with all three parameters: `makeNetworkCall("www.mark.gg", 4, true)`. Adding @JvmOverloads generates two overloaded methods for you using the default values specified in the function declaration.

<div>
	<img class="rounded-corners" style="max-width: 800px; border: 1px;" src="{{ site.images2017 }}/10-10/jvm-overloads.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px;"><strong></strong></p>
</div>

New programming languages like Swift and Kotlin can (naïvely) be evaluted solely on the merits of the language itself but a more accurate evaluation will look at the ecosystem: Xcode, Objective-C, Swift and Android Studio, Java, Kotlin. Annotations like `@JvmOverloads` make Kotlin a team player in an already established ecosystem giving it much more potential for disrupting and improving that ecosystem.
