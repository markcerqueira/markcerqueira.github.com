---
layout: post
title: "Managing Management - Effective JIRA"
description: ""
category: 
tags: [managing management, engineering management, jira]
---

Whether you love (few people) or hate (more people) JIRA, effectively using it can minimize the time you spend on it and maximize the value you get out of it. Ineffective JIRA looks like:

* Browsing for issues from the Projects view - Good luck finding what you're looking for!
* Creating, curating, sharing a list of custom Filters - Good luck navigating between filters and getting people to start leveraging a new filter!
* Creating a custom Dashboards - Good luck introducing any change when everyone has their own dashboard!
* Manually reviewing things to keep issues in order - Good luck remembering to do this consistently and not lose your mind!

Effective JIRA gives you everything your team needs in one place. When issues are in a bad state, you don't have to remember to clean them up, you get notified. How do you get here? **Rich Filters** and **Subscriptions to Filters**.

**Rich Filters** let you define a base filter (e.g. project = Android) and then add a variety of Static Filters (i.e. fixed JQL), Dynamic Filters (e.g. dynamic fields like Assignee), Smart Filters (e.g. converting Last Updated to distinct values using JQL). Creating a dashboard based on a Rich Filter allows you to present all these filters as buttons. My team has moved from using personal, custom dashboards to using a single Rich Filter powered dashboard. When we talk about anything in JIRA now, it's all in one place and we're all speaking the same language.

<div>
    <img class="rounded-corners" style="max-width: 900px; border: 1px; margin-top: 24px;" src="{{ site.images2019 }}/04-08/rich.png"/>
    <p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px; margin-top: 18px;"><strong>Buttons along the top filter everything else on the screen</strong></p>
</div>

**Subscriptions to Filters** leverages individual filters but don't worry - you won't be visting the filter much because the filter is only used to find issues and email you if any are found. For example, if an issue is marked as closed but doesn't have a Fix Version, someone looking at it won't immediately know what version of the app has the fix. To stay ahead of these situations, create filters for issues that aren't compliant and then add a subscription that notifies you via email. You'll get pinged closer to the time the issues fall into a bad state which makes cleaning them up much easier.

<div>
    <img class="rounded-corners" style="max-width: 400px; border: 1px; margin-top: 24px;" src="{{ site.images2019 }}/04-08/subscription.png"/>
    <p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px; margin-top: 18px;"><strong>Let trouble come to you!</strong></p>
</div>

These two tools have made our team much more JIRA-effective. It won't make people fall in love with JIRA but you'd be surprised how much less people dislike something if it starts being useful and easy to use.

{{ site.managing_management }}
