---
layout: post
title:  "Jekyll Drafts - Write, review, rewrite, post"
date: 2016-08-05 08:00
comments: true
categories: jekyll tutorial drafts
---

In my blogging past I did a lot with a blogging CMS.  One of the features I really loved was the ability to write drafts.

If you have read any of my posts one thing you will quickly learn about me, I can't spell.  I probably didn't get the points on the SAT's for spelling your name correctly.  I know what the problem is, I go to fast.  Even when I review what I wrote it will look correct because I am not taking them time.

My solution to this problem is drafts.  When I was blogging with a CMS I would write a post and then have my wife review it for mistakes.  So how to get around this in Jekyll?

It's pretty easy actually.  It just takes three steps:

1. In your site root create a _drafts folder
2. When you create a draft post, create it in this folder and don't give it a date ex. my-first-draft.markdown
3. When you test your site add --drafts after the serve

{% highlight bash %}

$ bundle exec jekyll serve --drafts

{% endhighlight %}

Now your site should run serving posts from the _drafts folder as well as the _posts folder.  The files in drafts will have a post date that matches there last modified date so you should see them in the list of posts accordingly.

### What do I do when I want to post them? 

When your ready to make this post live all you need to do is rename it will a date, add a date to the Front Matter, and move it to your posts directory.

If that seems hard remember your a dev!  We don't do things the easy way we do them the right way.

