# Gems

Gems are ruby libraries that can be easily reused across projects. A large number of gems exist to help developers leverage the code written by other developers. Gems are designed to be easily portable across projects.

The frameworks [Ruby on Rails](http://rubyonrails.org) and [Sinatra](http://www.sinatrarb.com) are just gems themselves.

## How to use gems

There exist gems for pretty much anything that you may need in your Ruby code: authentication, games development, security, communications, etc.

Let's take a look at a particular example of using a certain gem. For example, let's pretend we want to send a text message from our Ruby program. Text messages can be sent by [Twilio](http://www.twilio.com), a communications provider that developer its own gem called [`twilio-ruby`](https://github.com/twilio/twilio-ruby) for us to use.

First, we'll need to install it. In your command line type

````
$ gem install twilio-ruby
````

This will download it from the internet (from [RubyGems.org](https://www.rubygems.org), to be exact) and install into your system. Gem installations are specific to your ruby version, so if you install a gem for `ruby-2.0.0` and then switch to `ruby-1.9.3`, you'll need to install it for that version as well.

````ruby
require 'twilio-ruby' # we're telling ruby to load the gem

# put your own credentials here, get them at twilio.com
account_sid = 'ACxxxxxxxxxxxxxxxxxxxxxxxxxxxxx'
auth_token = 'yyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy'

# set up a client to talk to the Twilio REST API
client = Twilio::REST::Client.new account_sid, auth_token

# send an sms
client.account.sms.messages.create(
  :from => '+14159341234',
  :to => '+16105557069',
  :body => 'Hey there!')
````

Provided that you have the credentials (account ID and authentication token) from [Twilio](http://www.twilio.com), this code is everything you need to send a text message from your Ruby code.

The first line is necessary to load the gem into memory. This makes the classes defined inside the gem available to our program. In particular, after the gem has loaded, we get access to `Twilio::REST::Client` class that we instantiate on line 8 and use on line 11.

## How to install gems

````
$ gem install name_of_the_gem
````

This works but the problem with this approach is that the information about
the gems you're using isn't available to other developers.

For example, let's say you wrote an awesome program that sends text messages
and you put it on [Github](http://github.com) for others to use. However,
there's no easy way for other developers to know what gems you used in your
code. If we're talking about a short script such as the one above, the answer
may be obvious but real projects usually use dozens of various gems, so
installing all of them manually isn't an option.

Another problem with the manual approach is that when you deploy your
application, that is, copy it to a server for everyone to use, you may not
be able (or want to) install the gems manually.

Is there any better solution? Meet [Bundler](https://github.com/makersacademy/course/blob/main/pills/bundler.md)


## Where to find gems to use

A great place to start is [Ruby Toolbox](https://www.ruby-toolbox.com), a directory of ruby libraries and frameworks, ranked by popularity. Otherwise, a google search often gives good results. Try searching for "ruby send text gem" and `twilio-ruby` will probably be one of the top results.

## What a gem looks like inside

A gem is simply a set of Ruby classes that you require in your code just like any other Ruby code. You may take a look at [`twilio-ruby` source code on Github](https://github.com/twilio/twilio-ruby).

When you do

````ruby
require 'twilio-ruby'
````

you are actually requiring the `lib/twilio-ruby.rb` file that, in turn, loads all other files. To see what a gem looks like, clone [this repository](https://github.com/twilio/twilio-ruby) and take a look in the lib folder.

## How to create a gem

_Creating a gem is not much harder than writing a usual Ruby class, but that is another story..._

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=pills/gems.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=pills/gems.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=pills/gems.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=pills/gems.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=pills/gems.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
