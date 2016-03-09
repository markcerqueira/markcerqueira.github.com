---
layout: post
title: "PayPal and Delusions of Grandeur"
description: ""
category: 
tags: [paypal, rant]
---
{% include JB/setup %}

**tl;dr - PayPal thinks they're awesome, but I still think they suck.**

It always blows my mind when PayPal acts like a company that's succeeding at doing everything right. After the recent iCloud hack, where a bunch of celebrities had risqué photos leaked, PayPal decided to throw a punch at Apple.

<div>
	<img class="rounded-corners" style="max-width: 400px; border: 0px;" src="/assets/images/posts/2014-10-22/paypal_ad.png"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 20px;"><strong></strong></p>
</div>

You would think with an ad like this, PayPal is really at the forefront of protecting their customers. **WRONG**. 

<!--break-->

In June, I raged hard when PayPal said they were ["kicking the tires"](/2014/06/04/kicking-the-tires-with-paypal/) when it came to integrating Apple's TouchID API into their iOS app. Raged because they were talking about integrating TouchID when their iOS app didn't even support two-factor authentication. Months later, **the PayPal iOS app still does not support two-factor authentication** and of course, does not support TouchID either. Upping the ante on how bad they are, the app now instructs you to "download the new app" that supports two-factor authentication. **No such version exists.**

<div>
	<img class="rounded-corners" style="max-width: 400px; border: 0px;" src="/assets/images/posts/2014-10-22/ios_lies.png"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 20px;"><strong>It's all a lie!</strong></p>
</div>

When I log onto PayPal on my computer, which supports two-factor authentication, **I'm presented with the two-factor authentication prompt... EVERY SINGLE TIME**. Most services with two-factor authentication let you check a box to "remember this computer." This drops an auth token on your computer that usually expires in a really, really long time. When you try logging on again, the auth token is used to skip the security code part of authentication. PayPal can't be troubled with making security more convenient. **Every time you log onto PayPal, you will need to enter a security code.**

<div>
	<img class="rounded-corners" style="max-width: 600px; border: 0px;" src="/assets/images/posts/2014-10-22/security_key.png"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 20px;"><strong>An exercise in frustration!</strong></p>
</div>

People say there are trade-offs between security and convenience. But some security does not need to come at the cost of all convenience. "Keep your money safer by turning off two-factor authentication because our iOS app does not support it and it's really annoying on our website" says **PayPal -- a company that truly doesn't care about your security.**
