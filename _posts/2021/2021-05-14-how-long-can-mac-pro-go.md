---
layout: post
title: "How Long Can the 2008 Mac Pro Go?"
description: ""
category: 
tags: [mac]
---

My journey to combat the [planned obsolescence][1] of my 2008 Mac Pro might have finally hit a wall. But before we cover the bad news let's talk good news!

Up until recently my boot drive was a Crucial M4 connected over SATA. Occasionally my computer would slow down and hang for several seconds at a time. SSDs are fast but they have gotten faster since 2013 when the M4 debuted. I figured a 2013 SSD must be the slowest thing in my computer so I picked up a Samsung 870 EVO. According to [UserBenchmark][2] I should expect a 77% performance increase going from the M4 to the 870 EVO! To ensure I was not losing any of those gains over SATA I picked up an [OWC Acelsior S][3] which plugs into a PCE slot and can provide double the bandwidth compared to SATA. So did it work?

<div>
    <img class="rounded-corners" style="max-width: 860px; border: 1px; margin-top: 24px;" src="{{ site.images2021 }}/05-14/consolidated-results.png"/>
    <p class="caption-text" style="line-height: 1.5em; margin-bottom: 30px; margin-top: 6px;"><strong>Crucial M4 / SATA (left) vs. 870 EVO / PCE (right)</strong></p>	
</div>

I think it worked! **Write speeds are 8x faster** and **read speeds are 1.7x faster**. It may be the placebo effect but I haven't noticed any slow downs or hangs since this upgrade. Installation of the Acelsior S was also very simple: it actually was plug-and-play.

Now the bad news. I was previously able to install High Sierra using the [macOS patchers dosdude1][4] created and things have been working swimmingly well given I'm running High Sierra on "unsupported" hardware. Turns out the 2008 Mac Pro can also install Mojave and even Catalina! I installed Catalina but then ran into the wall: Nvidia has not released macOS drivers for any version after High Sierra and my setup sports a GTX 970. There is a [workaround][5] available that force installs the drivers on unsupported macOS versions but I ran into a lot of visual glitches on my setup. Some internet sleuthing later I found out that this workaround does not support hardware acceleration so these glitches are expected. This wall isn't unsurmountable but it would involve buying a weaker graphics card (e.g. GTX 680 or ATI Radeon 4890) and flashing it so it works natively with macOS but at this point I'd be so off the beaten path I'm not sure Catalina would work well. You win, Tim Apple.

So long as the software I use on this machine continues to support High Sierra I'll be able to squeeze some more years out of it. It's impressive 13+ years later this machine works really well but the end is nigh.

[1]: {{ site.base_url }}/2019/04/26/combating-macos-planned-obsolescence
[2]: https://ssd.userbenchmark.com/Compare/Samsung-870-EVO-1TB-vs-Crucial-M4-512GB/m1445454vsm144
[3]: https://eshop.macsales.com/shop/SSD/PCIe/OWC/Mercury-Accelsior/S-Carrier
[4]: http://dosdude1.com/software.html
[5]: https://github.com/Benjamin-Dobell/nvidia-update
