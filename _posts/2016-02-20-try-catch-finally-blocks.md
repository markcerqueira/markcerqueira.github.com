---
layout: post
title: "try-catch-finally blocks"
description: ""
category: 
tags: [android, java]
---
{% include JB/setup %}

It's always pleasant to learn something new about a language you've been using for a while. Turns out when you declare a try block, **you don't need a catch block**. You ALWAYS need a catch OR a finally block, but the catch block is not required if you have a finally block. This is valid Java:

{% highlight java %}
public static void crashProneMethod() {
  try {
    String badString = null;
    badString.length();
  } finally {
    // Clean up if needed
  }
}
{% endhighlight %}

What is practical usage of this? If you wanted your method to catch an exception but let the method caller handle it, you could skip catching and re-throwing the exception in your method. That looks something like this:

{% highlight java %}
// Note that this method signature specifies that this method throws an Exception
public static void crashProneMethod() throws Exception {
  try {
    String badString = null;

	// This won't crash but the caller of crashProneMethod will
	// need to wrap the call to crashProneMethod in a try-catch 
	// (or try-finally) block. This lets you "catch" the exception 
	// and throw it to the caller without having to manually call throw. 
    badString.length();
  } finally {
    // Clean up if needed
  }
}
{% endhighlight %}

This is a decently cool trick, but like [variable shadowing in Java][1], it's probably better to explicitly catch the exception and throw it because it makes your code more readable. But if you're into exercising a language to make your code more difficult to read, try-finally away!

[1]: http://mark.gg/2015/04/26/thats-allowed-in-java/
