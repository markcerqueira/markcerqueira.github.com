---
layout: post
title: "&lt;uses-permission-sdk-23&gt;"
description: ""
category: 
tags: [android]
---

Adding permissions to an Android app on a device running anything pre-Marshmallow breaks auto-updating because those versions of Android do not support runtime permission granting. That sucks because auto-updating helps get your app update more quickly into people's hands. Can we add a permission that we will only request on Marshmallow (and up) devices which lets us both add a permission and avoid breaking auto-updating? 

Turns out, you can! Instead of using the standard `<uses-permission>` tag, you can instead opt for `<uses-permission-sdk-23>`. The [developer documentation][1] does an uncharateriscally good job at answering all the questions I had. Namely,

<blockquote>
If a new feature is minor enough, you may prefer to disable the feature altogether on [pre-Marshmallow] devices, so the user does not have to grant additional permissions to update the app. By using the &lt;uses-permission-sdk-23&gt; element instead of &lt;uses-permission&gt;, you can request the permission only if the app is running on platforms that support the runtime permissions model, in which the user grants permissions to the app while it is running.
</blockquote>

You obviously won't have access to the permission on pre-Marshmallow devices so if the new permission is required for a core feature this won't work for you. But this seems like a great middleground that covers almost [half of Android devices][2] out there.

[1]: https://developer.android.com/guide/topics/manifest/uses-permission-sdk-23-element.html
[2]: https://developer.android.com/about/dashboards/index.html