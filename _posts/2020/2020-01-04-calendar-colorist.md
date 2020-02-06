---
layout: post
title: "Managing Management - Calendar Colorist!"
description: ""
category: 
tags: [managing management, engineering management, kotlin]
---

When I shared my [Managing Management - Time Management via Color-Coded Calendar][1] blog post on [Twitter][2] it got some nice traction because of a generous retweet from Will Larson. In the blog post I mention automating color-coding in the future via the Google Calendar API and someone asked for me to share that system once I built it.

Striking while the iron is hot... **Calendar Colorist is here**!

<div>
    <img class="rounded-corners" style="border: 1px; margin-top: 0px;" src="{{ site.images2020 }}/01-04/calendar-colorist.gif"/>
    <p class="caption-text" style="line-height: 1.5em; margin-bottom: 30px; margin-top: 6px;"></p>
</div>

Calendar Colorist is a simple rule-based utility written in Kotlin to color code your Google Calendar. The README on [GitHub][3] walks you through setting it up to color code your calendar. I hope it's helpful for your color-coding needs!

P.S. For bonus points, once you've got it all set up, configure that personal [TeamCity][7] server you have (it's free!) to run it once a week to fully automate this automated process!

<div>
    <img class="rounded-corners" style="max-width: 800px; border: 1px; margin-top: 0px;" src="{{ site.images2020 }}/01-04/teamcity.png"/>
    <p class="caption-text" style="line-height: 1.5em; margin-bottom: 30px; margin-top: 6px;"><strong>Fully automated!</strong></p>
</div>

P.P.S. A few thoughts on Kotlin after taking it on this most recent whirl: 

* Kotlin's interoperability with Java is fantastic. I used the Java version of the [Google Calendar API][4] and had zero drama getting things working. It literally just worked™️ although it would be nice if Google added nullability annotations to their code.
* Kotlin extensions are also great for extending classes in libraries that cannot be easily edited. I added [several properties and functions][5] to the Event class via an extensions to make Events easier to work with.
* I got tripped up using Kotlin's `let` with a trailing Elvis operator `?:`. I assumed in an expression like `a()?.let { ... } ?: b()` that so long as `a()` was not null `b()` would never get executed but turns out the `...` inside the let block can end up getting us to `b()`. Many thanks to Heath for [helping me diagnose and fix this one][6]! 🙏

{{ site.managing_management }}

[1]: {{site.base_url}}/2019/12/16/management-systems-calendaring/
[2]: https://twitter.com/markmcerqueira/status/1212797842189770752
[3]: https://github.com/markcerqueira/calendar-colorist
[4]: https://developers.google.com/calendar/quickstart/java
[5]: https://github.com/markcerqueira/calendar-colorist/blob/master/src/main/java/EventExtension.kt#L8
[6]: https://twitter.com/heathborders/status/1213938020392558592
[7]: https://www.jetbrains.com/teamcity/
