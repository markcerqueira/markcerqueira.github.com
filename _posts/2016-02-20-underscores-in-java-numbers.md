---
layout: post
title: "Underscores in Java Numbers"
description: ""
category: 
tags: [android, java]
---
{% include JB/setup %}

Following [variable shadowing][1] and [catch-less try blocks][2], today we explore another cool little Java thing I learned about the other day: underscores in Java numeric literals.

{% highlight java %}
// Declaring a few "numbers" with underscores to make them more readable
int oneMillion = 1_000_000;
long creditCardNumber = 1111_2222_3333_4444L;
long socialSecurityNumber = 111_222_3333L;
{% endhighlight %}

Unlike variable shadowing and catch-less try blocks, **underscores in numeric literals makes things clearer and more readable** so I encourage using them! 

Read more about this handy little language feature and see more examples in the [official Java documentation][3].

[1]: /2015/04/26/thats-allowed-in-java/
[2]: /2016/02/12/try-catch-finally-blocks/
[3]: https://docs.oracle.com/javase/8/docs/technotes/guides/language/underscores-literals.html
