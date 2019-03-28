---
layout: post
title:  "Learning Jekyll"
date:   2019-03-28 02:22:07 -0500
categories: Ruby
---

Oh boy its been quite a night!

Initially, I thought it would be a good idea to create a personal website so I can keep
track of any progress with learning Ruby and on rails.

I got way too side tracked learning how to make a website using GitHub Pages (fantastic
tool by the way). I don't know anything about design though, so I thought, "Oh, I know
a great idea. Why not learn Jekyll since it uses Ruby on rails and I can have
custom themes that's constantly updated!"

YA, RITE.

I spent a lot of time Googling how to install themes and lots of places just would rather me fork their theme from their personal GitHub account, but then the gem management by Ruby gets really weird and I can't run the website that way. Then I tried copy and pasting elements from people's themes to see if that would work (giving credit to them of course), but no fruit. Eventually, I just picked out a simple theme rather than a fancy one from rubygems.org and called it a day. Probably built and tore apart this website 10 times before I got something that actually worked.

Would of made more sense to not of wasted so much time figuring out what a `gem` even
was in Ruby. What I learned though is that Gemfiles created when you create a new website allows you to install custom plugins and modules that would fit your need. It seems like there's a lot to be learned here as there are unlimited plugins and modules you can use to help your workflow.

The `_config.yml` is a neat little file where you can quickly change any main information such as the name of the website or links to social media. Any changes made to the look of the website or the theme will not impact this at all which is pretty neat.

It also seems like Jekyll allows you to create your own customer 404 error page as well. Something to consider revisiting once I learn more.

Posts are made within the `_posts` folder and the format seems to be in Markdown. I've used this before in college, but in a very barebones manner. Nothing too complex. If I can learn LaTeX, I'm sure markdown shouldn't be too bad to learn.

The `Gemfile.lock` file is a little confusing at first. First glance it seems to be all the dependencies that you can install into this as each line has a name and then a `~> (version number)` to indicate what version you're running. I accidently found out that if there is an update, running `bundle update` in the root directory of the website (`nguy1708.github.io` in this case) reaches out to `"https://rubygems.org"` to check for any updates and installs when necessary.

The one file I couldn't figure out is the `index.md`. It appears to be a mark down file but all that is in it is:

{% highlight markdown %}
---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---
{% endhighlight %}

Based off only that, it seems like I can maybe add additional links to the landing page. More than just the "About" section that is currently in place. More investigating will be needed here.

Tonight has been a trial by fire for sure. I could look up more extensively to figure out how to use this to the best potential, but I think I need to start slow. Firstly by starting with learning Ruby. Then, once getting familiar with that, go on to Ruby on rails.

Looking online, it seems that everyone points to the Odin Project as the go to guide to learning Ruby. The outcomes seem to be making sure that I know what an array in Ruby is like, how to call it, some basic string manipulation, etc.

I'm not quite sure how I want to structure this blog at the moment either. Whether keeping it like this where it's just all my thoughts spilled out onto text, or maybe try to limit it so that it sounds more professional. I'll play around and see what I'm satisfied with I guess.

Until next time!


<!--
You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
-->
