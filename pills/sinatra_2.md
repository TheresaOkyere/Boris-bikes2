## _Hello World_ application

Let's create a basic web application using Sinatra. It will have only one page and on this page there will be "hello!" text. This is what it will look like:

![What we're making](images/sinatra/sinatra_basic_1.png)

Now, let's make it happen. Create a new file _hello.rb_ and type the following:

````ruby
require 'sinatra'

get '/' do
  'hello!'
end
````
> Why are we requiring `sinatra` in this file?

Now, run this file.

`$ ruby hello.rb`

You should see this:

```
== Sinatra/1.4.3 has taken the stage on 4567 for development with backup from Thin
>> Thin web server (v1.5.1 codename Straight Razor)
>> Maximum connections set to 1024
>> Listening on localhost:4567, CTRL+C to stop
```

Open [this address](http://localhost:4567) in the browser and you should see a white page with "hello!" in the upper left corner.

This would be a good time to commit your code, push it to Github (:pill: [Version Control with Git](git.md)), and switch Driver/Navigator Roles&nbsp;:twisted_rightwards_arrows:

> :pill: [`localhost` and web host addresses](localhost_web_addresses.md)

## How does _Hello World_ work?

So, let's take a look at the source code again.

````ruby
require 'sinatra'

get '/' do
  'hello!'
end
````

First, we require Sinatra, the gem, to be available in our application.

Then we call the `get()` method, provided by Sinatra, passing `'/'` as an argument (this could therefore be re-written `get('/')` but the convention is to ignore the brackets).

What this method does is tell Sinatra to respond to a `GET` HTTP request to the path `/` (which happens whatever the user visits `http://localhost:4567`) and return the result of executing the block, in this case the string 'hello!':

1. The browser requests page `/` (`http://localhost:4567/`) ->
2. Sinatra activates the block defined by the `get '/' do` method call ->
3. the block returns the string 'hello!' ->
4. Sinatra returns this string ('hello!') to the  User

The '/' part of the address is the last slash in `http://localhost:4567/`. Next up, let's try adding another page.

[Go to part 3](sinatra_3.md)

Resources
--------

* [Sinatra Main Site](http://www.sinatrarb.com/)
* [Sinatra Main Intro Documentation](http://www.sinatrarb.com/intro.html)
* [Talk Slides on Sinatra Chat Server](http://obfusk.org/achatwithsinatra/#1)
* [Detailed Talk Slides on Sinatra](http://www.slideshare.net/BobNadlerJr/sinatra-flatiron)
* [Sinatra Up and Running (Book)](http://shop.oreilly.com/product/0636920019664.do)
* [Jump Start Sinatra (Book)](http://www.sitepoint.com/store/jump-start-sinatra/)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/sinatra_2.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/sinatra_2.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/sinatra_2.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/sinatra_2.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/sinatra_2.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
