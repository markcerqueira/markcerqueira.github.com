---
layout: post
title: "Managing Multiple Android SDKs/NDKs in Jenkins"
description: ""
category: 
tags: [ci, android]
---
{% include JB/setup %}

At Smule, we use a single node to run Jenkins for our Android projects. When building our projects that rely on both the SDK and NDK tools, we defined SDK_DIR and NDK_DIR as global environmental variables. But what happens when the tools are updated? In 2012, Google released [5 major updates](http://developer.android.com/tools/sdk/tools-notes.html) to its Android SDK tools and [6 revisions](http://developer.android.com/tools/sdk/ndk/index.html#Revisions) to its NDK toolset. Synchronizing a single team to upgrade is relatively straightforward. But when coordinating different teams that may be in different phases of a release cycle, a smooth transition is oftentimes difficult to achieve. Furthermore, if we upgrade the tools and later need to build an older tag, we are not recreating the build as it truly was, since the tools are now upgraded.

<!--break-->

To solve these problems, we moved the configuration of the SDK and NDK path from the global Jenkins configuration environment and put it somewhere where it could be project-independent and version controlled. Each project now contains a bash file that looks like this:

{% highlight bash %}
# Available NDK Paths
NDK_8B_PATH="/Users/Jenkins/android-ndk-r8b"
NDK_8D_PATH="/Users/Jenkins/android-ndk-r8d"

# Available SDK Paths
SDK_16_PATH="/Users/Jenkins/android-sdk-16-macosx/tools"
SDK_21_PATH="/Users/Jenkins/android-sdk-21-macosx/tools"

export PATH=$PATH:$NDK_8D_PATH:$SDK_21_PATH:$SDK_21_PATH/platform-tools
{% endhighlight %}

This requires some bookkeeping to maintain various versions of the SDK and NDK toolsets on a single machine or across multiple nodes for multi-node setups. Now, a team can select the SDK and NDK they want whenever they are ready and with zero impact on any other teams while still preserving the ability to accurately create older builds.

<p style="margin-bottom: 4px;">The basic Jenkins workflow for our Android jobs now looks like:</p>
1. Check out the project.
2. Execute the script within the project that exports our desired NDK and SDK paths. This step gives us flexibility and helps us recreate older builds/tags accurately.
3. Execute the script that writes out the SDK/NDK paths to required places (e.g. local.properties).
4. Any extra configuration you need to do before you build.
5. Build it!
6. Discard any changes made to files. If on the next pull we update the SDK/NDK paths, we will want to make sure any file changes are gone.
7. Post-build archiving/publishers.
