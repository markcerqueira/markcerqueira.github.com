---
layout: post
title: "Dropbox and iTunes"
description: ""
category: 
tags: [technical]
---
{% include JB/setup %}

**tl;dr** - If you keep your iTunes library in Dropbox, it's all sunshine and rainbows until you realize Dropbox is syncing iTunes Library.itl and iTunes Library.xml after EVERY song play or skip. 

Putting your iTunes library in Dropbox sounds like a great idea. And for the most part it is. You get your iTunes library on every computer you sync with Dropbox. You add music on one computer, and you get it on the others. Generally, it's convenient and easy. 

The trouble starts when we look at the files that manage our library: **iTunes Library.itl** and **iTunes Library.xml**. Every time a song is touched (played or even skipped), these two files are updated. Every time the files are updated, they are synced to Dropbox. 

<div>
	<img class="rounded-corners" style="max-width: 700px; border: 1px solid #000000;" src="/assets/images/posts/2014-12-22/db_sync.png"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 24px;"><strong></strong></p>
</div>

My iTunes Library (~18,000 songs) itl and xml files are **5.1 MB** and **28.3 MB** respectively. Let's say the average song is 4 minutes long. If you are listening to my iTunes library for an hour (15 songs), that's **500 MB worth of file changes that are synced to Dropbox in one hour**! We're easily talking **gigabytes of bandwidth consumed daily** if you listen for more than a couple of hours. It's pretty ridiculous.

It's not a huge deal yet. But still, with bandwidth caps looming in the future, it's something worth thinking about. So, can we make iTunes in Dropbox less bandwidth hungry?

<!--break-->

* I could clean up my library and make it smaller. My library is huge and I'm usually only listening to a very small subset of it. That said, it's nice to have access to my entire library at all times. Especially when I get a hankering for some old jams I haven't listened to in a while. However, this solution is too easy and we'd learn little if we stopped here, so let's ignore it. 

* GTFO XML! iTunes only uses the iTunes Library.itl file to organize your entire library. As Apple documents in [this support article][1], the iTunes Library.xml file makes "your music and playlists available to other applications on your computer" like iPhoto and iMovie. That's stuff I don't need. I deleted my iTunes Library.xml file hoping iTunes would happily chug along without it. iTunes loaded fine as expected, but it then quickly recreated the XML file in all it's 28.3 MB glory. 

* If I can't make iTunes Library.xml go away, I should be able to tell Dropbox to ignore that file and not sync it right? Wrong! Dropbox's Selective Sync settings only allow you to ignore folders; there is currently no support for ignoring files. The first link that comes up when I Google "Dropbox ignore file" looks like a feature request posted on Dropbox's forums that unfortunately 404s. So I made a [new post requesting the feature][2]. For now, you can "hack" file ignore with the steps from this [Super User answer][3]. 

<div>
	<img class="rounded-corners" style="max-width: 700px; border: 1px solid #000000;" src="/assets/images/posts/2014-12-22/improvement.png"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 24px;"><strong>Getting better...</strong></p>
</div>

**Now that the XML file is no longer synced, syncs are 85% leaner!** But we could do better... if we worked at Apple and could make important engineering decisions. We know a few things:

* The itl file that manages our library's metadata seems to be purposefully obfuscated.
* The new iTunes 12 icon is absolutely hideous.
* The itl file (5.1 MB) has enough information in it to re-generate the XML file (28.3 MB).
* XML is too too verbose. The itl file likely contains some other information given my XML file can be compressed from 28.3 MB to 1.7 MB using the built-in archiver in OS X. That leaves 3.4 MB (5.1 MB - 1.7 MB) of mystery in that file!

So let's use an entry in our iTunes Library.xml file to get an idea of what an entry in the itl file would look like. Here's a song entry:

{% highlight xml+cheetah %}
<key>Track ID</key><integer>21743</integer>
<key>Name</key><string>Dead Sea (Tower of Geddon)</string>
<key>Artist</key><string>Chrono Cross</string>
<key>Album Artist</key><string>Yasunori Mitsuda</string>
<key>Composer</key><string>Yasunori Mitsuda</string>
<key>Album</key><string>Chrono Cross OST</string>
<key>Genre</key><string>Game</string>
<key>Kind</key><string>MPEG audio file</string>
<key>Size</key><integer>7803584</integer>
<key>Total Time</key><integer>190406</integer>
<key>Disc Number</key><integer>2</integer>
<key>Disc Count</key><integer>3</integer>
<key>Track Number</key><integer>15</integer>
<key>Track Count</key><integer>26</integer>
<key>Year</key><integer>1999</integer>
<key>Date Modified</key><date>2011-02-09T04:15:40Z</date>
<key>Date Added</key><date>2011-02-09T04:12:57Z</date>
<key>Bit Rate</key><integer>320</integer>
<key>Sample Rate</key><integer>44100</integer>
<key>Play Count</key><integer>83</integer>
<key>Play Date</key><integer>3502032647</integer>
<key>Play Date UTC</key><date>2014-12-21T23:50:47Z</date>
<key>Skip Count</key><integer>9</integer>
<key>Skip Date</key><date>2013-11-14T02:08:13Z</date>
<key>Rating</key><integer>100</integer>
<key>Album Rating</key><integer>100</integer>
<key>Album Rating Computed</key><true/>
<key>Artwork Count</key><integer>1</integer>
<key>Persistent ID</key><string>8633DA1C1A82A603</string>
<key>Track Type</key><string>File</string>
<key>Location</key><string><!---->.mp3</string>
<key>File Folder Count</key><integer>5</integer>
<key>Library Folder Count</key><integer>1</integer>
{% endhighlight %}

Most of this data doesn't need to be updated frequently. In fact, only 5 of the 31 values above (Play Count, Play Date, Play Date UTC, Skip Count, Skip Date) would trigger the file changes after playing or skipping a song.

iTunes could break these "volatile" fields into a separate file and use the track ID if it ever needed to match data between the two files. This iTunes Volatile Library.itl file would sync at the current frequency during playback (but it would be smaller in size), while the file containing the other metadata would change and sync less frequently. If keeping this data 100% accurate across your computers isn't very important, you could even ignore this file using the Dropbox ignore-file-hack.

<div>
	<img style="max-width: 400px; border: 0px solid #000000;" src="/assets/images/posts/2014-12-22/db_fresh.png"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 24px;"><strong>Dr. Dre - can you makes iTunes the leanest and illest it can be?</strong></p>
</div>

There are other solutions like storing volatile data in iCloud and tying that to your Apple account. Also, if the XML file was still used to manage your library (instead of the obfuscated binary itl file format), you could even store your iTunes Library in git and push and pull changes to the XML file across different computers. How wonderful it would be to resolve a merge conflict in iTunes Library.xml? Dear God -- did I play that song 4 times or 6 times!? 

[1]: http://support.apple.com/en-us/HT201610
[2]: https://www.dropboxforum.com/hc/communities/public/questions/201339089-Selective-sync-should-allow-us-to-ignore-specific-files-within-a-folder
[3]: http://superuser.com/a/757498
