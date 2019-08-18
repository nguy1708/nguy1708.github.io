---
layout: post
title:  "User Model"
date:   2019-08-17 22:10:03 -0600
categories: Ruby
---

User models can get rather complex. There is a lot under the hood for something so basic such as collecting a name, email, and password when you sign up at a website.

I used SQLite for the sample website that you can find under the name "sample_app" at my github. (github.com/nguy1708)

It's nice that rails takes care of the simple details for you so you can just create pretty quick models by just using the command 
```Bash
$ rails generate model User name:string email:string
    invoke active_record
    create      db/migrate/2019TIMESTAMP_create_users.rb
    create      app/models/user.rb
    inovoke     test_unit
    create          test/models/user_test.rb
    create          test/fixtures/users.yml
```

What this does (like the other generate commands) is it sets up all the files required for your rails environment to work. In this case, it creates a simple database schema for you. In this case, I'm just trying to make it simple. Keep it down to an id, name, and string. 

| users | |
|------|------|
| id | integer | 
| name | string |   
| email | string |   

What I didn't know is that these schemas have a couple hidden attributes such as `created_at` and `updated_at`. It makes sense though, as getting the time stamp for both allows there to be less duplications should things get submitted at the "same" time or whatnot. 

In rails you can easily migrate your databases should you decide to add a column or other info by using the command:
```bash
$ rails db:migrate
```

Should you make a mistake, likewise you can use:
```bash
$ rails db:rollback
```
and it will reverse the previous migration. To be honest, I don't know SQL that well, but I assume it does something similar to the `drop_table` command if migrate acts as `create_table`.

Test driven development is very useful for models as you want to constantly implement tests after each change to make sure people who visit your website are entering the correct information and not just filling it out with junk (accounts with blank user names or emails that dont exist, trolls basically).

So right away, you want to create tests that makes sure that the name field is nonempty, so that people have to input something, and you also want to introduce a maximum because memory is limited (also, potential security flaws ;) ). The same goes for email and passwords. For emails specifically, you want to include a validation that the email is unique. You don't want the same user to make multiple accounts under the same email right? 

I learned that when you do this, Rails will save it into memory, but nothing stops it from checking for uniqueness in the database. This was shocking to me (because I'm a noob), but you actually have to include a uniqueness constrain in the database as well. 

The scenario the book used is lets say I was signing up. The website is under heavy load, so performance is not optimal. After I enter my information, I hit submit twice by accident. This sends 2 requests in quick secession. Then in rails, the first request passes validation and request 2 does the same. Then request 1 is saved AND request 2 is saved. Now we have two accounts that have the same exact email address despite checking for uniqueness in ruby.

To get around this, you have to introduce a database index to the email attribute. To do this in rails, its just a simple generate call.
```bash
$ rails generate migration add_index_to_users_email
```
as the name provides, it works like an index in a book. When it looks at say, "foo@bar.com", it will see how many times this shows up in the database (in this case, only 1). When it gets the duplicate request to save, the database will then be like, "oh wait, we already have an index with this email. REJECTED!!!!!".

So back to our scenario after adding the index to our schema, (don't forget to `rails db:migrate`!) when it receives the second request, it won't pass the uniqueness constraint. 

So I'm sure this all means nothing without the code, so I will include the user.rb file where it validates this information so that it might make more sense. 

```ruby
class AddIndextoUsersEmail < ActiveRecord::Migration[5.0]
  def change                                    # this function adds an index to the users email so 
    add_index :users, :email, unique: true      # that it is unique in the database
  end
end
```

```ruby
class User < ApplicationRecord                                # User inherits from ApplicationRecord
  before_save { self.email = email.downcase }                 # this just makes it so that emails are not case sensitive
  validates :name, presence: true, length: { maximum: 50 }    # checks user name is not blank, and has a max of 50 char
  VALID_EMAIL_REGEX = /\A[\w+\-.]+@[a-z\d\-.]+\.[a-z]+\z/i    # REGEX symbols
  validates(:email, presence: true, length: { maximum: 255 }, # checks to make sure email is nonempty and has a maximum limit
             format: { with: VALID_EMAIL_REGEX },             # checks email to make sure that symbols other than '@' are not used AND '@' and '.' has to be used to follow the convention of 'foo@bar.com'
             uniqueness: { case_sensitive: false })           # this makes sure the email is unique and is not case sensitive
  validates(:password, presence: true, length: { minimum: 6 })# this makes sure the password is nonempty, and has a minimum of 6 chars
  has_secure_password                                         # this hashes up the password such that if the db was obtained by a third party, they wouldn't be able to see the passwords
end
```

At first I just wanted to include the code about the index, but I figured I might as well share the model code for the user as well. I added comments so that it might make it easier to follow along with what I'm saying. 

This blog is really just a stream of my consciousness so I apologize if you read this far and it seems like a complete mess hahaha.

ANYWAYS, trying to think about what else I learned....

Oh, password management. Yeah, you passwords are pretty important as it helps protect your account from being accessed by an unauthorized source.

In the model, you want to make sure that passwords are also validated when a user creates one. There are times where someone could make a typo, so you want to add a line of code that has them add the password twice. That way the user will know if they inputted the right password.

Another thing to watch out for is making the passwords secure. You don't want to just store the password in your database. Its like storing someone's money in a bank inside open boxes. You want to put that money instead inside a LOCKED box so its more secure. You can do that natively within rails. The guide didn't go over how it encrypts the password, but you can use it by just adding the `bcrypt` gem. 

Additionally, you want to store that encryption inside your database, not the password by itself. You can use generate again:
```bash
$ rails generate migration add_password_digest_to_users password_digest:string
```

The migrate file will look similar to the index one having something along the lines of:
`add_column :users, :password_digest, :string`.

By doing this, it stores the encrypted password into the database instead of the real one. So then if your database was ever compromised, some rando won't be able to access your user's passwords (unless they figure out how to decrypt it. Ideally I would want to add my own encryption in the future and not reply on rail's built in gems. Some type of modified RSA key, although bcrypt might use it too).

Then the las step is to add the built-in `has_secure_password` method you see at the end of User Class code. It just allows you to have the ability to saved a hashed password into your database. It also adds in the password and password confirmation. 

I'm sure there are a lot more small details I'm leaving out, but these are the big things. In the next chapter it seems to go over the actual sign up process, so this will get more exciting!

Until next time!