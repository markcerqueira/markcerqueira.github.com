---
layout: post
title: "Rethinking How We Talk About Programming Languages"
description: ""
category: 
tags: [java, technical]
---

A small anecdote to warm us up... I switched from iOS to Android development in 2012. At the time, the team I joined was using the official Android IDE Eclipse. A few days in, I was about to switch back to iOS because I could not stand Eclipse. A colleague suggested I check out IntelliJ IDEA and because of that I was able to stick with it.

**It may time to rethink how we talk about programming languages.** We frequently talk about languages in a vacuum, but oftentimes, there are rich ecosystems built around languages. These include things like IDEs (e.g. IntelliJ IDEA, Android Studio) and open-source libraries to enhance the language (e.g. RxJava, Retrolambda). These things impact how I work with a language and I find myself talking about how the synergy between all these elements can supplement the deficiencies of a particular language.

Let’s take Java for example. Unlike modern languages like Kotlin and Swift, **Java does not have named arguments** so calling a method with lots of parameters can look funny. For example, let's call our `makeNetworkCall` method:

```java
makeNetworkCall(true, false, true);
```

What do these three boolean methods do? Impossible to say from just looking at this line. The method header looks like this:

```java
makeNetworkCall(boolean allowCacheResponse, boolean allowRetries, boolean followRedirects)
```

To make the call look more readable I used to do in-line comments for each parameter:

```java
makeNetworkCall(true /* allowCacheResponse */, false /* allowRetries */, 
		true /* followRedirects */);
```

This works but it's a tad annoying and requires buy-in from everyone on a project. We can cry about how Java does not have named arguments for methods and ride the high-horse of our favorite programming language that does... **Or we can rely on the ecosystem around a language to help us work around defencencies.** This is what IntelliJ IDEA added in a recent update:

<div>
	<img class="rounded-corners" style="max-width: 900px; border: 1px;" src="{{ site.images2017 }}/03-10/makeNetworkCall.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px;"><strong></strong></p>
</div>

Here we have an IDE supplementing a programming language to enhance the development experience. No new workflows are needed, no rewrites into a hot new programming language needed to reap the benefits, and no waiting for the platform you develop on to adopt the language updates before you can use new stuff. I don't talk about Java in a vaccuum anymore because that doesn't do justice to all the things I use everyday that make development easier.
