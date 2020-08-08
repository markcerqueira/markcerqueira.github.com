---
layout: post
title: "Team-Building Activities and Easy Audio Capture on macOS"
description: ""
category: 
tags: [mac, engineering management]
---

As work from home for many companies has been extended indefinitely the need for keeping your team engaged has become even more important. I have found scheduling a meeting with the team with no agenda and no discussion related to work has been a small thing that has worked well. There are a ton of fun ways to spend this time. Ones we've tried and enjoyed:

* Icebreaker questions on [plenty of websites][1] - lots of opportunities to learn fun facts about your team
* Drawing shenanigans on [skribblio][2] - supports up to 12 players
* Codenames on [horsepaste.com][3] - hit or miss in my opinion because Codenames is hard
* Quizbowl on [protobowl.com][4] - middle school is challenging enough
* Deck-building games like [Dominion][5] - the base game is free, expansions require a nominally priced subscription
* Party games like [Jackbox][6] - lots of options here, great for groups that are 3-8 people

What does any of this have to do with audio capture on macOS? Jackbox, the last item on the above list is played with one person running the game and then sharing their screen with everyone else playing. On macOS you can share video but there is no simple, built-in way to capture and share audio over video conference software like Google Meet. There are some guides available online for how to do this but the simplest, but not cheapest, option to get this working is [Loopback][7] by Rogue Amoeba.

<div>
    <img class="rounded-corners" style="max-width: 800px; border: 1px; margin-top: 24px;" src="{{ site.images2020 }}/06-20/loopback.png"/>
    <p class="caption-text" style="line-height: 1.5em"><strong></strong></p>
</div>

Loopback lets you create new audio input devices that can capture audio from a variety of sources. In the above screenshot I'm capturing audio from an HyperX headset, the Macbook Pro's internal microphone, Jackbox Party Pack 4, and Jackbox Party Pack 5. This all funnels into a new virtual audio input device called HyperX + Jackbox that I can set as my input device in the sound preferences for macOS.

<div>
    <img class="rounded-corners" style="max-width: 800px; border: 1px; margin-top: 24px;" src="{{ site.images2020 }}/06-20/volume-prefs.png"/>
    <p class="caption-text" style="line-height: 1.5em"><strong></strong></p>
</div>

And you're good to go! If there are other apps you need to capture audio from it's easy in Loopback to add them to this virtual audio device.

[1]: https://www.google.com/search?q=icebreaker+questions
[2]: https://skribbl.io/
[3]: https://www.horsepaste.com/
[4]: https://protobowl.com/
[5]: https://dominion.games/
[6]: https://www.jackboxgames.com/the-ultimate-guide-to-player-counts-in-each-jackbox-game/
[7]: https://rogueamoeba.com/loopback/
