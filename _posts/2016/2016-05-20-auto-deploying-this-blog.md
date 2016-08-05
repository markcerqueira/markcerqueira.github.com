---
layout: post
title: "Auto-Deploying This Blog"
description: ""
category: 
tags: [meta, technical, automation, ci]
---

A long time ago I started **generating my site locally and pushing it up to Github manually** because Github Pages does not allow you to run custom plugins. This isn't as painful as it sounds. A friendly internet hero -- ixti -- crafted a nice Rakefile that [automated publishing][1].

**But doing the publishing myself led to some workflow issues.** Allowing GitHub Pages to do the work for you is nice because you only have to deal with one branch. Make changes to that branch, push to GitHub, and GitHub Pages would generate the site and deploy it. Everything is always in sync. The new workflow had me writing and crafting content on the source branch and then using the publishing command to generate my site locally and then it would push it to the master branch: the "deploy." **Separating the crafting and deploying steps meant I sometimes published content without pushing it into the source branch or I'd push content and not deploy it.**

<div>
	<img class="rounded-corners" style="max-width: 800px; border: 1px solid #cdcdcd;" src="/assets/images/posts/2016-05-20/travis.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px;"><strong>Continuous deployment via Travis</strong></p>
</div>

In keeping with [2016's automation resolution][1], I set up my blog to auto-deploy itself. Using and adapting Domenic Denicola's [clear and helpful instructions][3], the new set-up has [Travis][4] run the automated publishing flow when any changes are pushed to the source branch. Turns out Travis is not only a great continuous integration tool, but can be adapted to be continuously deploying as well! No more pushing content to the source branch and running the publishing command locally; **I'm back to just needing to push once**.

{% highlight bash %}
# The blog's gotten big so rake publish pushes 75.05 MiB!
Writing objects: 100% (1052/1052), 75.05 MiB | 1.46 MiB/s, done.
Total 1052 (delta 166), reused 0 (delta 0)
To git@github.com:markcerqueira/markcerqueira.github.com.git
 + f2e99be...3aea10b master -> master (forced update)
{% endhighlight %}

And there are a few more benefits including **email notifications if something goes wrong** during the publishing flow and **no need to wait on a 70+ MB push** when publishing, which is great when I'm tethered or in a rush.

This minor improvement isn't mind-blowing, but it does make my interaction with blogging more streamlined and simple. That's what my automating 2016 resolution is all about. Onwards!

{% highlight bash %}
git push origin source
# We're done. Walk away. Go outside. Eat a banana.
{% endhighlight %}

[1]: http://ixti.net/software/2013/01/28/using-jekyll-plugins-on-github-pages.html
[2]: /2016/01/01/automating-2016/
[3]: https://gist.github.com/domenic/ec8b0fc8ab45f39403dd
[4]: https://travis-ci.org/markcerqueira/markcerqueira.github.com