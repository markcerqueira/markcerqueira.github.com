---
layout: post
title: "Permissions Validation on Android"
description: ""
category: 
tags: [android]
---

I previously wrote about how unwanted permissions can sneak into your APK during manifest merging and how one can [undeclare permissions][1]. While undeclaring permissions is an option, validating the permissions in your final APK is a better approach since you can explicitly check for all the permissions you want and fail if there are any unknown permissions.

So how do we this? Fortunately it's pretty easy to whip up a script that leverages the Android Asset Packaging Tool (AAPT).

AAPT lives in the `build-tools` directory of your ever-expanding Android SDK folder. The build tools are versioned: my SDK folder contains versions 25.0.2, 25.0.3, and 26.0.1. You can do some technical interview preparation and test yourself on the somewhat mundane exercise of finding the most recent version of AAPT programmatically. For the lazy, just grab the AAPT binary and put it in the same directory as your script.

Once you've got AAPT you can run it to get the permissions of your APK: `aapt d permissions GGApp.apk`:

{% gist markcerqueira/6810139a7932fbd40f6c4e0f6bf2e54c %}

It's easy enough now to parse out the permissions and compare them against the set of permissions you are expecting in your final APK!


[1]: 2017/08/24/undeclaring-permissions-on-android