---
layout: post
title: "Auto-Grinding in Final Fantasy Type 0"
description: ""
category: 
tags: [video games, final fantasy, technical]
---
{% include JB/setup %}

**Final Fantasy Type-0** was originally released in Japan for the PSP in 2011. Four years later, an enhanced HD port made its way to the rest of the world. I've played through the game. Aside from the vestiges of the PSP that could not be fixed (bad camera, small areas, low-quality NPC sprites) the game is great. The battle system is fun, fast, and action-packed. The music -- by Takeharu Ishimoto -- is AWESOME! And if you exclude the conclusion, the story is pretty coherent for a Final Fantasy game. 

The interesting thing about this game is there really is no single main character, or even a small, manageable cast of main characters. You command a group of **fourteen** powerful cadets at a military academy of a nation at war. When you deploy on a mission, you pick **three** cadets for your main party. If a cadet in the main party falls, you can't use that cadet for the remainder of the mission. But you can replace that cadet with one from your reserves. There is no experience share so cadets only gain experience if they are actively fighting. Unless you want to bank your success on no cadets dying, **it's in your best interest to level up more than three cadets.** 

<div>
	<img class="rounded-corners" style="max-width: 600px; margin-top: 10px;" src="/assets/images/posts/2015-04-02/fftype0.png"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 24px;"><strong>So many characters to level up!</strong></p>
</div>

In my younger days, I'd relish the opportunity to spend hours upon hours grinding all fourteen characters. But the me of today ~~can't~~ shouldn't do that. Enter [Auto Agito][1] - a little workflow I conjured up to automatically level up your cadets. This takes advantage of a feature of the game: **Secret Training**. You can send a cadet to Secret Training, take a break from playing the game (like go to sleep or work), and then return later and reap free experience. By moving the PS4's system clock forward you can simulate going to work or sleep! Auto Agito automates and repeats this entire flow: starting Secret Training, advancing time, and then returning to reap the experience. Here's a video showing one iteration of the entire process.

<div style="text-align: center; margin-bottom: 20px;">
<iframe width="560" height="315" src="//www.youtube-nocookie.com/embed/HDU4rSxBPw8?rel=0" frameborder="0"></iframe>
</div>

Check out the [README][2] for specifics on equipment needed and steps involved. Yes, grinding is a quintessential part of the JRPG experience. But when I see room for automation, I can't help but see how far I can take things. Happy (automatic) leveling!

[1]: https://github.com/markcerqueira/auto-agito
[2]: https://github.com/markcerqueira/auto-agito/blob/master/README.md


