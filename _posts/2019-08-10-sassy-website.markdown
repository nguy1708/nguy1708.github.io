---
layout: post
title:  "Sassy Website"
date:   2019-08-10 16:52:03 -0600
categories: Ruby
---

It just occurred to me that I haven't shared the project I'm documenting on this whole time. If you go to my github (github.com/nguy1708) you can find the repository called "Sample App" which is what I'm using for my learning thus far.

I've also been making this following a book by Michael Hartl. For anyone looking into getting into rails, I highly recommend it. 

For this update, I spent a little more time learning the basics of HTML5 and CSS. Then enhancing it one level by using Twitter's Bootstrap and Sassy CSS. Sassy CSS is basically CSS, but it allows for better formatting and variable declarations. A very powerful tool. 

Something that was pretty interesting this time around was learning about the asset pipeline. Essentially this pipeline is how all the files come together when you use rails. 

The asset pipeline allows us to better refactor and eliminate any duplication in code. Something else learned was the use of partials. This also helps clear any clutter in the main layout. To use it was a little odd at first. You first invoke it by placing something along the lines of:
```ruby
<%= render 'layouts/your_page' >
```

Then for it to work, you just have another file in your layout folder with the file name `_your_file.html.erb`. The underscore is rather important in the nomenclature of this. Using it clears up the layout a lot and then you can fine tune any parts instead of one big file. 

As for the asset pipeline, there are a few directories you can do this in. One is the `app/asset` folder I have been working on. Then you can place any assets for libraries in the `lib/assets`, and similarity for 3rd party vendors in `vendor/assets`.

What makes this special about asset pipeline is that it can help simplify production and management of assets such as CSS, Javascript, and images. Although I haven't actually written anything and am just using the one rails includes already, it sounds like you can do cool things with the preprocessor by allowing you to use other frameworks like CoffeeScript (also have not dived into, Sass, etc)

Then I learned about named routing conventions. So instead of routing normally by just stating `get static_pages/home`, you can actually give it a name to make it easier to use. To do so you can just use the commands `get "/your_name", to: controller#page`. So, using the example above, it can just be `get "/home", to: static_pages#home`. 

Then the last thing in the chapter was integration tests. You can actually just generate it by using `rails generate integration_test name_of_test` and it will just generate the necessary files for you. With this, it allows you to do end-user tests so that you don't have to go back and manually click on every link to make sure it's running correct. A huge time saver here. 

Next chapter seems to focus on modeling users, so this will be interesting....