---
layout: post
title: "Shout Out to GoToMeeting"
description: ""
category: 
tags: [rant]
---

When I first discovered Android's "Don't keep activities" developer option, I jumped for nerd joy. You're telling me I can force the Android operating system to be aggressive and destroy my activities every time I leave them? YES PLEASE. The end result is defensive code that will work better in low-memory situations. Getting all your activities destroyed as soon you leave them likely won't happen under normal circumstances (more likely to happen on cheaper, low memory devices). But it's always better to be safe than sorry, especially when you want to keep your customers happy and engaged with your product.

The other day I decided to give GoToMeeting a try on an Android device and was greeted with this:

<div>
	<img class="rounded-corners" style="max-width: 400px; border: 0px; margin-bottom: 10px;" src="/assets/images/posts/2013-12-20/gotomeeting.png"/>
	<p class="caption-text" style="line-height: 1.5em;"><b>Really!?</b></p>
</div>

I'm not even going to mince words; this is Citrix's development team being **LAZY**. That option was added so developers could make their apps more stable. It wasn't added so developers could detect it was turned on and then FORCE users to leave their app and turn it off. And I'm not asking for the moon here because it's not difficult to make your app work with that option turned on. You've got bundled instance state to save any pertinent data that can be retrieved upon activity recreation. Even complex objects can be bundled if you make them implement the Parcelable interface. In a rare moment, the Android SDK actually impressed me. 

This isn't rocket science. It's caring about making a decent product -- something the Citrix team doesn't seem to care much about.