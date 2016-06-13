---
layout: post
title: "Nuking Permission Errors on El Capitan"
description: ""
category: 
tags: [mac]
---
{% include JB/setup %}

I have a home server running El Capitan (10.11.5). The other day when a cron job failed to send out some emails, I took a look and was **horrified** to find my Desktop folder (yes, I have my source code folder on the Desktop) had its **permissions totally borked**.

I tried the usual solutions: ran Software Update, restarted (twice), chmod-ed everything, tried modifying permissions from the Get Info pop-up, ran Disk Utility's First Aid, [repaired disk permissions][1] from the command line (El Capitan removed this from Disk Utility for some reason), and [reset home folder permissions and ACLs][2] (access control lists not anterior cruciate ligament). **None of this did the trick.**

In desperation **I took to the internet to find random things to paste into the command line**, preferably with **sudo** in it! I saw [a post on Apple's help forums][3] by Linc Davis; I've seen him post plenty of helpful things in the past and he is Level 10 with 204,169 points which is a lot of credibility points in my book. His solution was to paste this bad boy (which unlocks all your user files and resets their ownership and ACLs to defaults) into the command line:

{% highlight bash %}
{ sudo chflags -R nouchg,nouappnd ~ $TMPDIR.. ; sudo chown -R $UID:staff ~ $_ ; sudo chmod -R u+rwX ~ $_ ; chmod -R -N ~ $_ ; } 2> /dev/null
{% endhighlight %}

**And it worked!** Thanks, Linc!

I'll keep this bad boy around for the inevitable future permissions mishaps. And I also discovered a new requirement for anything I paste into the command line: piping the output of standard error to /dev/null blackhole (i.e. 2> /dev/null)!

[1]: http://osxdaily.com/2015/11/04/verify-repair-permissions-mac-os-x/
[2]: http://kb.parallels.com/en/120432
[3]: https://discussions.apple.com/thread/5182705?start=0&tstart=0