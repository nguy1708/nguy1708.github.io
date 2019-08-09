---
layout: post
title:  "Ruby Progress follow up"
date:   2019-08-03 16:12:46 -0600
categories: Ruby
---

Okay, I know I did promise an update. Still not exactly sure how I want to do these. I would love to go in-depth of the things I learned, but that would take quite a bit of time. For now I'll just do a summary. Maybe in the future I'll come back and touch back on these to really show that I retained what I learned.

Things accomplished so far:
* Learning to deploy early to build good practices
* TDD - test driven development. Good to build tests early on so that you can build around your objects and reduce the amount of regressions
* refactor frequently - with TDD, it will be easier to go back often and clean up code without worry of breaking the entire app
* ```rails generate controller ControllerName <optional action name>``` runs a script that makes and adds all the necessary items for a rails controller. 
* ```routes.rb``` is a ruby file that helps direct things. New routes will be defined here.
* Views are in a `.erb` format that stands for embedded Ruby. You can reduce redundancies with this by making functions that take care of it for you.
* TDD uses a "Red, Green, Refactor" cycle. What this really means is you write the test first. Make sure that it fails as expected (hence red). Then write the test such that it passes the test (green). Refactor as necessary afterwards!


I hope to continue to add to more to this blog! 
