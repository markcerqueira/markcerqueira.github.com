---
layout: post
title: "Android Emails with Multiple File Attachments"
description: ""
category: 
tags: [android, technical, kotlin]
---

The other day I was looking to create a share intent in Android with multiple file attachments. As always, especially with anything related to security and permissions, there were many "solutions" to be found but none that worked.

After some engineering -- many trials and many errors -- here's the final output that did the trick:

{% gist markcerqueira/b8b1d16afd0784dd889896e265245766 %}

The trick is to use [FileProvider][1] to create content URIs via `FileProvider.getUriForFile` from within your app. These URIs can be used by the receiving app. You'll need to create a provider in your manifest file...

{% gist markcerqueira/e198d3917d56bc1783f4ee5c10bd2c20 %}

... and define paths in a paths file. Note that since I was creating my files in the cache directory my file path file specifies `cache-path`.

{% gist markcerqueira/dc5f9deea389cb42aa06021325aa3a8e %}

Happy coding!

[1]: https://developer.android.com/reference/android/support/v4/content/FileProvider
