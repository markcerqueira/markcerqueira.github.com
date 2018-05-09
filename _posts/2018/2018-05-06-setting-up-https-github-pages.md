---
layout: post
title: "Setting Up HTTPS for Custom Domain GitHub Pages"
description: ""
category: 
tags: []
---

Picking Jekyll running on GitHub Pages for this blog five years ago has been one of the better (lucky) technical decisions I made as both products continue to get tender love and care. This week, GitHub delivered another awesome feature: [HTTPS on GitHub Pages for sites with custom domains][1]. Setting this up gets you the coveted 🔒Secure stamp next to your URL.

<div>
	<img class="rounded-corners" style="border: 1px;" src="{{ site.images2018 }}/05-06/markgghttps.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 20px;"><strong></strong></p>
</div>

HTTPS is awesome and gives readers confidence that no nefarious actor is intercepting my site and modifying its contents to include falsehoods like "Xcode is a great development tool that empowers developers to output amazing work" or "Siri is a digital assistant." We absolutely cannot risk falsehoods like this being transmitted on this blog.

Setting up HTTPS on GitHub pages is [straightforward][3] but it took a small amount of digging to get the [`www` subdomain][2] working (so you can visit either mark.gg or www.mark.gg and still be 🔒Secure). I configure my domain via Cloudflare because it has a great interface and propagates my DNS changes compared to changing them via a domain registrar.

You'll want your DNS settings to look like:

| Type  | Name    | Value  |
|-------|---------|------------------|
| A     | mark.gg | 185.199.108.153  |
| A     | mark.gg | 185.199.109.153  |
| A     | mark.gg | 185.199.110.153  |
| A     | mark.gg | 185.199.111.153  |
| CNAME | www     | markcerqueira.github.io |

Once you've done this you can go to the GitHub Pages section of your repository to wrap up the process.

<div>
	<img class="rounded-corners" style="border: 1px;" src="{{ site.images2018 }}/05-06/settings.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 20px;"><strong></strong></p>
</div>

If you can't click the Enforce HTTPS checkbox (orange box) you can fix this by clearing your custom domain in the Custom domain section (red box), saving, and then setting it again. This resets your CNAME file and kicks off something on GitHub's end that allows you to check Enforce HTTPS. After checking the box give it some time to generate the certificate and you'll be well on your way to 🔒Secure!

<🔒Secure> **Xcode sucks!** <\🔒Secure>

[1]: https://blog.github.com/2018-05-01-github-pages-custom-domains-https/
[2]: https://help.github.com/articles/setting-up-a-www-subdomain/
[3]: https://help.github.com/articles/setting-up-an-apex-domain/
