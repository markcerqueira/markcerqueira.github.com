---
layout: post
title: "Changing Progress Bar Spinner Color"
description: ""
category: 
tags: [android]
---

Situation: you've got a little progress spinner in your Android app. 

``` xml
<ProgressBar
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:indeterminateOnly="true"/>
```

But it's grey. You want it to be a different color. Something more exciting. To the Googles!

Like many Android things, there are multiple Stack Overflow posts with all sorts of answers and comments on each one saying "Thanks" and "That doesn't work for me." I cut through all that and here is how you do it programmatically and it works across all API levels:

``` java
// Source: http://stackoverflow.com/a/36828947
try {
  int color = ContextCompat.getColor(this, R.color.favorite_color);
  myProgressBar.getIndeterminateDrawable().setColorFilter(color, PorterDuff.Mode.SRC_IN);
} catch (Exception e) {
  // Why try-catch? Because some Xiaomi device out there will probably choke...
}
```

Now your `ProgressBar` -- that's actually a spinner and not a bar -- be colored!