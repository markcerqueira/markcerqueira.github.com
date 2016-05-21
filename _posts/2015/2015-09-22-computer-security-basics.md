---
layout: post
title: "Computer Security Basics"
description: ""
category: 
tags: [technical]
---
{% include JB/setup %}

In our rapidly technologizing world, staying secure means adapting to novel threats. Staying safe isn't difficult. A little effort here and there will keep you out of a lot of trouble. Here are some basic computer security tips.

1. **Passwords** - Most people are terrible about passwords: using just a single password for everything. This is bad. When you hear about a website getting hacked, and passwords getting leaked your first thought should not be, "Crap! What other sites was I using that password on?" It should be, "Oh... I guess I need to update my password on that one site." You need unique passwords for everything. Don't share passwords unless you are okay with someone getting into that service. The unique password lifestyle isn’t as hard as it sounds. There are plenty of password managers that make staying secure easy. I like [1Password][1].

2. **Two-factor authentication** - Two-factor means you need two things to log onto a particular service. You are probably already familiar with one-factor authentication when a service just asks you for your password. Two-factor requires another form of verification. Usually this is a code sent via SMS to your phone or a code generated on your phone with an app like Google Authenticator. For any critical services (anything involving access to your email or money) it’s important to set up two-factor authentication. This makes accessing your account more difficult for adversaries and isn’t as big an inconvenience as some people make it out to be. For most services, you are allowed to flag a device as personal. Once flagged, it won’t ask for a code again.

3. **Back up your data** - Devices break, devices get stolen, and sometimes you accidentally delete important files. Keeping your data safe is important and it’s something that’s often overlooked because you don’t really see the value of your data until it’s long gone. The cost of backing up your data is chump change compared to the cost of attempting to recover data from a bad hard drive or the mental anguish suffered if a thief makes off with your computer. I wrote a whole post about backing up, aptly named [Back It Up][2]. For the impatient: just get [CrashPlan][3] and let it automagically back everything up for you to the cloud.

4. **Keep your computer up-to-date** - Is your computer nagging you to install some updates? Go ahead and let it do it's thing, especially if they mention security in them. Keeping your computer updated leaves you less vulnerable to all the bad stuff out there.

5. **Enable Click-to-Play in your browser** - Most web browsers load all content when you visit a page. A page can include content that requires a plug-in like Flash or Silverlight to run. If these plug-ins have some vulnerability, malware can silently target those vulnerabilities. If you see an update for Java, Adobe Reader, Quicktime, Silverlight or Flash install them ASAP! This [How to Geek article][4] explains how to set up click-to-play on the more popular web browsers.

This is certainly not an exhaustive list, but it's a decent start to protecting yourself. Did I get something totally wrong or something super important is missing here? [Send me a tweet!](https://twitter.com/markmcerqueira) Cheers!

[1]: https://agilebits.com/onepassword
[2]: http://mark.gg/2014/01/24/back-it-up/
[3]: https://www.code42.com/crashplan/
[4]: http://www.howtogeek.com/188059/how-to-enable-click-to-play-plugins-in-every-web-browser/
