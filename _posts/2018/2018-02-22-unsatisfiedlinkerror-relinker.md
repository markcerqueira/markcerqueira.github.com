---
layout: post
title: "Satisfying the UnsatisfiedLinkError in ReLinker"
description: ""
category: 
tags: [twitch, android]
---

In the Twitch Android app we leverage some native C++ code. Android's default `PackageManager` used to load libraries in these situations is brittle so we leverage [ReLinker][1] to provide more robust loading. We recently moved from compiling our C++ externally to setting it as a Gradle dependency and letting Gradle handle compilation.

As we rolled out the update that included this change, we saw a bunch of UnsatisfiedLinkErrors pop up:

<div>
	<img class="rounded-corners" style="max-width: 800px; border: 1px;" src="{{ site.images2018 }}/02-22/unsatisfied.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px;"><strong></strong></p>
</div>

The vast majority of these errors were happening on Android 4.x. We didn't have to look far for a potential solution as ReLinker has an awesome README that mentions that [recursive loading][2] can solve intra-library dependencies that the system's library loader may fail to "on older versions of Android."

Our theory is that moving from externally compiling the native code to having Gradle do it changed how the library's dependencies were being packaged and older devices were choking because of this change. So we threw the `recursively()` method at it and fortunately it solved our problem 100%.

[1]: https://github.com/KeepSafe/ReLinker
[2]: https://github.com/KeepSafe/ReLinker#recursive-loading
