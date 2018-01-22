---
layout: post
title: "Twitch Live Dashboard Out Now on Mobile"
description: ""
category: 
tags: [twitch, ios]
---

Twitch streamers rejoice! You can now manage your channel right on your iOS or Android device with the new live dashboard.

<div style="margin: auto; width: 50%; text-align: center; margin-bottom: 1em;">
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Streamers, starting today you can access your live dashboard on mobile! Use the Twitch app to update stream info, view stats, and chat from your phone while live. <a href="https://t.co/V69RyDkdka">pic.twitter.com/V69RyDkdka</a></p>&mdash; Twitch (@Twitch) <a href="https://twitter.com/Twitch/status/954050273609207808?ref_src=twsrc%5Etfw">January 18, 2018</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
</div>

I was lucky enough to both manage the delivery of this feature on iOS and Android and also implement it on iOS. As I toy with the idea of switching into management I'm lucky enough to have a manager who's giving me opportunities to drive projects to get a taste of what it's like to be a manager.

As for iOS development, my feelings on it haven't changed to much since I last did some [serious iOS work at Evernote in November 2016][1]. I'm sad to report Xcode and the iOS ecosystem hasn't improved much in the past year. Objective-C and Swift interoperability is painful especially if you're used to the buttery smooth Java-Kotlin interoperability. I also had weird compiler errors that were fixed not by the standard "delete Derived Data and try again" but by restarting Xcode! 

The iOS ecosystem pain points aside, it was nice (and very stimulating) to work on a completely different codebase with a different set of Twitch team members. Because [Swift is like Kotlin][2], I coded all of the dashboard feature in Swift. 😏 I'm blessed to have awesome coworkers who quickly powered me up many levels on the Swift front.

I hope everyone enjoys the new live dashboard. It was a blast to build it!

[1]: {{site.base_url}}/2016/11/12/omg-swift-closures/
[2]: http://nilhcem.com/swift-is-like-kotlin/
