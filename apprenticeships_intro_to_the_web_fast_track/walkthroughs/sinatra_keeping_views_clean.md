# Walkthrough – Sinatra: Keeping views clean

[Back to the Challenge](../sinatra_keepig_views_clean.md)

Let's refactor our code to push the 'heavy logical lifting' of random name generation out of the view, and in to the controller. Views shouldn't concern themselves with this sort of complexity.

Before we refactor, our view looks something like this:

```erb
<h1>My name is <%= ["Amigo", "Misty", "Almond"].sample %></h1>
<div style='border: 3px dashed red'>
  <img src='http://placekitten.com/500/500'>
</div>
```

Our route for this looks something like this:

```ruby
# in app.rb

get '/cat' do
  erb :index
end
```

First, let's move the complex randomisation into the route. We'll assign it to an instance variable so we can access the return value from within the view.

```ruby
# in app.rb

get '/cat' do
  @name = ["Amigo", "Misty", "Almond"].sample
  erb :index
end
```

Now, we can just access the instance variable within the view:

```erb
<h1>My name is <%= @name %></h1>
<div style='border: 3px dashed red'>
  <img src='http://placekitten.com/500/500'>
</div>
```

That's much easier to read! Also, we've pushed the 'heavy lifting' of name randomisation a bit 'further down the stack'.

> Although you are used to instance variables being accessible throughout an instance of a class, the `@name` instance variable is _only accessible within the scope of the route in which is was defined_. In other words, you cannot visit `/cat` to set `@name`, and then visit another route that uses that same `@name`. **The instance variable cannot be accessed by any other routes.**

Let's dive a bit more into the `erb` method. Technically, the `erb()` method reads the input file, processes Ruby that is inside and returns resulting HTML. This HTML is then returned by the block passed to the `get()` method:

![Rendering ERB in Sinatra](../images/sinatra_rendering_erb_diagram.jpg)

Before proceeding, you'll want to commit the code, push it to Github and switch Driver/Navigator Roles &nbsp;:twisted_rightwards_arrows:.

Next up, let's use _parameters_ to add some more sophistication to our kitten website.

[Forward to the Challenge Map](../README.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=apprenticeships_intro_to_the_web_fast_track/walkthroughs/sinatra_keeping_views_clean.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=apprenticeships_intro_to_the_web_fast_track/walkthroughs/sinatra_keeping_views_clean.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=apprenticeships_intro_to_the_web_fast_track/walkthroughs/sinatra_keeping_views_clean.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=apprenticeships_intro_to_the_web_fast_track/walkthroughs/sinatra_keeping_views_clean.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=apprenticeships_intro_to_the_web_fast_track/walkthroughs/sinatra_keeping_views_clean.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
