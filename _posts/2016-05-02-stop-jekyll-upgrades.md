---
layout: post
title: "Stop Jekyll Upgrades"
description: ""
category: 
tags: [meta, technical]
---
{% include JB/setup %}

I build my blog with [Jekyll][2] and I love it. But **I dread any time I accidentally update the Jekyll executable**. Everything breaks and it takes a lot of trial-and-error to get things working again. It doesn't help that I'm a noob at Ruby, RubyGems, and the internal workings of Jekyll in general. 

Today, I'm putting a stop to this madness and using the [Ruby bundler][1] for its designed purpose and am **version-locking the jekyll executable to version 2.4.0**:

{% highlight bash %}
# Lock Jekyll to version 2.4.0 in the Gemfile
echo "" >> Gemfile && echo "gem 'jekyll', '2.4.0'" >> Gemfile

# Reset all Gems
rm Gemfile.lock
sudo bundle clean --force
bundle install

# Run Jekyll, but use bundle exec to run the specific version
bundle exec jekyll serve --watch
{% endhighlight %}

Note that commands like jekyll and rake now need to be run with through **bundle exec**. If you just run jekyll directly, it'll run the most up-to-date one that is installed to your default path. 

This setup now lets me take control of when I'll have to suffer through a Jekyll upgrade.

**P.S. I still <3 you Jekyll!**

[1]: http://bundler.io/rationale.html
[2]: https://jekyllrb.com/