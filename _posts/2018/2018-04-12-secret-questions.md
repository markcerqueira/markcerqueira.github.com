---
layout: post
title: "Answer Secret Questions with Gibberish"
description: ""
category: 
tags: [technical, security]
---

This week renowned security guru Brian Krebs posted (yet another) great article on how [people knowingly give away historical information on social media][1] that can sometimes reveal answers to that person's security questions. Krebs is not a fan of security questions at all and advises people to lie when answering them.

This strategy stymies attackers potentially discovering this information and using it to penetrate you, but it adds some cognitive overload as you'll have to remember the lies you tell across multiple security questions. My recommendation: **answer secret questions with gibberish**. Here's an example of what this looks like:

* **Username:** CarriersHaveArrived
* **Password:** bpJZAQdt7XnbNjFBh8DsiU2Tf
* **First pet:** beuaw8gb2rGG
* **Favorite teacher:** d4Uu8sx3hyxw3PJ
* **City you met your spouse:** 2enMrpWTFXsoEW

If you're already using a password manager you can generate additional random strings and keep the answers to your security questions alongside the other credentials. If you're not using a password manager you [really][2] [should][3].

Worth noting:

* This model doesn't work for multiple-choice security questions. And yes... a [major US airline][4] uses those. 🤦‍♂️
* I once called a bank and as part of authenticating me I had to answer one of my security questions. I recommend sticking to characters and numbers and keeping the length of your security question answers to something reasonable for cases like these. 🙃
* My password manager of choice, [1Password][5], does not support auto-filling answers to security questions. I can imagine this workflow is an edge-case but it'd be cool for them to detect the security question, find the answer, and auto-fill it. 🤞

Happy -- and safe -- computing!

[1]: https://krebsonsecurity.com/2018/04/dont-give-away-historic-details-about-yourself/
[2]: {{site.base_url}}/2015/09/22/computer-security-basics/
[3]: {{site.base_url}}/2014/04/22/recovering-from-heartbleed/
[4]: http://www.slate.com/articles/technology/future_tense/2016/03/united_airlines_uses_multiple_choice_security_questions.html
[5]: https://1password.com/
