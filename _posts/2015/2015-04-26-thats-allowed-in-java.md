---
layout: post
title: "That's Allowed in Java!?"
description: ""
category: 
tags: [java, android]
---

Sometimes you think you know a programming language really well. When I first looked at the Java code below, I thought there was **NO WAY** this code could compile.

{% highlight java %}
class WTFBBQSauce {
    public String myString = "ClassLevel";

    public void doWork() {
		 // myString above (class-level) is shadowed by this method-level declaration
         String myString = "MethodLevel";

         System.out.println(myString); // this will print "MethodLevel"
    }
}
{% endhighlight %}

I thought the declaration of myString in doWork would complain about a variable with the same name already being accessible. **But I was wrong**. It compiles and runs.

How? Why? This works because of [**variable shadowing**][1]. You have probably already seen variable shadowing in action in constructors and probably didn't bat an eyelid.

{% highlight java %}
class WTFBBQSauce {
    public int sauceSize; // size of WTFBBQSauce in ounces

    public WTFBBQSauce(int sauceSize)
		// we explicitly use this.sauceSize to refer to the instance variable sauceSize
		// above; if we just say sauceSize we are referring to the parameter passed in
		this.sauceSize = sauceSize;
    }
}
{% endhighlight %}

That said, I'm not going to run out and use this newfound knowledge. **Variable shadowing makes code confusing.** My inner compiler (the thing that told me this would never compile) will help me steer clear of using this language feature. But given how programmers sometimes like to ~~show off~~ discuss the finer points of languages, this knowledge isn't totally useless.

Kudos to [Abubakkar Rangara][2] for helping me get to the bottom of my Java knowledge gap!

[1]: http://www.xyzws.com/javafaq/what-is-variable-hiding-and-shadowing/15
[2]: http://stackoverflow.com/a/29887707/265791
