---
layout: post
title:  "Jekyll SEO - Draw Readers"
date: 2016-08-18 08:00
categories: jekyll seo tutorial
---



How do you get people to your blog?  Through search engine optimization (SEO).  What is SEO? Simply put it's adding special elements to your site that search engines are looking for.  These normally include a site map and meta tags.

### SEO

If you are blogging as a hobby a big key is motivation.  It's a lot of work to just put together a simple blog, and that work is only multiplied when adding content is concerned.  It's extremely satisfying knowing someone read what you wrote and they benefited from it.  SEO won't tell you someone is reading your blog so that is where free site analytics tools like [Google Analytics][google-analytics].

You can find more information on SEO at [Tutorials Point][tutorialpoint-seo].

---
*Note*: Content is KING!  The best thing you can do for your site and to improve search rankings is great unique content.  That's either really bad news or really good news depending on how you look at it.

---

### Meta tags

If you want search engines to know what your blog is about, and try and relate your posts to what readers want you need to include meta tags in your posts.

Google doesn't use meta tags, but Yahoo! and others do so it's worth the time and effort to add them to your site.  The [Jekyll SEO tag][jekyll-seo-tag] gem makes it really easy to add meta tags.

Add the below line to your Gemfile:

{% highlight ruby %}

gem 'jekyll-seo-tag'

{% endhighlight %}

Now that your Gemfile is all setup you just need to add it to your _config.yml.  Your _config.yml file might not yet have a gems section but no fear it's easy to add just add the below to the end of your _config.yml:


{% highlight ruby %}

gems:
  - jekyll-seo-tag

{% endhighlight %}

For meta tags you are done.  Your site will now have meta tags included so search engines that use that data will pick it up and included it.


### Sitemap

The sitemap tells a search engines web crawler where all your pages are ensuring that no content is missed.  For that reason a sitemap is very important, but if you had to build one completely from scratch... well let's just be glad we don't need to do that.  So how do we automate the process of creating a sitemap?

There is a Jekyll plugin called [Jekyll Sitemap][jekyll-sitemap] that will automate the creation of your sitemap which is oh so beautiful.  This install is just like the previous install just a different plugin name.

First add it to your Gemfile:

{% highlight ruby %}

gem 'jekyll-sitemap'

{% endhighlight %}

Then added it to the _config.yml file:

{% highlight ruby %}

gems:
  - jekyll-seo-tag
  - jekyll-sitemap

{% endhighlight %}

After adding Jekyll SEO tag and Jekyll Sitemap your "completed" files might look something like below:

Gemfile:

{% highlight ruby %}

source 'https://rubygems.org'
gem 'github-pages', group: :jekyll_plugins
gem 'jekyll-sitemap'
gem 'jekyll-seo-tag'

{% endhighlight %}

_config.yml:

{% highlight ruby %}

# Above is where all of your default config file data will be

gems:
  - jekyll-sitemap
  - jekyll-seo-tag

{% endhighlight %}

This is a good start for your sites SEO but we aren't there yet.  Next up we will setup Google Analytics to help you track hits to your site.

[jekyll-sitemap]: https://github.com/jekyll/jekyll-sitemap
[jekyll-seo-tag]: https://github.com/jekyll/jekyll-seo-tag
[google-analytics]: https://analytics.google.com/
[tutorialpoint-seo]: http://www.tutorialspoint.com/seo/