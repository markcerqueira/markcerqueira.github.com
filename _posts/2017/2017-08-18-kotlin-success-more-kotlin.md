---
layout: post
title: "Kotlin's Success Requires More Kotlin"
description: ""
category: 
tags: [technical, kotlin, java]
---

I believe self-driving cars will work best once we've got a critical mass of them on the road. The period in between where we've got some self-driving cars and (flawed) humans driving together there will still be accidents. Once self-driving cars rule the roads I expect we'll see these cars start talking to each other instead of relying only on sensors to sort out surroundings. This information sharing will give individual participants more knowledge and make the entire mesh perform better.

**Kotlin is like a self-driving car: it's cool on its own but will be better the more Kotlin it's interoperating with.**

One of Kotlin's strongest strengths is that nullability is fully built into the language: a `String` is a guaranteed non-null string while a `String?` could contain a valid string but it could also be null. Passing in a `String?` when a `String` is required is a compile-time error and not a runtime NullPointerException crash like we get in Java. It's worth noting Java has the `@NonNull` and `@Nullable` annotations but these are not enforced at compile-time.

Nullability in Kotlin isn't super sexy, but it's useful as it forces us to tackle nullability when writing code rather than sprinkling null-checks in our code after we write it.

But while you're in a mixed language environment you can't really rely on nullability fully because when going from Java to Kotlin you don't get the compile-time checks on nullability. In Java, try declaring a parameter `@Nullable` and pass it to a Kotlin method that requires a non-null explicitly. You get a warning but the code compiles! That's not good. Make the Java file Kotlin and you'll be forced to sort that out. 

How do we solve this? Use more Kotlin. Ask third party libraries to provide Kotlin implementations for at least their external interface. While you're still using Java annotate methods and parameters so when you convert to Kotlin down the road it will be easier.  Kotlin will shine when we've got nullability built in from the first line of code executed to the last when the customer successfully exits the app after having a delightful, bug-free experience! 