---
layout: post
title: "5 Ways to Static in Java"
description: ""
category: 
tags: [java, android]
---
{% include JB/setup %}

Someone asked me the other day if I knew about all the usages of static in Java. Turns out, I didn't know them all! Let's review them.

1\. **Static methods** - Methods of class can be static or non-static. Non-static methods are called instance methods because they can only be invoked on an instance of the particular class they belong to. Static methods can be called without any instance.

<!--break-->

2\. **Static variables** - Like static methods, static variables do not belong to instances of a class. If you have a static variable, its value is global and shared. Instance variables require an instance of the class; static variables do not. 

3\. **Nested static classes** - Sometimes you have a class that is only useful to one class so you nest it in another class. This nested class can be static or non-static. If the nested class is static, it cannot directly access instance variables of the outer class that contains it. If the nested class is non-static it is called an inner class. Instances of inner classes can only exist within instances of the outer class that contains them. 

4\. **Static initializers** - Static initializers are blocks of code that are executed (top-down) when the class is loaded. As the name implies, they can be used to initialize things in a static context. For example, if you have a JSON mapper class (as seen below) with a static ObjectMapper, you can configure it when the class is invoked, rather than having to call an initialization method. 

{% highlight java %}
public class JsonUtils {
    private static ObjectMapper sObjectMapper = new ObjectMapper();
    static {
        sObjectMapper.configure(JsonParser.Feature.ALLOW_SINGLE_QUOTES, true);
    }
}
{% endhighlight %}

5\. **Static imports** - A static import allows you to refer to fields and members of a class without actually specifying the class. For example, if you wanted to access the value of Pi in the Math class, you would normally do this: 

{% highlight java %}
import java.lang.Math;

double pi = Math.PI;
{% endhighlight %}

But if you don't want to specify that PI is in the Math class you can do a static import:

{% highlight java %}
import static java.lang.Math.PI

double pi = PI;
{% endhighlight %}

This is useful in certain cases, but if abused, can make code harder to read since magical constants of mysterious origin may be referenced without too much context.

**How did I do?** I knew the first three, and was prodded into the fourth one since I had used it a few times previously. I had absolutely no idea about static imports. Then again, my amazing development tool of choice, IntelliJ, handles importing any and every file I need. 
