---
layout: post
title: "Ruby DateTime to Objective-C NSDate"
description: ""
category: 
tags: [technical, objective-c, ios]
---
{% include JB/setup %}

Converting a Ruby DateTime to an Objective-C NSDate will lead you on a wonderful journey where you realize the DateTime outputs itself is incompatible with any potential NSDateFormatter you try to use to parse it. The crux of this is because [DateTime includes a colon in its timezone offset][1] which you cannot express in a NSDateFormatter.

So what is one to do? One option is to skip the default formatter of DateTime and roll your own:

{% highlight ruby %}
# See http://stackoverflow.com/a/9132422/265791
my_datetime.strftime('%Y-%m-%d %H:%M:%S')
{% endhighlight %}

Then build the corresponding formatter in Objective-C:

{% highlight objective-c %}
[dateFormatter setDateFormat:@"yyyy-MM-dd HH:mm:ss"];
{% endhighlight %}

With this, you too can avoid the fruitless journey of trying to get NSDateFormatter to comprehend DateTime's default format. Happy interoperating with languages!

[1]: http://stackoverflow.com/a/7115343/265791
