---
layout: post
title: "Ant, dex, and jars all over"
description: ""
category: 
tags: [android]
---

We recently added [Android Annotations](http://androidannotations.org/) to the Sing Karaoke Android project. Using the annotations has been awesome so far, but it did present an interesting issue when it came to compiling and bundling the proper library in our Ant build script.

<!--break-->

Android Annotations provides two jar files: *androidannotations-X.Y.jar* used to generate code at compile time and *androidannotations-X.Y-api.jar* which contains only the code necessary during run time. So for our builds, in addition to the standard **libs** folder used for compilation/runtime, we would compile with a **libs-compiling** folder containing *androidannotations-X.Y.jar* and then link with a **libs-runtime** folder containing *androidannotations-X.Y-api.jar*. I deviated a bit from the [recommended setup](https://github.com/excilys/androidannotations/wiki/Building-Project-Ant) for where to put these libraries because I wanted the folders containing the libraries to all be treated the same during the Ant build process. The end goal here is:
* **libs** - used during compile time and runtime
* **libs-compiling** - used only during compile time
* **libs-runtime** - used only during runtime

During the compile step, in the javac task we can use the handy classpath attribute to add any extra libraries we need to make the compiler happy (**libs** and **libs-compiling**):

{% highlight xml+cheetah %}
<!-- include all libraries needed for compilation -->
<fileset dir="libs" includes="*.jar"/>
<fileset dir="libs-compiling" includes="*.jar"/>
{% endhighlight %}

With this, compilation will succeed. But afterwards, when everything is compiled into a Dalvik Executable (.dex) and packaged into a single .apk file, only the jars in the **libs** folder were getting pulled. So the app would load, but would crash as soon as it tries to use any of the methods in the missing jar libraries. This did not come as much of a shock; the classpath attribute's scope likely terminates as soon as javac is done. After beating my head against a wall trying to get dex to acknowledge my **libs-runtime** folder, I implemented this *solution*:
  
{% highlight bash %}
# run this command before we execute our Ant build
cp -R -v libs-compiling/ libs/
{% endhighlight %}

{% highlight xml+cheetah %}
<!-- TODO fix dex step so we can do this properly -->
<!-- include all libraries needed for compilation -->
<!-- <fileset dir="libs-compiling" includes="*.jar"/> -->

<fileset dir="libs" includes="*.jar"/>
{% endhighlight %}

This made me cringe a little inside, especially since we were using the bulkier compile version of Android Annotations and not the slimmer runtime version. Fortunately, I got around to taking care of this as well. At first, I searched the internet and could not find anything that would just let me specify some extra paths for dex. A few solutions had people running the dx command themselves, but after a few failed attempts at copy-and-paste-and-adapt, I started looking elsewhere. Eventually, I just started looking at the default Ant build.xml file that is distributed in the tools folder of the Android SDK. In there was this Ant macro:

{% highlight xml+cheetah %}
<!-- Configurable macro, which allows to pass as parameters output directory,
     output dex filename and external libraries to dex (optional) -->
<macrodef name="dex-helper">
{% endhighlight %}

The first hit when I googled "dex-helper" for some usage tips is a [bug report](https://code.google.com/p/android/issues/detail?id=13091) which was fortunately closed in January 2011, but did include an awesome example. So at the end of this adventure, I arrived at a painless solution to the issue of dex running when there are jar files in multiple directories:

{% highlight xml+cheetah %}
<target name="-post-compile">
  <echo message="Adding external libs to dex lib path via dex-helper"/>

  <dex-helper>
    <external-libs>
      <fileset dir="libs-runtime" includes="*.jar"/>
      <!-- no need to add "libs" as dex already adds it -->
    </external-libs>
  </dex-helper>
</target>
{% endhighlight %}

Now we compile with **libs**/**libs-compiling** and run with **libs**/**libs-runtime**!