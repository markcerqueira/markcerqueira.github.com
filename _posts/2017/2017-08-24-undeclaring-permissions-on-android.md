---
layout: post
title: "Undeclaring Permissions on Android"
description: ""
category: 
tags: [android]
---

Android apps declare what permissions they want with `uses-permission` in `AndroidManifest.xml`. That's cool because you can see all the permissions your app wants, but it gets more complicated when you add external libraries to your code. If they have manifest files, those [manifests will get merged][2] with yours at build time. This means you can unknowingly add permissions to your app, which is bad because your customers can be sensitive about adding new permissions and, more importantly, it can break auto-updating for you app.

Enter undeclaring permissions! Want to ensure your app never requests location? You can explicitly flag those permissions to always be removed during manifest merging:

{% gist markcerqueira/205a335d1d2e10e51f10496186302860 %}

It might seem like a good idea to explicitly "undeclare" [dangerous permissions][1] your app does not want to ensure those don't get merged in, but the libraries that are including those permissions may not be checking if the permission has been granted. If code runs that needs those permissions you'll get a `SecurityException` and a crash. Yikes! The best course of action here is to validate the permissions in the final output from your build process like [this process Square uses][3].

[1]: https://developer.android.com/guide/topics/permissions/requesting.html#normal-dangerous
[2]: https://developer.android.com/studio/build/manifest-merge.html#inspect_the_merged_manifest_and_find_conflicts
[3]: https://medium.com/square-corner-blog/surfacing-hidden-change-to-pull-requests-6a371266e479