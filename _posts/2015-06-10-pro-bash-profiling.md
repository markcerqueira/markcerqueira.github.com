---
layout: post
title: "Pro Bash Profiling"
description: ""
category: 
tags: [technical]
---
{% include JB/setup %}

My Bash profile is critical to keeping me **elite** on the command-line. Keeping myself elite across multiple computers is also very easy with Dropbox (or your file syncing service du jour). Then I create a very, very simple .bash_profile that looks like this:

{% highlight bash %}
~ cat .bash_profile

source ~/Dropbox/Bash/main.sh
{% endhighlight %}

This grabs the contents of main.sh from a folder in my Dropbox and effectively puts it in the .bash_profile file. What does main.sh look like?

{% highlight bash %}
~ cat ~/Dropbox/Bash/main.sh 

# Git Power Up!
source ~/Dropbox/Bash/git-completion.sh

# Android
source ~/Dropbox/Bash/android.sh

# Evernote
source ~/Dropbox/Bash/evernote.sh

# The rest including everything and the kitchen sink...
{% endhighlight %}

I separate things out a little more to keep things modular and keep similar functionality together, which makes everything a little easier to both maintain and read. 

I don't update these files very often, but anytime I do, it'll get synced automagically. The sad days of typing a new alias on a computer and seeing "command not found" are gone!

Came here looking for awesome Bash profile aliases? Check out [Nate Landau's extremely OP Bash profile][1] for some excellent Bash profiling!

Happy Bash profiling!

[1]: http://natelandau.com/my-mac-osx-bash_profile/


