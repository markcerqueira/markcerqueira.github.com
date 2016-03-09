---
layout: post
title: "Getting Google Play on Genymotion"
description: ""
category: 
tags: [android, final fantasy, technical]
---
{% include JB/setup %}

I've got a project in the works that requires running an Android app -- Final Fantasy Record Keeper (FFRK) -- on my computer. BlueStacks lets you install apps from the Play Store easily but BlueStacks also kind of sucks -- especially the Mac (beta) version.

[**Genymotion**][1] has been a reliable and flexible Android emulator, but unfortunately it does not come with Google Play services out of the box, so installing applications from the Play Store is not possible. But with a little bit of work, you can power up your Genymotion emulator! These steps are largely adapted from [these instructions posted on the XDA-Developers][4], and feature some additional information regarding steps that tripped me up. 

<div>
	<img class="rounded-corners" style="max-width: 400px; margin-top: 10px; border: 0px;" src="/assets/images/posts/2015-04-22/ffrk-title.png"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 24px;"><strong></strong></p>
</div>

1. Set up the **Android Debug Bridge** (adb). It comes bundled with the Android SDK. Google it if you don't have it set up yet.

2. Download and install [**Genymotion**][2] and [**VirtualBox**][3]. Genymotion requires VirtualBox to work. 

3. Open Genymotion and add a new Android emulator. Originally I went with the Google Nexus 7 - 4.4.4, but that ended up causing FFRK to crash immediately on launch. The **Google Nexus 7 2013 - 4.3** worked for me so use that one.

4. Download the **ARM Translation Installer** (9.4 MB) and **Google Apps for Android 4.3** (91.7 MB). Both can be downloaded from this [helpful XDA-Developer post][4]. It is very important that you **do NOT unzip the ARM Translation zip file**. If you do, it'll overwrite itself and make itself unusable in the next step. If your browser is set to automatically launch files, disable that behavior.

5. Launch the Genymotion virtual machine (VM) and **drag the ARM Translation Zip file onto the VM**. The file will transfer and then you will be asked if you want to flash the VM. Agree, wait a bit, and then reboot the VM using *adb reboot*. The adb command can take a little while to run so give it some time. If you don't get asked to flash the VM, you probably unzipped the ARM Translation zip file. Go back to step 4.

<!--break-->

Now there are two ways to install FFRK. You can download the APK from an external source and install it via adb (less steps, faster) OR you can install Google Play services on your VM and then install FFRK via the Play Store (more steps, but useful if you're using a Google account to transfer game data from another device).

<hr class="separator"/>

**Direct Installation**

1. Download the FFRK APK from a site like [APK Downloader][6]. The package name for FFRK is com.dena.west.FFRK.

2. Install the APK via adb: *adb install com.dena.west.FFRK.apk*. Note that if you had done this before flashing your VM with the ARM Translator, you'd get the INSTALL_FAILED_CPU_ABI_INCOMPATIBLE error. This, time it should install just fine. 

<div>
	<img class="rounded-corners" style="max-width: 500px; margin-top: 10px; border: 0px;" src="/assets/images/posts/2015-04-22/direct.png"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 24px;"><strong></strong></p>
</div>

<hr class="separator"/>

**Install via Google Play Store**

1. **Drag the Google Apps file onto the VM**. The file transfers, and then you agree to the disclaimer, wait, and reboot via adb. 

2. Once rebooted, you'll likely see Google Play Services crashing repeatedly. Don't worry. Just **make your way to the Play Store and log into a Google account**. Theoretically, you would then see a list of apps and services that could be updated, but I saw nothing so I just waited a bit (assuming things were upgrading in the background without my knowledge) and then rebooted the VM. After a few reboots, the Play Store updated and the Play Services crashes went away. 

3. Search for Final Fantasy Record Keeper and hit the **INSTALL** button. 

<div>
	<img class="rounded-corners" style="max-width: 400px; margin-top: 10px; border: 0px;" src="/assets/images/posts/2015-04-22/ffrk-playstore.png"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 24px;"><strong></strong></p>
</div>

<hr class="separator"/>

**Post-Installation Optimization**

1. FFRK should now launch and run, but it might be a bit laggy. To try to help reduce this, I quit the VM and reduced the resolution of the machine from 1200 x 1920 (320 DPI) to 600 x 960 (160 DPI).

2. The redditor lilmacaco (little monkey in Portuguese!) found that [turning down animation scales][5] improved performance as well. Follow the aforementioned link for instructions on turning on Developer Options and then turning down animation scales. He recommends turning them down to .5, but I just turned mine off completely. 

<div>
	<img class="rounded-corners" style="max-width: 400px; margin-top: 10px; border: 0px;" src="/assets/images/posts/2015-04-22/ffrk-animations.png"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 24px;"><strong></strong></p>
</div>

<hr class="separator"/>

Please let me know via [Twitter][6] or [reddit][7] if you have any more optimizations or find steps that could use more clarification. Happy FFRKing on Genymotion! 

[1]: https://www.genymotion.com/#!/
[2]: https://www.genymotion.com/#!/download
[3]: https://www.virtualbox.org/wiki/Downloads
[4]: http://forum.xda-developers.com/showthread.php?t=2528952
[5]: https://www.reddit.com/r/FFRecordKeeper/comments/31yetr/pc_players_which_emulator_do_you_use/cq6v94n
[6]: https://twitter.com/markmcerqueira
[7]: https://reddit.com/u/marktronic
