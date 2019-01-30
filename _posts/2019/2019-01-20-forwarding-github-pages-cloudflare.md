---
layout: post
title: "Redirecting to HTTPS Enforced GitHub Pages via Cloudflare"
description: ""
category: 
tags: [cloudflare]
---

The recent [migration to Cloudflare Registrar][1] has been relatively pain-free except for one thing: getting domains to redirect to my GitHub Pages blog with a custom domain and HTTPS enforced. I've previously [wrote about how to set this up][2] so if you still don't have a custom domain set up you'll want to pick one of your fancy domains to be the primary and then follow along here for the rest. In this post we'll show how to redirect markcerqueira.com to my primary domain name mark.gg.

First, a quick review on how you do redirects in Cloudflare because this was also non-trivial for my DNS-impaired skillset. Cloudflare has a Page Rules section which allows defining (only up to 3 if you're not a paying customer) custom rules which include a handy Forwarding URL command.

<div>
	<img class="rounded-corners" style="border: 1px; max-width: 800px;" src="{{ site.images2019 }}/01-20/pagerules.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 20px;"><strong></strong></p>
</div>

The trick here though is that Page Rules do not apply unless traffic is passing through Cloudflare. What this means is you'll need an A record in the DNS section that gets traffic to pass through Cloudflare. You can pick a dummy IP address like 1.2.3.4 for the value of this record but the most important thing is to ensure the Cloudflare icon is turned on; this means traffic will route through Cloudflare. You'll never hit 1.2.3.4 because the Page Rule with do a redirect first. Since we're on the DNS page we also add a CNAME for www so people-inclined-to-type-www will still get routed to the proper place. 

<div>
	<img class="rounded-corners" style="border: 1px; max-width: 800px;" src="{{ site.images2019 }}/01-20/dns.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 20px;"><strong></strong></p>
</div>

Voilà! This should work but this redirect gave me security errors (e.g. Your connection is not secure) for a while. After a visit to the Crypto page and some (increasingly rare) reading of documentation on what things do I realized my issue was that SSL was set to Flexible which forbids HTTPS support at the origin. My assumption that Flexible SSL would better serve this scenario compared to Full or Full (Strict) was my great undoing. **Setting the SSL setting to Full (Strict) cleared up the security errors I was seeing.**

For good measure here are all the Crypto settings I have configured for my redirecting domain that currently work without issue:

* SSL - Full (Strict)
* Always Use HTTPS - On
* Authenticated Origin Pulls - On
* Minimum TLS Version - TLS 1.0
* Opportunistic Encryption - On
* Onion Routing - On
* Automatic HTTPS Rewrites - On

Hope that helps! If I got something wrong please <a href="https://twitter.com/markmcerqueira">send me a tweet or slide in my DMs</a>. Cheers and thanks for reading!

[1]: {{ site.base_url }}/2019/01/16/migrating-to-cloudflare-registrar/
[2]: {{ site.base_url }}/2018/05/06/setting-up-https-github-pages/
