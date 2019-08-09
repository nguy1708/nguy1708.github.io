---
layout: post
title:  "Rails Flavored Ruby"
date:   2019-08-09 17:35:23 -0600
categories: Ruby
---

For this update, I learned a little bit more about the inner workings of rails itself. While in rails, ruby techniques work, but you can't say the same the other way around.

These past few days, going over chapter 4 of Hartl's book, it goes over more of some basic Ruby techniques and OOP principles. It was a good refresher since I haven't done much since starting at my new job. It went over things like string manipulation, arrays, hashes, inheritance, classes, superclasses, etc. Was a very good refresher. 

It also went over what methods are, how to call methods, and I learned something cool you can do within rails. Did you know you can actually edit built in classes such as String, Range, etc classes in rails? By normal convention, you probably won't need to unless you have to, but it was cool to learn that you can edit them so that it fits your needs. To do so is pretty simple too. For example, if you wanted to have a method that shuffles your string be natively part of the String class, you would just do the following:

```ruby

class String
  def shuffle
    self.split('').shuffle.join
    # You can also do the above command without 'self'
    # " split('').shuffle.join " would also work
  end
end

>> "foobar".shuffle
=> "boroaf"

``` 

Normally, typing `"foobar".shuffle` by itself wouldn't do anything; however, but editing the built in class, you can give it that function which is super powerful. 

Something that I learned that was unique to Ruby is symbols. They act as labels are are a data type of `Symbol`. They're basically strings as the book calls it "without the baggage". To be honest, I didn't really work with them a whole lot, so I can't say I know the exact use cases other than being super convenient and not needing double quotes all the time. 

Note: Since they're a seperate data type, if you were to try doing `:name.split('')`, it would not work whereas `'name'.split('')` would. 

Something else that I found odd was the use of Ruby blocks. From my initial understanding of it, it's Ruby's way of doing for loops. The convention isn't has intuitive as other languages I think. Maybe this will be something I have to get used to. I did make some notes to hopefully make it easier to understand. 

```ruby
# each
(1..5).each do |i|
  # for each number i in the range of 1 thru 5, output 2 times the current i
  puts 2*i  
end
```

```ruby
# do a task x amount of times
>> 3.times {puts "hello"}
=> "hello" 
=> "hello" 
=> "hello" 
```

```ruby
# outputs to an array
>> (1..5)map { |i| i**2 } # takes the current i in range of 1 thru 5 and outputs the square into an array
=> [1,4,9,16,25] 
```

```ruby
# String array outputs with %w
>> %[a b c]
=> ["a", "b", "c"]
>> %w[a b c].map { |char| char.upcase }
=> ["A", "B", "C"]
>> %w[A B C].map { |char| char.downcase }
=> ["a", "b", "c"]

```

```ruby
# You can also do shorthand with "&:"
# It eliminates the need to state your "i"
>> %w[A B C DEE].map(&:downcase)
=> ["a", "b", "c", "dee"]
# as we can see, its shorter and more clean with "&:" 
```

Since I've gone and given some examples, I may as well state that I also learned about interpolation in ruby. Pretty simple to use I think.
```ruby
# String Interpolation with '#{}'
>> name = "Hoang"
=> "Hoang"
>> puts "#{name}"
=> "Hoang"
```

I feel like I'm leaving out a lot more of the stuff I learned, but this is the things that stuck with me most. They're setting up for some real webpage design in the next chapter. Hopefully I can continue to update my findings!

Until next time! 


