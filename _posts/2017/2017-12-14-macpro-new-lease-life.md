---
layout: post
title: "Mac Pro 2006 - A New Lease on Life"
description: ""
category: 
tags: [mac]
---

Visiting home during the holiday season reaffirms my family's belief that software engineers and computer technicians are one in the same!

This year was special because the malfunctioning hardware was a 40+ pound "vintage" behemoth: the 2006 Mac Pro (MacPro1,1). My cousin got the machine into a state where it no longer booted and when she dragged it to the Apple store she got an Apple welcoming for a machine that is over 10 years old: they told her it was a "vintage machine" and that they couldn't help her out.

<div>
	<img class="rounded-corners" style="max-width: 700px; border: 1px;" src="{{ site.images2017 }}/12-14/dust.jpg"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px;"><strong>A decade's worth of dust!</strong></p>
</div>

This Mac Pro cost $3,000 back in 2006 and I don't think anyone would complain getting 10+ years out of a computer for that cost. But with a little over $400 in upgrades this machine feels fast, powerful, and brand-spanking new. So where did we go with $400 in upgrades?

* **OS:** Snow Leopard (10.6) ~> El Capitan (10.11)
* **CPU:** 2 x 2.66 GHz Dual-Core Xeon (no upgrades)
* **RAM:** 2 GB DDR2 ~> 18 GB DDR2
* **Graphics:** GeForce 7300 GT 256 MB ~> Nvidia GTX 660 2 GB
* **Hard drive:** 250 GB 7200 RPM ~> 520 GB Crucial SSD

Note that while this machine only officially supports Lion (10.7) with the [Pikify App][1] you can get El Capitan (10.11) running perfectly. This is clutch because you can have a spiffy, powerful machine but if software vendors don't support your "out-dated" OS you're out of luck.

<div>
	<img class="rounded-corners" style="max-width: 700px; border: 1px;" src="{{ site.images2017 }}/12-14/upgraded.jpg"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px;"><strong>Upgrade complete!</strong></p>
</div>

Here are a few gotchas and tips for anyone looking to give their MacPro1,1 a new lease on life:

* I first installed Lion to get the machine booting. But the only way to get the machine booting (even for the Lion installer) was to boot into Safe Mode (holding down the Shift key during boot). I was uanble to track down why this was happening or fix it but once I upgraded to El Capitan, the issue went away.
* El Capitan boots and runs with the stock GeForce 7300 GT but you'll notice graphical glitches pretty quickly. The machine never kicked the bucket and crashed but I would not consider it usable without a graphics card upgrade.
* More powerful graphics cards usually require some external power to work. Macs naturally do not use the standard PC molex connectors so you'll need to buy a special power cable to power your graphics card. For the GTX 660 I bought these [Mini 6 Pin to 6 Pin PCI Express][2] on Amazon and they worked perfectly.
* With an updated graphics card you won't get the Apple boot screen because the graphics card isn't recognized until the OS loads but this setup your boot times will be incredibly short. I recommend hanging onto your GeForce 7300 GT because if you have boot problems you can swap it in to help debug things.

And that's that! It was a fun experience to breath some new life into this vintage, beautiful, and heavy machine!

[1]: https://forums.macrumors.com/threads/2006-2007-mac-pro-1-1-2-1-and-os-x-el-capitan.1890435/page-56#post-22335903
[2]: https://www.amazon.com/dp/B071JJPJXW/
