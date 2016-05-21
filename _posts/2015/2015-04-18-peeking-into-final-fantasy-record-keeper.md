---
layout: post
title: "Peeking Into Final Fantasy Record Keeper"
description: ""
category: 
tags: [video games, final fantasy, technical]
---
{% include JB/setup %}

<div class="float-image-right">	
  	<img style="border: 0px;" src="/assets/images/posts/2015-04-18/ffrk.png" alt="Final Fantasy Record Keeper"/> 
  	<p>I've been playing a lot of <strong><a href="http://www.finalfantasyrecordkeeper.com/">Final Fantasy Record Keeper</a> (FFRK)</strong>. It's a free-to-play game available on iOS and Android. It's pretty fun! You get characters from different entries in the series, battle in different settings, get equipment, craft abilities, get experience points, get annoyed by a Moogle, get to listen to awesome music, unleash powerful limit breaks, and the rest of the whole JRPG shebang. In short, I'm hooked.</p>
</div>

Today, I **hooked up FFRK to [Charles Proxy][1]**. Charles is a nifty tool that can show you network traffic (via API calls) leaving and coming back to your phone. Let's take a look at one API call: *get_battle_init_data*. This API is called at the beginning of a battle. A battle in FFRK consists of multiple rounds of enemies that you must fight in succession. This one API provides data for all rounds of a single battle.

In the JSON response to this API, there is an array "rounds" that has metadata for each of the rounds of enemies you'll face off against. Inside that array, is "drop_item_list" which describes an item that will be dropped when you complete the round. Also, you'll find an array keyed by "enemy" which has metadata for each enemy. Nested a bit inside each enemy object, you'll find a "drop_item_list" for that enemy which describes what item the enemy drops. 

<div>
	<img class="rounded-corners" style="max-width: 600px; margin-top: 10px; border: 0px;" src="/assets/images/posts/2015-04-18/items.png"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 24px;"><strong>Item dropped after a round ends (red) and item dropped when an enemy is destroyed (green).<br>The items, respectively, are a Blue Potion and a Minor Fire Orb.</strong></p>
</div>

What's the difference between drop_item_list nested under "round" and drop_item_list under "enemy?" Turns out some items are dropped after completing a round and not by a particular enemy. For example, potions (nested under "round") were only dropped after all enemies were destroyed. You've probably noticed you never get a potion halfway through a round and this is why. 

I ran the Ship Graveyard (FFV) a few times because **figuring out how to get the Black Cowl reliably** is a great proof of concept.

<!--break-->

<div>
	<img class="rounded-corners" style="max-width: 340px; margin-top: 10px; border: 0px;" src="/assets/images/posts/2015-04-18/siren.png"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 24px;"><strong>I can has Black Cowl?</strong></p>
</div>

During my first pass, I just looked at the response data and drop_item_list and mapped what I was seeing returned in the API to what I was getting in the game. Each drop_item_list has an integer keyed by "type" and after some data collection, the mappings so far look like: gold (11), potion (21), ability potion (31), weapon/armor (41), orb (51). I also mapped a few items specifically:

<div style="width: 50%; margin: 0 auto;">
<table style="margin-bottom: 1em;">
	<tr><th>item_id</th><th>type</th><th>rarity</th><th>Item Name</th></tr>
	<tr><td>40000007</td><td>51</td><td>1</td><td>Lesser White Orb</td></tr>
	<tr><td>21009001</td><td>41</td><td>1</td><td>Cherry Staff (XII)</td></tr>
	<tr><td>21010002</td><td>41</td><td>1</td><td>Shortbow (XII)</td></tr>
	<tr><td>40000031</td><td>51</td><td>1</td><td>Minor Fire Orb</td></tr>
	<tr><td>22053001</td><td>41</td><td>1</td><td>Copper Cuirass (V)</td></tr>
	<tr><td>22054002</td><td>41</td><td>1</td><td>Leather Armor (III)</td></tr>
</table>
</div>

So, if we had a more complete mapping of item_ids **we could know as soon as a battle starts exactly what items will be dropped**! Turns out, it isn't very difficult to map items to item_ids. Just hop over to the Party tab and you'll get item_ids and you'll see a request made to party/list which returns -- among many other things -- arrays for "materials" and "equipments" that you possess. item_id in the get_battle_init_data matches to equipment_id in the party/list API. I verified this by checking that the Cherry Staff (XII) equipment_id matched what I found while manually collecting item_ids. By the way, **the Black Cowl item id is 22051015**!

<div>
	<img class="rounded-corners" style="max-width: 600px; margin-top: 10px; border: 0px;" src="/assets/images/posts/2015-04-18/cherrystaff.png"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 24px;"><strong>item_id = equipment_id</strong></p>
</div>

**Can we exploit this?** Let's see! If you start a battle, pause immediately, look at the items that will drop, and then force restart the app, you'll make another request to *get_battle_init_data*, but the drops do not change.

But there are ways to re-roll drops as highlighted [here][3]. The general gist of the strategy is to force quit the app if you don't get the drop you want and when you restart the app you decline to restart the battle. This throws you completely out of the battle flow. When you reenter you make a fresh call to *get_battle_init_data* that will get you new drops. This costs stamina -- an energy unit required for battling that slowly restores over time -- so **re-rolling drops has a cost**. What does this look like at the API level?

<div>
	<img class="rounded-corners" style="max-width: 700px; margin-top: 10px; border: 0px;" src="/assets/images/posts/2015-04-18/reset.png"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 24px;"><strong>Drops don't change unless you cross a red arrow!</strong></p>
</div>

When you start a battle, a series of API calls are made. *begin_session* and *begin_battle* return a session key and then *get_battle_init_data* is called. If you do the re-roll trick mentioned above, a call is made to *quit*. The middle block (green) of API calls that features two calls to *get_battle_init_data* is me starting the battle and force quitting it. Note that in this scenario, drops DO NOT change. To get drops to change, *quit* (highlighted by the red arrows) must be called, or *win* which is called when you complete a battle. Then *begin_session* and *begin_battle* (which consumes stamina) are called again and this re-rolls drops. In short, if you don't call *quit* (or *win* by completing the battle), drops won't change. 

Can we re-roll our drop list without costing us any stamina? Unlikely given the API design. Charles allows you to set [breakpoints][2] on API calls. If we breakpoint on the *get_battle_init_data* response, we can check it for the item_ids we want. If they are present, we can allow the response through and everything proceeds as normal. If the item_ids don't have what we care about, we abort the request. I did this six times (hit the breakpoint, copied the response, aborted the request) and then compared the all responses to *get_battle_init_data*. They were all exactly the same.

{% highlight bash %}
~/md5 r*.txt
MD5 (r1.txt) = 3467b0c7a40ebc3f72fa7b9165dc8220
MD5 (r2.txt) = 3467b0c7a40ebc3f72fa7b9165dc8220
MD5 (r3.txt) = 3467b0c7a40ebc3f72fa7b9165dc8220
MD5 (r4.txt) = 3467b0c7a40ebc3f72fa7b9165dc8220
MD5 (r5.txt) = 3467b0c7a40ebc3f72fa7b9165dc8220
MD5 (r6.txt) = 3467b0c7a40ebc3f72fa7b9165dc8220
{% endhighlight %}

If I had to guess *begin_battle* creates a battle session on the FFRK servers. Until *quit* or *win* is called, repeated calls to *get_battle_init_data* will return the same response. When you force quit the app and return and the app asks if you'd like to resume your interrupted battle, it's likely noticing that you have an open battle session on the servers (opened by *begin_battle*) that is not closed yet (by *win* or *quit*).

So is this all for naught? Not necessarily. Unfortunately, we can't re-roll drops for free, but we can save ourselves some time and take some of the guesswork out of farming for a particular drop. For example, to farm the Black Cowl using this system:

* Hook up your device to Charles Proxy.
* Start the battle and pause as soon as the battle starts.
* Look the response to *get_battle_init_data.* Look at the drop_item_list for the enemy in the 4th round (index 3). That enemy is Siren -- the boss.
* If the item_id is 22051015, congrats! You're going to get a Black Cowl when you beat the boss.
* If the item_id is not 22051015, flee the battle; this calls the *flee* API which is similar in functionality to the *quit* API. Start the battle again and repeat the steps above until you get the Black Cowl item id in the API response.

This new method is more time-efficient and takes the guesswork out of farming drops, but it won't prevent stamina drain. Oh wells!

Source code and sample JSON data available at [ff-record-keeper on GitHub][4]!

[1]: http://www.charlesproxy.com
[2]: http://www.charlesproxy.com/documentation/proxying/breakpoints/
[3]: http://www.justpushstart.com/2015/04/final-fantasy-record-keeper-how-to-reroll-drops/
[4]: https://github.com/markcerqueira/ff-record-keeper