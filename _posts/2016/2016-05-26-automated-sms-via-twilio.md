---
layout: post
title: "Automated SMS Via Twilio"
description: ""
category: 
tags: [technical, java, automation]
---
{% include JB/setup %}

A couple of weeks ago I wrote a simple email reminder program that pulled events from Google Calendar and then notified people about it with an email sent via the Gmail API. You can read more about the why and how in [that post][1].

After getting that up and running, I quickly got a feature request: "it'd be really cool if it could send a text message too!" I'm a strong believer in ask (kindly) and you (may) receive...

<div>
	<img class="rounded-corners" style="max-width: 400px; border: 1px solid #cdcdcd;" src="/assets/images/posts/2016-05-26/twilio.jpg"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px;"><strong></strong></p>
</div>

Setting up automated text messages was a breeze with [Twilio][3]. The API is super simple and just works. And it's pretty cheap too: $1.00 a month for a number (needed to send text messages) and under one cent ($0.0075) per text message sent.

The updated code can be found on [kendo-emailer on Github][2]. TwilioHelper and TwilioConfiguration are the main files to look at if you're interested in setting up Twilio yourself. 

[1]: /2016/03/26/automated-calendar-reminders-gmail
[2]: https://github.com/markcerqueira/kendo-emailer
[3]: https://www.twilio.com/
