---
layout: post
title: "ACME Responder for Sinatra"
description: ""
category: 
tags: [ruby, sinatra]
---

Scenario: you've got a snazzy Sinatra server running on Heroku. You just got a fancy custom domain and you now want to get an SSL certificate for it.

Solution: [Damien Mathieu][1] from the Heroku team built a cool utility to **automate SSL certificate generation and renewal**: [sabanyon][2]. Bonus points for naming it after a [delicious Italian dessert][3]! The instructions exist (never a given), are easy to follow (happens sometimes), and work as expected (frequently rare). Thanks, Damien!

Damien includes challenge responder code for a bunch of different apps, but not Sinatra. Fortunately, the Ruby example provided only needs a few tweaks to get everything working:

{% gist 2fe0d1ab7654febaa6735316b72b3882 %}

Now your domain will have an SSL certificate forever!

[1]: http://dmathieu.com/
[2]: https://github.com/dmathieu/sabayon
[3]: https://en.wikipedia.org/wiki/Zabaione