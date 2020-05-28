---
layout: post
title: "Migrating to Cloudflare Registrar"
description: ""
category: 
tags: [cloudflare]
---

While Cloudflare is better known for distributed denial-of-service (DDOS) mitigation and content delivery network (CDN) services, I have long relied on them to help mitigate my profound ineptitude about DNS. Given Cloudflare's DNS changes propagate faster than your run-of-the-mill registrar it's been an invaluable ally in my trial-and-error approach to getting my DNS settings correctly. If your nameservers aren't pointed at diva.ns.cloudflare.com and merlin.ns.cloudflare.com you're definitely doing DNS wrong.

In December when Cloudflare announced they were getting into the domain registrar business at wholesale prices I hit that Early Access button fast. Today, the day has finally arrived!

<div>
    <img class="rounded-corners" style="max-width: 600px; border: 1px; margin-top: 24px;" src="{{ site.images2019 }}/01-16/cloudflare.png"/>
    <p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px;"><strong></strong></p>
</div>

I currently use Dreamhost as my domain registrar. Dreamhost currently charges $11.99 to register a .com domain and $13.95 each year thereafter. For .com domains, Cloudflare charges $8.03 ($7.85 wholesale price + $0.18 ICANN fee) a year. While $6 in savings per year per domain won't save or break the bank it's nice to know my domains will be with a registrar that will never charge ["anything more than the wholesale price each TLD charges"][1].

I also rely on Dreamhost for web hosting services but with GitHub Pages and Heroku the only service I now use is their email forwarding service. With services like [Mailgun][2] that provide easy (and free) routing of incoming emails, paying for web hosting services at this point also is very unnecessary. **Update:** Mailgun put its Routing feature behind a $35 / month paywall. [ImprovMX][3] offers free email routing if you've got only a handful of domains and aliases to set up. If you have more its paid option is relatively afforable compared to Mailgun's new paypal.

I've been a happy Cloudflare customer for a while now and while they technically won't be making any money off me providing domains at wholesale cost I'm happy to bring my domains closer to their nameservers.

[1]: https://blog.cloudflare.com/cloudflare-registrar/
[2]: https://www.mailgun.com/
[3]: https://app.improvmx.com/
