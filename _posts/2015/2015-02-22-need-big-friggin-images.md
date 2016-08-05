---
layout: post
title: "Need Big Friggin' Images?"
description: ""
category: 
tags: [technical]
---

I found myself in need of some **big friggin' images** the other day. After scouring the web for a while and coming up with paltry-sized images (ONLY hundreds of megabytes), I decided to just create some myself. I whipped up a quick Python script -- [**imggen.py**][1] -- that uses the [Pillow image library][2] to generate square images where each pixel is a random color. It's certainly no remarkable coding achievement, but the output is pretty pretty. 

<div>
	<img class="rounded-corners" style="max-width: 800px; margin-top: 10px; border: 0px;" src="/assets/images/posts/2015-02-22/RGBA_400_regular.PNG"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 24px;"><strong>160k Pixels!</strong></p>
</div>

**The images also got really big and took a long time to generate as the size increased.** Running the script with size 2000 pixels generated a 13.9 MB image in 23 seconds; 16000 pixels, 22 minutes, 875 MB; 34000 pixels, 107 minutes, 3.95 GB! Yes, I know plenty about time and space complexity for algorithms; just let me enjoy this moment as my computer struggles to generate these images! 

I toyed around the script to generate images in **different styles.** Below is a composition of four variations of imggen.py. Clockwise from top left: the **original** script that generates a random color for every pixel, a **rows** version that picks a random color and uses that for the entire row, a **grayscale** version that generates a random grayscale color for every pixel, and a **columns** version that is similar to the rows version, but for columns instead. 

<div>
	<img class="rounded-corners" style="max-width: 800px; margin-top: 10px; border: 0px;" src="/assets/images/posts/2015-02-22/RGBA_400_collection.PNG"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 24px;"><strong>640k Pixels in 4 Servings</strong></p>
</div>

Wow! Such beauty! Much pixels! Check out [**imggen.py**][1] and you can be a (computer) artist too!

[1]: https://gist.github.com/markcerqueira/459fa0a3aae001d3471f
[2]: https://pillow.readthedocs.org/