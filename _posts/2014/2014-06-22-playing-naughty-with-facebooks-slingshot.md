---
layout: post
title: "Playing Naughty with Facebook's Slingshot"
description: ""
category: 
tags: [technical]
---

The new Facebook Slingshot app is like SnapChat with a twist: you can only see a photo or video someone has sent if you if send them something back first. It's pretty cool. I'm not here to wax poetic about the potential merits of the "send me content back or you can't see what I sent you" mechanic, but I do get slightly irked when I take all of **5 seconds** to craft a crappy SnapChat only to NEVER hear back from the poor sap who wasted 10 seconds looking at it. 

My biggest question about Slingshot is: can we just bypass this whole locked content stuff?

<div>
	<img class="rounded-corners" style="max-width: 400px; border: 1px solid #000000;" src="/assets/images/posts/2014-06-22/locked.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 20px;"><strong></strong></p>
</div>

Turns out you can. Just configure your device to use an SSL proxy like [Charles Proxy](http://www.charlesproxy.com/) and check out the calls made to **https://api.parse.com/update** and **https://api.parse.com/client_function**. Look in the JSON array keyed by "lockedShotUsers" and you should see something like this. Note: the JSON body was trimmed to just show the essentials.

{% highlight java %}
"lockedShotUsers": [{
    "name": "Tom",
    "username": "alltom",
    "shots": [
      {
        "mediaType": "video",
        "media": {
            "__type": "File",
            "name": "92aeee69-f7e9-42de-b72c-4ead1a3a9ee7-video.mp4",
            "url": "https://s3.amazonaws.com/files.sling.me/bf152dba-764e-400e-b773-2e2a2111823f/92aeee69-f7e9-42de-b72c-4ead1a3a9ee7-video.mp4"
        },
        "mediaSize": 385633,
        "thumbnail": {
            "__type": "Bytes",
            "base64": "OMITTED - base64 encoding of the blurred thumbnail"
        },
      }
    ]
}]
{% endhighlight %}

Yes, that is a video taken by my mentor and hero, Tom Lieber a.k.a. [alltom.com](http://www.alltom.com), playing Super Smash Bros. Yes, I didn't reply to him. Yes, he called me a cheater and made me feel a little bad about this breach of Slingshot etiquette.

Does this matter? Not really. You could make it so the content URL isn't sent down until you send content to someone else, but you don't get a lot by cheating here. You'll see what your friend sent you and have a little evil laugh. The main operating principle for the system still holds -- if you want more content, you're gonna have to make and share content. But if a friend says send me a picture of your credit card and I promise to send a picture of mine to unlock yours, you may want to ignore them.
