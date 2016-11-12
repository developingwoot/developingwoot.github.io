---
layout: post
title:  "Jekyll Install Tutorial"
date:   2016-08-05 06:00:08 -0400
comments: true
categories: jekyll tutorial install
---
There are a ton of much better posts on the Internet about how to create and setup a Jekyll blog, but this post exists because I wanted to chronicle my journey to setup a free blog that I can truly call mine.

First, I setup a github repo.  If you want to know how do to this check out their [GitHub Pages][github-pages]

I then created a local directory where I wanted to keep my Jekyll files and cloned the repo there.

I then cd'd into that directory when I refer to the root of my site, that's where I am talking about.

I'm writing this post on an old Linux Laptop that I have so I already had ruby installed version 2.3.1

Now I need to install the gem bundler so in a terminal
{% highlight bash %} 
$ gem install bundler
{% endhighlight %}

I got a warning that said it didn't detect gem in my path, this would have made me unable to execute commands, however, I was able to execute them no problem so I ignored it.  The gem did install.

I didn’t have a Gemfile so I added one and copied these lines into the file using vi (a Linux text editor.  You can use whatever text editor you have available).

{% highlight bash %}

source ‘https://rubygems.org’
gem ‘github-pages’, group: :jekyll_plugins

{% endhighlight %}

Next all I had to do was install the bundle.  I installed the bundle to the site root.

{% highlight bash %}

$ bundle install 
{% endhighlight %}

This installed a bunch of gem/jekyll related files but did not install the base Jekyll template.

So I ran (I ran so far awaaay... sorry)

{% highlight bash %}

$ jekyll new .--force

{% endhighlight %}

This installed Jekyll template files to my site root.

To launch the site and see the fruits of all that labor..

{% highlight bash %}

$ jekyll serve

{% endhighlight %}

The above command will serve my site so I can test it locally before pushing it up to github.  I must admit at this point I was a little underwhelmed, but remember I want a free site that I can call "MY" site.  Jekyll provides the perfect launch pad for my end goal.

Note:  If you ran these steps than you can keep your site up to date by running the below command in your site root.

{% highlight bash %}

$ bundle update 

{% endhighlight %}

Your all set to start configuring your free totally customizable blog.

Next up configuring your Jekyll site.

[github-pages]: https://pages.github.com/
