---
layout: post
title: "Base64 Into SharedPreferences"
description: ""
category: 
tags: [android, java]
---

Want to push and pull some **Base64** from **SharedPreferences**? You'll need to do some String to byte[] conversion to get it done. First, I (foolishly) tried using toString() on a byte[] but that won't work! The String constructor saves the day!

{% highlight java %}
// Encoding
String encodedString = new String(Base64.encode(string.getBytes(), Base64.DEFAULT), Charset.defaultCharset());

// Decoding - Base64.decode() this can throw an IllegalArgumentException so best to try-catch!
String decodedString = new String(Base64.decode(string.getBytes(), Base64.DEFAULT), Charset.defaultCharset());
{% endhighlight %}

