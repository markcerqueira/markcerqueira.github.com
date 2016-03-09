---
layout: post
title: "Flexible Android Preferences"
description: ""
category: 
tags: [android]
---
{% include JB/setup %}

The recommended way of building a Settings screen in Android is to define preferences in an XML file and then load that file in a PreferenceActivity or PreferenceFragment. But that only works if you know all your preferences at compile-time. And sometimes we don't know them. Sometimes, we want to be a little more flexible with preference loading. 

As expected of Android documentation, we are told, "Your app's settings are generally pre-determined, although you can still modify the collection at runtime," but then given no documentation as to how to add or remove things from the collection. Typical. 

Fortunately, it's not difficult to do this. Enter [flexible_preferences][1] -- a short Android application that shows you how to do gymnastics with Android Preferences. Tricks include:

* Uses a custom layout file so you can show stuff besides the preferences like a loading spinner if you're fetching preferences over the wire.
* Create preferences without an XML file!
* Hide and show preferences based on input (e.g. hide all other preferences if we toggle one particular preference to the off state).

And the best part (besides using the OP LinkedHashMap data structure) is it still leverages Android's built-in preference functionality, so you get a lot of stuff for free!

[1]: https://github.com/markcerqueira/flexible_preferences
