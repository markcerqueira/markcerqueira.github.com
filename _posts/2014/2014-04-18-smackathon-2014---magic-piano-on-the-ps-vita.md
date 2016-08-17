---
layout: post
title: "Smackathon 2014 - Magic Piano on the PS Vita"
description: ""
category: 
tags: [smule]
---

Today wrapped up Smule's first Smackathon (a Smulean hackathon) of 2014. Armed with clairvoyant vision and a burning desire to be amazing, The Backstreet Trolls (me and Josh Wu) set out to port the popular Magic Piano to the PlayStation Vita. 

<div>
	<img class="rounded-corners" style="max-width: 600px; border: 1px solid #000000;" src="/assets/images/posts/2014-04-18/running.jpg"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 20px;"><strong></strong></p>
</div>

<!--break-->

Sony provides development tools for building and running applications on a Vita. The language of choice is C#, which provided a nearly seamless transition for someone coming from Android (Java) development. Contrary to its name, C# is actually more like Java than C. Fortunately, Sony also provides a bunch of great examples we were able to mess around with. The IDE -- PlayStation Mobile Studio -- wasn't great. It confounded us many times with odd behavior and unhelpful error messages. When you think Eclipse is a better IDE, you know you've got some problems.

<div>
	<img class="rounded-corners" style="max-width: 600px;" src="/assets/images/posts/2014-04-18/ide.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 20px;"><strong>A weak IDE, but the Simulator wasn't half bad.</strong></p>
</div>

Josh took care of everything audio. For the actual piano sounds, we implemented a system similar to the Android version of Magic Piano: we played sounds from a bank of sound files. Josh also handled converting some songs into a format that our application could parse. I took care of the rest: reading in the music files Josh wrote up, placing the notes on the screen, and making them fall gracefully down the screen. Within a day, we had a prototype. 

<div>
	<img class="rounded-corners" style="max-width: 600px; border: 1px solid #000000;" src="/assets/images/posts/2014-04-18/troll-mode.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 20px;"><strong>Troll Mode enabled!</strong></p>
</div>

With 24 hours left, we knew that there was much room for improvement. I took the the road more travelled and made tweaks to gameplay, optimized texture loading and sprite rendering,  and <i>\*gasp\*</i> refactored and cleaned up our code to make it more maintainable and extendable. But Josh took the road less traveled. I added a button for enabling "troll mode," and let Josh run wild. In troll mode, the images representing notes became Smule employees making troll faces, and the piano sounds were all replaced with us singing our approximation of said notes. He took the road less traveled, and it made all the difference.

<div>
	<img class="rounded-corners" style="max-width: 600px; border: 1px solid #000000;" src="/assets/images/posts/2014-04-18/backstreet-trolls.jpg"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 20px;"><strong>The Backstreet Trolls with Magic Piano for PS Vita!</strong></p>
</div>

Our project was awesome. All the Smuleans put in great effort and it's pretty spectacular what we all produced in such a short amount of time. The Backstreet Trolls are eagerly looking forward to the next Smackathon, which will close out what should be an eventful 2014!