---
layout: post
title: "GTFO GoToMeeting!"
description: ""
category: 
tags: [rant, technical]
---
{% include JB/setup %}

A few days ago, I dragged three different versions of GoToMeeting from my Applications folder to the trash. A few days later, I found myself deleting the same three copies of GoToMeeting  **again**. How did GoToMeeting reinstall itself? A few tweets to the helpful person behind @GoToMeeting confirmed my worst fears...

<div>
	<img class="rounded-corners" style="max-width: 600px; border: 0px;" src="/assets/images/posts/2014-09-10/reinstall.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 30px;"><strong></strong></p>
</div>

GoToMeeting runs a background agent that exists outside the app bundle and automatically updates itself. Turns out, it will also reinstall the app and it will even install three different versions of itself! **How annoyingly convenient!**

GoToMeeting's instructions for disabling automatic updates involve waiting for GoToMeeting to reinstall itself and then disabling automatic updates from within the app. **I REFUSE!!!** I'm getting rid of this nuisance now.

Fortunately, cleaning up GoToMeeting permanently isn't too difficult. It just requires killing a launch agent configuration file, but if you want to be thorough you can wipe the entire folder that contains the background updater. To the command-line!

{% highlight bash %}
# if you like playing it safe, replace -f (force delete) with -i (interactive delete)

# delete the launch agent configuration file
rm -fv ~/Library/LaunchAgents/com.citrixonline.GoToMeeting.G2MUpdate.plist

# delete the folder that contains the background updater
rm -rfv ~/Library/Application\ Support/CitrixOnline/
{% endhighlight %}

Good riddance, GoToMeeting!