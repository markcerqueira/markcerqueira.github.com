---
layout: post
title: "Automated Google Calendar Reminders Over Gmail"
description: ""
category: 
tags: [automation, technical, java]
---
{% include JB/setup %}

I do instructor scheduling for the [San Francisco Kendo Dojo][2]. Google Calendar and creating events that repeat monthly solves most of the scheduling puzzle. But I was sometimes getting questions about who was teaching and when. I decided weekly reminders directly to instructors' email inboxes with the week's schedule was the way to keep everyone up-to-date. In keeping with **[2016's automation goal][4]**, I decided to **automate these weekly reminders**. 

<div>
	<img class="rounded-corners" style="max-width: 600px; border: 1px solid #000000;" src="/assets/images/posts/2016-03-26/email.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px;"><strong>An email sent from kendo-emailer</strong></p>
</div>

[kendo-emailer][1] is a Java-based project that uses the **Google Calendar and Gmail API**. It pulls events from the kendo instructor calendar, creates a nice email for any events within the next 2 weeks, and sends it to all the instructors. **For anyone teaching in the coming week, their last name is put in the subject.** The idea here is that even if someone does not open the email, they will hopefully see their name in the subject line! 

<div>
	<img class="rounded-corners" style="max-width: 800px; border: 1px solid #000000;" src="/assets/images/posts/2016-03-26/cronnix.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px;"><strong>Quick and dirty cron with CronniX</strong></p>
</div>

I use [CronniX][3] to schedule weekly emails by running this project on my home server. To ensure I don't email instructors anything weird I have the project email only me (preview mode) on Friday afternoon. If everything looks good, I don't need to fix anything for the email sent to everyone (production mode) on Saturday. This preview/production system is a **cheap and easy way to let me "deploy" code** that impacts people. 

I'm happy to report that the reminder emails have been very well-received! I generalized [kendo-emailer][1] to share it without compromising personal information (e.g. instructor names and emails are pulled from a CSV file that is gitignored). I hope it's helpful for anyone looking to do some automation with Google Calendar and Gmail.

[1]: https://github.com/markcerqueira/kendo-emailer
[2]: http://www.sanfranciscokendo.org
[3]: http://www.macupdate.com/app/mac/7486/cronnix
[4]: /2016/01/01/automating-2016/
