---
layout: post
title: "Android SDK Trickery"
description: ""
category: 
tags: [android, rant]
---
{% include JB/setup %}

Sometimes you need to write cringe-inducing code. The other day, I was trying to figure out when the Android keyboard was present and not present. Unlike iOS, Android doesn't provide convenient ways to detect when the keyboard appears and disappears. I found a "solution" that keeps track of the size of the root view of the activity; if its display frame is smaller than the actual height of the view, a keyboard is likely present. To detect this I added a global layout listener to my root view's view tree. When I went to remove it, I ended up having to write this:

{% highlight java %}
@SuppressWarnings("deprecation") // no words for this sadness...
private void stopListeningForKeyboardDismissal() {
    if (Build.VERSION.SDK_INT > Build.VERSION_CODES.ICE_CREAM_SANDWICH_MR1) {
        mRootView.getViewTreeObserver().removeOnGlobalLayoutListener(mKeyboardPresentListener);
    } else {
        mRootView.getViewTreeObserver().removeGlobalOnLayoutListener(mKeyboardPresentListener);
    }
}
{% endhighlight %}

The method remove**GlobalOn**LayoutListener was introduced in API level 1, but it did not follow the naming conventions in the ViewTreeObserver class. So it was deprecated and replaced by remove**OnGlobal**LayoutListener in API level 16. What would happen if you didn't call these properly? Just a NoSuchMethodError exception that would cause much sadness. Good troll, Google. Good troll. 

<div>
	<img class="rounded-corners" style="max-width: 500px; border: 0px; margin-bottom: 10px;" src="/assets/images/posts/2013-12-24/androge.png"/>
	<p class="caption-text" style="line-height: 1.5em; font-size: 1em;"><b>The Androge</b></p>
</div>