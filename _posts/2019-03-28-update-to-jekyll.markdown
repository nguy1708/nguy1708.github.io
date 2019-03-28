---
layout: post
title:  "Update to Jekyll"
date:   2019-03-28 03:42:16 -0500
categories: Ruby
---

Oh man, just when I thought it was over.

So when I try to run the website locally `http://127.0.0.1:4000/`, I get the following

{% highlight markdown %}
---
Not Installed: No such file or directory - git
Liquid Exception: No repo name found. Specify using PAGES_REPO_NWO environment variables, 'repository' in your configuration, or set up an 'origin' git remote pointing to your github.com repository. in /_layouts/post.html
    ERROR: YOUR SITE COULD NOT BE BUILT:
           ------------------------------------
           No repo name found. Specify using PAGES_REPO_NWO environment variables, 'repository' in your configuration, or set up an 'origin' git remote pointing to your github.com repository.
---
{% endhighlight %}

But when I push the updates to github, then it appears like it should...
