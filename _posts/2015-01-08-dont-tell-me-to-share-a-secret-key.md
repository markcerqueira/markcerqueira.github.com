---
layout: post
title: "Don't Tell Me to Share a Secret"
description: ""
category: 
tags: [rant, technical]
---
{% include JB/setup %}

My friend Spencer asked me if I could beta test Mini Audicle for iOS. I agreed and asked him if he had any performance monitoring tools set up. Long story short, I ended up integrating **Crittercism** (my favorite crash monitoring tool) into Mini Audicle iOS so he could collect crash data from every user. 

One important part of the Crittercism integration process is **uploading dSYMs - debug symbol files**. For release builds, debug symbols are removed to reduce the binary size but this makes crash logs much less useful. Fortunately, dSYM files help us decode (symbolicate) these crash reports. It's super important to upload dSYMs if you want to make any sense of stack traces.

Fortunately, Crittercism [provides thorough instructions][1] on setting up automatic dSYM upload, but it's not all sunshine and rainbows.

<!--break-->

The instructions help you set up a script that runs after the build phase is complete. 

<div>
	<img style="max-width: 400px; border: 0px solid #000000;" src="/assets/images/posts/2015-01-08/not_the_key.png"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 24px;"><strong>Something is fishy here...</strong></p>
</div>

What's wrong with this? **The API key is right there, in plain sight!** As soon as you push this up, your key is available for all to see! While it seems you currently can't do much damage with the [Crittercism REST API][2], you probably shouldn't instruct customers to just put their API key out there for everyone to see. You should AT LEAST warn them about the potential dangers of sharing this key.

**Benefit of the doubt time!** I can imagine Crittercism is mostly integrated into enterprise applications that are hosted **privately**. But even in that case, ideally, only your build server, which makes builds for non-developers, would have access to the API key. To that end, Crittercism provides a [Jenkins plugin][3] eliminating the need to put the API key directly in your source code. 

But if you're a public open source project, do not have a build server, and want to have auto-uploading dSYMs to Crittercism what options do you have? You can still use their method safely by modifying Crittercism's provided instructions a bit. Here is what Mini Audicle iOS uses: 

{% highlight bash %}
# only upload during Release builds, otherwise every build will upload a dSYM
if [ "${CONFIGURATION}" = "Release" ]; then
    # put the secret key in this file as an environmental variable
    if [ -f ~/.crittercism_keys ]; then
		# this is required to inject the environmental variables into
		# the shell spawned by Xcode
        source ~/.crittercism_keys

        APP_ID="MY_FIRST_APP_ID_abcdefghi"

		# instead of having your API key here, it is copied in from the
		# environmental varible
        API_KEY=${MINI_AUDICLE_SECRET_KEY}

		# run the script
        source "${SRCROOT}"/ios/libs/Crittercism/dsym_upload.sh
    else
        echo "~/.crittercism_keys does not exist. Not uploading dSYM!"
    fi
else
    echo "Not a Release build so not auto-uploading dSYM file."
fi
{% endhighlight %}
 
It requires a little setup (creating the .crittercism_keys file), but we can now **both auto-upload dSYMs and host this project publicly without exposing the API key**. This script also only upload dSYMs for Release builds. 

[1]: http://support.crittercism.com/articles/knowledge_base/Uploading-dSYMs-to-Crittercism-automatically/
[2]: http://docs.crittercism.com/api/api.html
[3]: https://wiki.jenkins-ci.org/display/JENKINS/Crittercism+dSYM+Plugin