---
layout: post
title: "Recovering from Heartbleed"
description: ""
category: 
tags: [technical]
---

<div class="float-image-right">	
  	<img style="border: 0px;" src="/assets/images/posts/2014-04-22/heartbleed.png"/> 
  	<p>It turns out the backbone of secure communication across the Internet has had a catastrophic bug &mdash; Heartbleed &mdash; in it for the past two years. Yikes! One of the most frightening things about Heartbleed is no one really knows if the bug was ever exploited. Were some evil Communist people doing nefarious, Un-American things? Was a popular US information agency snooping on you to keep you safe? No one knows.<br><br>
	
	As always, it's best to err on the side of caution. If you've been getting emails from banks and online services recommending you change your passwords, it's because Heartbleed. That said, I think most people didn't even need Heartbleed to be in a compromised situation because quite frankly, most people suck at managing their security. Let's talk passwords!</p>
</div>

<!--break-->

Here's what I think a lot of people's password situation is like: **one password that is used everywhere.** I don't blame people for not having a unique password for every service because who could remember all those? Even with mnemonics, it's hard to remember a ton of passwords. You can try to get cute with your passwords, but if myAwesomeLinkedInPassword is your LinkedIn password, I have a pretty good idea what your Amazon password is going to be. 

So you don't need Heartbleed to compromise your security on the Internet; all you need is **one** service to get hacked. From there, hackers will have a field day if you used that password elsewhere. Some people have different levels of password: one password they use for sites they don't care about and a different password used only for important services. But this is still unsafe: one compromised "important service" and all your important services are at risk.

What am I getting at here? **Use a password manager.** A password manager lets you easily have unique passwords for every service you use, and it lets you make passwords as complex as possible. [A recent study][1] shows that the length of a password is more important than the composition (e.g. one symbol, one number, one upper-case letter). So make your passwords as long as possible, and make them unique. With a password manager, you won't need to know what your password is; just let the manager fill in all the info for you. I use and like 1Password (a somewhat questionable name for a product that encourages having many different passwords), but you can take your pick at the many that are out there. **Make your passwords hard to crack (long passwords) and make sure a compromised service doesn't compromise any other services (unique passwords)**.

<div>
	<img class="rounded-corners" style="max-width: 600px; border: 1px solid #000000;" src="/assets/images/posts/2014-04-22/1password.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 20px;"><strong>Use 1Password to manage hundreds of passwords!</strong></p>
</div>

How did I recover from Heartbleed? My 1Password database has over 700 logins in it! I wasn't going to update all of them, so I went through the entire list and made a folder of Important items. That list ended up containing a much more manageable 70 items. From there, **it took me an hour to update all of my important logins**. Boom! Done. I never knew the original passwords, and I don't know the new ones either. But I can tell you they are all unique and as long as possible. If there is ever another Heartbleed-level security compromise, I'll go through my Important folder and update the passwords once again.

If one service ever gets compromised, or in the case of Heartbleed &mdash; over half the internet &mdash; you shouldn't have a sinking feeling in your stomach. No worries about your Facebook friends that are about to get spammed and no worries about your bank account that may be having its funds drained. Be prepared &mdash; start using a password manager. This isn't fear-mongering. You don't have to look too far into the past to find large companies like LinkedIn and Adobe leaking millions of users' credentials. 

And while we're here, I'd be remiss not to discuss that [xkcd on password strength][2]. "correct horse battery staple" is a better password than "Tr0ub4dor&3," but you know what's ridiculously (like trillions and trillions and trillions and trillions) better than both of these? This wonderful abomination: "68qeu3Raj72e3db6upNFekivUf8688T". Here's how long the [Passfault Analyzer][3] says it would take to crack each of these passwords:

* Tr0ub4dor&3 - **less than 1 day!**
* correct horse battery staple - **1 year, 11 months**
* 8qeu3Raj72e3db6upNFekivUf8688T - **935,300,000,000,000,000,000,000,000 years**

Yes, that's a ridiculous amount of time. The universe itself is **only** 14,000,000,000 years old. If you think the universe is only 6,000 years old, this is **EVEN MORE** impressive. And best of all, I don't need to think about a stupid horse, battery, staples, or how correct one of them might be. I don't need to think at all; let a computer program do what it does best and remember things for you. 

<div>
	<img class="rounded-corners" style="max-width: 600px; border: 1px solid #000000;" src="/assets/images/posts/2014-04-22/jack_bauer.jpg"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 20px;"><strong>Not even this man can get your passwords out of you!</strong></p>
</div>

Also - the most important benefit of not knowing any of your passwords is actually not knowing them. So when Jack Bauer bursts into your house and demands you tell him the password to your Communist Nuclear Control Dashboard, you can tell him you honestly don't know. Huzzah!

[1]: http://cups.cs.cmu.edu/rshay/pubs/passwords_and_people2011.pdf
[2]: https://xkcd.com/936/
[3]: https://passfault.appspot.com/password_strength.html
