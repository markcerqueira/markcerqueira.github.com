---
layout: post
title: "Breaking Codenames with Binary"
description: ""
category: 
tags: [tabletop, technical]
---
{% include JB/setup %}

**Codenames** is an incredibly fun, deep, and addicting tabletop game. The game revolves around a 5 x 5 grid of words. Two teams race to pick out the eight (or nine if you go first) words that belong to your team. Two spymasters give their teams one-word clues that can point to words on a 5 x 5 board of words. Clues that let teams pick more words correctly are better of course. The first team to get all their words win!

It's fun. It's funny. It's hard. But we can make this game easy, not fun, and more like a math exercise. How? **With binary!** We can do this because:

* While a particular word can be blue, red, black, or beige **we only care about whether it's a word belonging to our team or not**. Ours or not ours. Binary. 
* The numbers from **zero to a hundred can be expressed as SINGLE words**. Yes, the numbers [21 through 99 are hyphenated][3]!
* Given we're restricted to one word clues that will be numbers ranging from 0 to 100, we can **usually express 6 bits of information** and sometimes 7: 111111 (6 bits) = 63, 1111111 (7 bits) = 127, but 1000000 (7 bits) = 64. In some cases were we have a lot of 0s at the end, we will express less than 6 bits of information (e.g. 01 is equivalent to 000000001).

What does this all mean? With 5 x 5 grid of words the spymaster has up to **25 bits of information** they need to get across to their team. Using only one word you can transmit about 6 bits of information. So you'll about need 5 turns to share 25 bits because 6 + 6 + 6 + 6 + 6 > 25, but depending on how the words you need to pick are placed (i.e. the last few spaces on the board do not belong to your team so you'll win before you need to share this information) and if you can squeeze in a 7-bit number, you'll **ON AVERAGE only need 4 turns to win**!

Here's an example of what this would look like for a particular configuration. In this example, we'll play the role of the red team. The red team goes first so we'll need to pick out 9 words. 

<div>
	<img class="rounded-corners" style="max-width: 700px; border: 0px;" src="/assets/images/posts/2016-03-28/codenames.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px;"><strong>Victory in 4 turns!</strong></p>
</div>

* 1st turn say "**70**" - 1000110, 7 bits, yellow text
* 2nd turn say "**20**" - 10100, 5 bits, green text
* 3rd turn say "**64**" - 1000000, 7 bits, pink text
* 4th turn say "**44**" - 101100, 6 bits,  white text

Note that the green text number (i.e. 10100) highlights the case mentioned above about expressing less than 6 bits of information when we have a lot of 0s.

My friends and I have played a lot but we have not gotten to the point where we can win in 4 turns. That said, are we going to use this system? **Probably not...** unless we're in a life-and-death situation which requires us to win Codenames to survive!

If you want to learn more about Codenames, GeekDad wrote a [great overview and review][1] or if you want to buy it hop on over to [Amazon][2].

[1]: http://geekdad.com/2015/08/codenames/
[2]: http://www.amazon.com/Czech-Games-00031CGE-Codenames/dp/B014Q1XX9S/
[3]: http://www.grammarly.com/handbook/punctuation/hyphen/11/hyphen-in-compound-numbers/