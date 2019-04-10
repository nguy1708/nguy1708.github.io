---
layout: post
title:  "The Real Start"
date:   2019-04-09 22:33:00 -0500
categories: Ruby
---

### And so it begins...

As I begin this journey I looked up what resources is best to learn on. There were two that always came up in every community forum I visited.

* The Odin Project - A free online resource that is very well structured for beginners of all skill levels
* The Ruby on Rails Tutorial by Michael Hartl - A book specifically for the ins and outs of Ruby on rails

With these two choices I figured I would be set for a while until I become sufficient enough. I notice a lot of people just jump straight into Ruby on Rails first and learn Ruby as they go. I was a little hesitant following this popular route because Rails is something you add on top of your Ruby skills. Sure, I'm rather familiar with scripting languages and programming itself, but I think it would be better to start with the basics so I can get a good foundation. It may seem faster to just start with Rails, but if my foundation is solid, then it should alleviate any headaches in the future. Or at least...in theory&trade;.

![alt text](https://github.com/nguy1708/nguy1708.github.io/blob/master/Images/outline.png?raw=true "The Odin Project outline")

This is the first part of the Odin Project's curriculum. First glance, doesn't seem too bad. I assume that we'll learn about the syntax on how functions are written, data types, some basic loops, arithmetic, variables, how to declare them, and the like.

Right in the introduction I feel validated as it talks about how some people diver straight into Rails. They too believe that its good to build a good foundation otherwise a lot of time is going to be wasted googling the error messages I would potentially get if I just dived into Rails.

So as part of the learning process the guide asks me to do all of Code Academy's basic Ruby course. This beginning part is longer than I thought, but it's expect starting from scratch.

As expect the introduction to Code Academy's Ruby course had me learn about variables, how to declare them, the different data types, math, and Boolean operators. Nothing seems out of the ordinary from what I've experienced learning Python, Java, and C/C++.

Like Python, the syntax is not as strict like Java or C/C++ since its a dynamic, interpreted language. So you don't need to worry about semicolons `;` or tabs (although tabs in Python is very essential).

 I do want to note that the "else if" command is unique in Ruby. To declare it, you have to write `elsif` which seems like a shortened version of "else if". It's like the in between of `else if` from Java and `elif` from Python.

Something that I did learn that I thought was interesting was the unique conditional `unless`. It's declared like a normal `if` statement, but inversed. I don't know how to explain it in this moment, so I'll give an example:

```ruby
hungry = false

unless hungry
  print "Continue to be productive doing normal activities"
else
  print "Get something to eat, you're hungry!"
```

The result of this small code block would printed "Continue to be productive doing normal activities".

It's like saying, you're not hungry because **hungry** is set to be **false**. So when you go through the conditional, you're not hungry, so it prints that line. Its like unless is checking for the variable to be false, and if it is, it will do down that route.

If **hungry** was set to be **true**, the we would get the "Get something to eat, you're hungry!". This is because how unless conditional works. Since our variable is true, it passes the first `unless` and then comes to the `else`.

I hope that makes since. I wanted to stay up longer, but I'm getting tired. I've successfully completed Code Academy's 1st and 2nd sections. The next section will go over loops and iterators which should be fun. Two sections down, 8 more to go.
