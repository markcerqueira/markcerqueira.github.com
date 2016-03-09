---
layout: post
title: "Drivers Still Suck on Windows"
description: ""
category: 
tags: [rant, technical]
---
{% include JB/setup %}

It's been a while since I used a Windows machine. While I do virtualize sometimes to run Windows-only software, I haven't considered myself a Windows user since the summer of 2006 when I switched to a Mac. It's been a while since I had to work with a Windows machine, but some things never change: **driver installation is still a harrowing experience on Windows**.

<div>
	<img class="rounded-corners" style="max-width: 600px; border: 0px;" src="/assets/images/posts/2014-09-02/guess.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 30px;"><strong>Milk makes your bones stronger. Drivers make your Windows PC usable.</strong></p>
</div>

A friend recently bought a Windows laptop (a Toshiba Satellite L55-A5284) and wanted me to help him set it up. Setting it up involved not paying Toshiba their exorbitant cost for an SSD and installing one ourselves, upgrading the RAM, and downgrading (i.e. upgrading) from Windows 8 to Windows 7. It was somewhat of a struggle but we were able to eventually take the machine apart, upgrade to an SSD, upgrade the RAM, "acceptably" put the machine back together, and install Windows 7. Yet, the real struggle hadn't even begun...

<!--break-->

A driver-less Windows machine is a pathetic thing. The display resolution is terrible, the trackpad is wonky, and connecting to a network with either Ethernet or Wi-Fi is impossible. Fortunately, laptop manufacturers have webpages for you to download drivers. Unfortunately, that's where most of the good ends.

For example, downloading the driver for the Wi-Fi card presents me with the following options:

<div>
	<img class="rounded-corners" style="max-width: 600px;" src="/assets/images/posts/2014-09-02/list.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 30px;"><strong>How lucky are you feeling?</strong></p>
</div>

Welp, this is hard. Not only are there four **different drivers for the same functional piece of hardware** (i.e. Wi-Fi card), there are also **multiple versions of some drivers**. I'm not quite sure why Toshiba doesn't hide the older versions. Newer should always be better right? As luck would have it, my friend's laptop had the Realtek driver which I downloaded last because it was at the end of the list. 

<div>
	<img class="rounded-corners" style="max-width: 600px; border: 0px;" src="/assets/images/posts/2014-09-02/mulan.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 30px;"><strong>Whooooooo makes that Wi-Fi card I cannot see?</strong></p>
</div>

With Internet connectivity, Windows Update helped me out and installed a bunch of the drivers, but there were a few stragglers left. So, back I went to Toshiba's website for **a game of cat-and-mouse trying to find the missing drivers**. An hour or so later, I was down to a single device -- USB2.0-CRW -- missing its driver. Some Google-fu revealed this was the multi-card reader, but **nothing on Toshiba's website seemed to work**.

Then I discovered driver-installing-helping-software like Driver Easy and Driver Max that scan your computer for hardware and find the drivers for you. Huzzah! Sounds wonderful. I wish I had found it earlier! Driver Easy was easily (pun intended) able to find the USB2.0-CRW driver and install it for me. 

<div>
	<img class="rounded-corners" style="max-width: 600px; border: 0px;" src="/assets/images/posts/2014-09-02/drivermax.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 30px;"><strong>Only $19.90 a month to unlock the MAX!</strong></p>
</div>

Sadly -- and very maddening -- Driver Easy also reported that most of the drivers I installed from Toshiba's website were outdated. Cool! Let's just update them all. What!? I need to buy a pro version of this software to get that awesome update all functionality? If you don't pony up the cash not only do you not get that feature, **Driver Max makes you wait 5+ minutes for each download** and **Driver Easy limits your download speed to 30 KB/s.** Both applications also block you from downloading multiple drivers at once, so grab a drink or a few drinks.

Sigh...
