---
layout: post
title:  "Configure Jekyll"
date:   2016-08-05 07:00:00 -0400
categories: jekyll tutorial config
---

Your _config.yml is the first place you should start when configuring your site.  This is where basic site configration information is stored.  This file can get rather complicated but let's first take a look at the basics.

Below is the beginning of my configuration file after editing it.

{% highlight yaml %}

# Welcome to Jekyll!
#
# This config file is meant for settings that affect your whole blog, values
# which you are expected to set up once and rarely need to edit after that.
# For technical reasons, this file is *NOT* reloaded automatically when you use
# 'jekyll serve'. If you change this file, please restart the server process.

# Site settings
title: Developing Woot
email: developingwoot@gmail.com
description: > # this means to ignore newlines until "baseurl:"
  I love tacos and writing code.  I want to start a blog that I change
  truly say is mine and keep it as free as possible.  This blog is 
  my story to blog free about code and tacos.
baseurl: "" # the subpath of your site, e.g. /blog
url: "http://developingwoot.github.io" # the base hostname & protocol for your site
twitter_username: developingwoot
github_username:  developingwoot
timezone: America/New_York

# Build settings
markdown: kramdown

{% endhighlight %}

These options are pretty self explanitory.

The way you edit it is by typing a value next to the key.  The key is 'title:' and the value would be Developing Woot.

title: Your sites title 
email: The email address you want displayed in your footer
description: Your sites description.  This is by default displayed in the footer also.
baseurl: This should be left blank with out current configuration
url: This is the url for your site

You can see I also included my twitter username and my github username.  Then I added someting that is not there by default, timezone.  This can be beneficial because Jekyll uses the timestamp of your post to determine when it should be displayed in your lists of posts.

If you right a post and the time of the post is some time in the future it will not display on your blog until that time has passed.  The timezone allows Jekyll to know where you are so your posts will show based on this timezone, not the timezone of the server.

Is that all there is to configuring a Jekyll blog?  Nope.  This config file can get extremely complex, but this at least gets you started.

To all you dev's out there I hope your Jekyll coding is going as well as mine but if not drop me a line I would be glad to help out.