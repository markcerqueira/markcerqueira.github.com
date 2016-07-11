---
layout: post
title: "Authenticating Programmatically Sent Emails"
description: ""
category: 
tags: [ruby, technical]
---
{% include JB/setup %}

Work on the Ruby and Sinatra project continues and this weekend I worked on creating a helper method for sending emails so I can have users confirm the emails they used to register. I wanted to send emails from a mailbox I set up on a custom domain I'm hosting with DreamHost. I created a mailbox on DreamHost's admin panel and with the [mail][1] Ruby gem it was pretty straightforward to get emails sent.

{% highlight ruby %} 
class ApplicationController < Sinatra::Base

  # Configure mail gem
  # You can use the config_env gem to save sensitive information (https://github.com/SergXIIIth/config_env)
  options = { :address              => 'www.yourdomain.com',
              :port                 => 587,
              :user_name            => 'welcome@yourdomain.com',
              :password             => 'yourpassword',
              :authentication       => 'plain',
              :enable_starttls_auto => true,
              :openssl_verify_mode  => OpenSSL::SSL::VERIFY_NONE }
  
  Mail.defaults do
    delivery_method :smtp, options
  end
	
  get '/mailtest/?' do
    Mail.deliver do
      to user@yourdomain.com
      from 'Welcome <welcome@yourdomain.com'
      subject 'Test Subject'
      body 'Test Body'
    end
  end
end
{% endhighlight %}

<div>
	<img class="rounded-corners" style="max-width: 800px; border: 0px;" src="/assets/images/posts/2016-07-10/spammer.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px;"><strong>Gmail has some doubts!</strong></p>
</div>

All looks good except Gmail ominously warns us: **"Gmail couldn't verify that chuckpad.io actually sent this message."** This means "Gmail doesn't know if the message is coming from the person who appears to be sending it," which makes our messages excellent candidates to get caught by Gmail's spam filters! Read more about authenticated messages [here][3].

After some digging around, I learned about **Sender Policy Framework (SPF) records**. Basically, a DNS record can have some metadata which identifies which servers are permitted to send email on behalf of the domain. And for some strange reason, DreamHost's default ["SPF information does not include all of DreamHost's mail servers"][4]. Fortunately, this can be easily remedied by [adding the SPF record][5] **v=spf1 include:netblocks.dreamhost.com** to our domain's DNS record.

<div>
	<img class="rounded-corners" style="max-width: 800px; border: 0px;" src="/assets/images/posts/2016-07-10/spf.png"/>
	<p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px;"><strong>Gmail's doubts are gone!</strong></p>
</div>

Give the DNS caches of the world a few hours to refresh, try again, and boom! **Success! Programmatic and authenticated!**

[1]: https://github.com/mikel/mail
[2]: https://github.com/SergXIIIth/config_env
[3]: https://support.google.com/mail/answer/180707?hl=en
[4]: https://help.dreamhost.com/hc/en-us/articles/220854287-What-SPF-records-do-I-use-
[5]: https://help.dreamhost.com/hc/en-us/articles/216106197-How-do-I-add-an-SPF-record-
