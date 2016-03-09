---
layout: post
title: "PayPal - One Step Forward, One Step Backward"
description: ""
category: 
tags: [paypal, rant]
---
{% include JB/setup %}

It's about DAMN time! PayPal has FINALLY added support for two-factor authentication in their iOS app.

<div>
	<img class="rounded-corners" style="max-width: 300px;" src="/assets/images/posts/2015-03-28/pp-2factor.png"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 24px;"><strong>FINALLY!</strong></p>
</div>

But, it wouldn't be PayPal if they didn't do something stupid to balance out this step forward. Turns out, logging into PayPal on your computer is more annoying if you use 2-factor authentication. How so?

Go to paypal.com and enter your login credentials (i.e. email and password) and press enter. You'll be taken to another screen where you're asked to **enter your login credentials again.** Why? The page says, "We're sorry. We need you to login again to verify additional security information." You enter your credentials again and after that you are finally prompted for your security code. PayPal just reinvented two-factor login as a 3-step process with 2 of the steps sharing the same form of authentication!

<div>
	<img class="rounded-corners" style="max-width: 800px;" src="/assets/images/posts/2015-03-28/pp-stupid.png"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 24px;"><strong></strong></p>
</div>

During the first query, if I have two factor authentication turned on, just route the request to the proper endpoint. Don't redirect me to another webpage where I have to enter my login details again. I'm the customer. I'm the one who gets to be lazy. Not you, PayPal! ME! ME ME ME!!!

The one thing PayPal does get right is apologizing upfront: "We're sorry." You should be sorry; because this is mind-bogglingly stupid.
