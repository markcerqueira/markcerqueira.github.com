---
layout: post
title: "Managing Management - Effective JIRA"
description: ""
category: 
tags: [managing management, engineering management, jira, automation]
---

Whether you love (few people) or hate (more people) JIRA, effectively using it can minimize the time you spend on it and maximize the value you get out of it. Ineffective JIRA looks like:

* Browsing for issues from the Projects view - Good luck finding what you're looking for!
* Creating, curating, sharing a list of custom Filters - Good luck navigating between filters and getting people to start leveraging a new filter!
* Creating a custom Dashboards - Good luck introducing any change when everyone has their own dashboard!
* Manually reviewing things to keep issues in order - Good luck remembering to do this consistently and not lose your mind!

Effective JIRA gives you everything you and your team needs in one place. When issues are in a bad state, you don't have to remember to clean them up, you get notified and in some cases they clean themselves up! How do you get here? **Rich Filters**, **Subscriptions to Filters**, and **JIRA Automation**.

**Rich Filters** let you define a base filter (e.g. project = Android) and then add a variety of Static Filters (i.e. fixed JQL), Dynamic Filters (e.g. dynamic fields like Assignee), Smart Filters (e.g. converting Last Updated to distinct values using JQL). Creating a dashboard based on a Rich Filter allows you to present all these filters as buttons and dropdowns. My team has moved from using personal, custom dashboards to using a single Rich Filter powered dashboard. When we talk about anything in JIRA now, it's all in one place and we're all speaking the same language.

<div>
    <img class="rounded-corners" style="max-width: 800px; border: 1px; margin-top: 24px;" src="{{ site.images2019 }}/04-08/rich.png"/>
    <p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px; margin-top: 18px;"><strong>Buttons along the top filter everything else on the screen.</strong></p>
</div>

**Subscriptions to Filters** leverages individual filters but don't worry - you won't be visting the filter much because the filter is only used to find issues and email you if any are found. For example, if an issue is marked as closed but doesn't have a Fix Version, someone looking at it won't immediately know what version of the app has the fix. To stay ahead of these situations, create filters for issues that aren't compliant and then add a subscription that notifies you via email. You'll get pinged closer to the time the issues fall into a bad state which makes cleaning them up much easier.

<div>
    <img class="rounded-corners" style="max-width: 400px; border: 1px; margin-top: 24px;" src="{{ site.images2019 }}/04-08/subscription.png"/>
    <p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px; margin-top: 18px;"><strong>Let trouble come to you!</strong></p>
</div>

**JIRA Automation** lets you take the above filters and either fixes them automatically or notifies the assignee to update the correct fields. For example, my team uses a  label that we put on all the JIRAs we own and I add myself as a watcher on all these to get notified when changes are made to to the tickets. But sometimes I'm not a watcher. Fortunately it's easy to set up a JIRA Automation to automatically add yourself as a watcher to tickets that match JQL: `labels in (_midnight-commander-x) AND watcher not in (markcerq)`. In cases that can't be fixed automatically you can lean on others to help; if a ticket is marked as done but it's in the Backlog you can have JIRA Automation post a comment asking the assignee to update the Fix Version to reflect the version the change is shipping in. JIRA Automation has a ton of info and use cases on their [website][1].

<div>
    <img class="rounded-corners" style="max-width: 800px; border: 1px; margin-top: 24px;" src="{{ site.images2019 }}/04-08/automation.png"/>
    <p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px; margin-top: 18px;"><strong>The power of #automation!</strong></p>
</div>

These three tools have made our team much more JIRA-effective. It won't make people fall in love with JIRA but you'd be surprised how much less people dislike something if it starts being useful and easy to use.

{{ site.managing_management }}

[1]: https://blog.codebarrel.io/
