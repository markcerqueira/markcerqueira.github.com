---
layout: post
title: "Xcode is Not Environmentally Friendly"
description: ""
category: 
tags: [technical, xcode]
---

Dread sets in whenever a new version of Xcode releases. It's dreadful because Xcode is a bloated monolith; downloading Xcode means download an 7+ GB bundle that includes an IDE, simulators, and the appleOS family of SDKs, all from scratch, every single time there is an update. Frustration is compounded with frequently failed downloads when trying to download from Apple's Developer website and the Mac App Store also randomly, silently failing to install Xcode.

<div>
    <img class="rounded-corners" style="max-width: 700px; border: 1px; margin-top: 24px;" src="{{ site.images2020 }}/04-20/xcode.png"/>
    <p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px;"><strong></strong></p>
</div>

Compare this to Android where the IDE (Android Studio) is a (comparatively) light 768 MB download. Updates to Android Studio are downloaded and applied as small patches. The Android SDK, build tools, and emulators live separately from the IDE so when you get a new version of Android Studio there's no need to get all that stuff again.

<div>
    <img class="rounded-corners" style="max-width: 700px; border: 1px; margin-top: 24px;" src="{{ site.images2020 }}/04-20/as.png"/>
    <p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px;"><strong></strong></p>
</div>

Ultimately Xcode is not environmentally friendly. From the article [Does Irresponsible Web Development Contribute to Global Warming?][1] by Emerge Interactive:

<blockquote>
	According to the American Council for an Energy-Efficient Economy it takes 5.12 kWh of electricity per gigabyte of transferred data. And according to the Department of Energy the average US power plant expends 600 grams of carbon dioxide for every kWh generated. **That means that transferring 1GB of data produces 3kg of CO<sub>2</sub>.
</blockquote>

A download of Xcode generates 22 kg of CO<sub>2</sub>. That's the equivalent of burning [two and half gallons of gasoline][2]! A more modularized Xcode would not only be more environmentally friendly, it would make updates for developers less dreadful. Be green and be kind, Apple!

[1]: https://www.emergeinteractive.com/insights/detail/does-irresponsible-web-development-contribute-to-global-warming/
[2]: https://www.epa.gov/greenvehicles/greenhouse-gas-emissions-typical-passenger-vehicle

