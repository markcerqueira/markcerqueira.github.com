---
layout: post
title: "Staying Dry with Android Layout Files"
description: ""
category: 
tags: [android]
---
{% include JB/setup %}

There are countless Android device types out there. The Android OS can load resources based on a device's screen size and pixel density. This is useful when you want different user experiences for larger tablets versus a smaller handset. The system works as intended, but what if you want the exact same layout with a few minor tweaks? Maybe you want a list item to be 40% taller on tablets, or maybe you want less padding around an image on smaller devices. Google provides thorough documentation on [supporting multiple screen sizes][1], but does not offer an elegant solution for tweaking layouts across device sizes. You could support multiple layout files for different classes of devices, but that's a pain to maintain given the minor differences across layout files. Fortunately, there is a way to stay DRY (don't repeat yourself) with your layout files!

<!--break-->

In this example, we have a basic list item that shows information for a song. It has an ImageView to show the album art and a TextView to display the song's title. Our layout file in the **res/layout** folder looks like this:

{% highlight xml %}
<com.company.ListItem
  android:layout_width="match_parent"
  android:layout_height="50dp"
  android:background="@color/list_item_background">

  <ImageView
    android:layout_width="wrap_content"
    android:layout_width="wrap_content"
    android:layout_gravity="center_vertical"
    android:src="@drawable/album_blank"/>

  <TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_gravity="center_vertical"
    android:layout_marginLeft="4dp"
    android:textColor="@color/song_title_text_color"
    android:textSize="14sp"
    android:text="@string/default_song_title"/>

</com.company.ListItem>
{% endhighlight %}

<hr class="separator"/>

<p style="margin-bottom: 8px;">Our trusty designer reviews the implementation on various devices and comes back with these requests:</p>
* Make the entire list item 20% taller on tablet devices.
* Add a larger margin to the left of the song title.
* Make the text size of the song title larger on tablets.

You could make a copy of the layout file and put it in the **res/layout-large/** folder, tweaking the values as requested. You may even need to do this for **res/layout-xlarge/** and **res/layout-small**. Copying, pasting, and tweaking are all easy, but any subsequent updates to the layout requires changing multiple layout files. If we added a TextView to our list item to show the name of the artist, we'd be copying and pasting that TextView into each instance of our list item layout file. In the end, repetition becomes frustrating, and maintenance becomes time-consuming.

You're already familiar with the key to avoiding this copy-and-paste madness: the **values** folder. You likely already use it if you define string and color constants. In the example above, we used the following values:

{% highlight xml %}
<resources>
  <!-- color values -->
  <color name="list_item_background">#ecebea</color>
  <color name="song_title_text_color">#222222</color>

  <!-- string values -->
  <string name="default_song_title">Song Title</string>
</resources>
{% endhighlight %}

It turns out, the configuration qualifiers you can append to **res/layout** and **res/drawable** to support multiple devices also works for the **values** folder! You can define **dimen** resource values that can store values with units like dp and sp. For example, in the layout file above, we could change the height of our list item from 50dp to **@dimen/list_item_height** and then we could define this **dimen** in the **values** and **values-large** folders. We repeat this for each of the requests made by our designer, and end up with two files (in **res/values** and **res/values-large**) that look like this:

{% highlight xml %}
<!-- res/values/list_item_values.xml -->
<dimen name="list_item_height">50dp</dimen>
<dimen name="list_item_song_title_left_margin">4dp</dimen>
<dimen name="list_item_song_title_text_size">14sp</dimen>
{% endhighlight %}

{% highlight xml %}
<!-- res/values-large/list_item_values.xml -->
<dimen name="list_item_height">60dp</dimen>
<dimen name="list_item_song_title_left_margin">8dp</dimen>
<dimen name="list_item_song_title_text_size">20sp</dimen>
{% endhighlight %}  

Now, we can have a single layout file. Android can load different layout files for different devices, and the values loaded also follow the same set of rules. You can even define a **string** to have different values, which may be useful for displaying longer strings on tablets. All those copies of your layout file can now be discarded and replaced with this single file:

{% highlight xml %}
<com.company.ListItem
  android:layout_width="match_parent"
  android:layout_height="@dimen/list_item_height"
  android:background="@color/list_item_background">

  <ImageView
    android:layout_width="wrap_content"
    android:layout_width="wrap_content"
    android:layout_gravity="center_vertical"
    android:src="@drawable/album_blank"/>

  <TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_gravity="center_vertical"
    android:layout_marginLeft="@dimen/list_item_song_title_left_margin"
    android:textColor="@color/song_title_text_color"
    android:textSize="@dimen/list_item_song_title_text_size"
    android:text="@string/default_song_title"/>

</com.company.ListItem>
{% endhighlight %}

<hr class="separator"/>

<p style="margin-bottom: 8px;">So now you can avoid repeating yourself, but you are adding a level of indirection. At Smule, we've avoided any indirection-induced pain by following these book-keeping practices:</p>
* Prefix the name of the value with the name of the layout file that's using it (e.g. song_list_item_, song_list_activity_).
* If you're sharing values across multiple layout files (e.g. the height of a navigation bar shown everywhere in the app), use some special prefix for those shared values (e.g. shared_).
* Keep device-dependent values in a separate XML file as opposed to just having a single file in the values folder. Things like strings and colors will unlikely vary across different devices, so keep those in a separate file.

I hope this helps anyone who's looking to maintain their Android layout files more easily. Huge kudos to Stack Overflow user, kennethc, who discovered this functionality and [posted about it][2]. If there is any additional magic to managing multiple layout files, please feel free to [send me a tweet](https://twitter.com/markmcerqueira) and I'll update this post! 

[1]: https://developer.android.com/guide/practices/screens_support.html
[2]: http://stackoverflow.com/questions/12616321/android-how-do-you-manage-multiple-layout-files-in-line-with-dry-principle