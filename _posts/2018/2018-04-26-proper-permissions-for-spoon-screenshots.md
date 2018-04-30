---
layout: post
title: "Proper Permissions for Spoon Screenshots"
description: ""
category: 
tags: [android, technical, twitch]
---

I've been working on setting up a UI testing framework for the Android team here at Twitch. [Good QA is a puzzle][1] so working through the challenges of UI tests is a must if you want to reliably deliver quality with each and every release. Fortunately between former, very knowledgable colleagues on the subject and great libraries like Espresso and Spoon setting up UI tests on Android isn't too challenging.

I did run into one pretty big hiccup: [getting screenshots working with Spoon][2]. Fortunately after repeatedly banging my head on my desk, breaking the problem down into smaller solvable problems, and typing things here and there, I got it resolved!

And sharing is caring so let's walk through it!

The key to getting screenshots working is to get your app to have the `WRITE_EXTERNAL_STORAGE` permission but strip it of the `maxSdkVersion` attribute. Your test app does not need it; only the app your testing does. Note that even if you don't specify this attribute, it might get merged into your manifest during manifest merging. If you open `AndroidManifest.xml` you can click on Merged Manifest near the bottom left to see the merged manifest. Adding this snippet to your manifest file will ensure the attribute gets stripped away.

{% gist markcerqueira/cb7301fdb3a6564f8f99804e93720257 %}

Then you can try building the app and test app, granting permissions, and then running the tests.

{% gist markcerqueira/e4942b8dfd0afdf91038a26511cc4615 %}

If each of these steps works for you, you should have screenshots after the Spoon runner finishes running! A few notes:

* At first I was using the [Gradle Spoon plugin][3] which basically wraps the above script into a single Gradle task. I opted to use this script because it let me see which steps were failing and let me avoid learning more about Gradle. 🙃
* `spoon-runner-2.0.0-20180425-all.jar` was assembled by checking out the master branch of the Spoon project, opening the project in Android Studio, and assembling the spoon-runner target. I am using [Spoon][4] 2 (not yet released) because it [runs each test in separate instrumentation process][5] which makes things generally more stable.
* I highly recommend passing the `--debug` flag to the Spoon runner command. It lets you see which test classes are running but most importantly helped me realized GIF generation is super slow, hence why I disabled it with `--disable-gif`.

Happy UI testing!

[1]: {{site.base_url}}/2017/09/16/qa-is-a-puzzle/
[2]: https://stackoverflow.com/questions/49040071/runtimeexception-unable-to-create-output-dir-storage-emulated-0-app-spoon-scr
[3]: https://github.com/jaredsburrows/gradle-spoon-plugin
[4]: https://github.com/square/spoon
[5]: https://github.com/square/spoon/pull/456

[10]: https://github.com/square/spoon/issues/484#issuecomment-371627713
