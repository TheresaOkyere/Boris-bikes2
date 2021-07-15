##From Strings to HTML

"hello" is a boring thing to send to our users. We can do better!

Behind the scenes, Sinatra was actually sending "hello" as an [HTML](html.md) file. Now we know that, we can just substitute our "hello" string for some cool HTML:

````ruby
require 'sinatra'
require 'sinatra/reloader' if development?

get '/' do
  "<div>
    <img src='http://placekitten.com/500/500'>
   </div>"
end
````

Now go to the webpage at the `localhost` address and check out the fruits of your labour. If the page isn't showing as you expect - are you using `Sinatra::Reloader`?

![alt text](images/sinatra/sinatra_basic_4.png)

A good time to commit your code, push it to Github (:pill: [Version Control with Git](git.md)), and switch Driver/Navigator Roles&nbsp;:twisted_rightwards_arrows:

However, this image, as lovely as it is, is a bit dull. Real web pages have something else in them that makes them look good: CSS.

CSS stands for Cascading Style Sheets. It's a language that describes what HTML elements should look like when they are rendered by the browser. For example, let's add some CSS code to create a border around the **div** that contains our image.

````ruby
require 'sinatra'
require 'sinatra/reloader' if development?

get '/' do
  "<div style='border: 3px dashed red'>
     <img src='http://placekitten.com/500/500'>
   </div>"
end
````

Now our web page looks like this:

![alt text](images/sinatra/sinatra_basic_5.png)

To achieve this effect we added an **attribute** called **style** to the **div** element. Its **value** is `border: 3px dashed red`. It defines what style is applied to the element, in this case a border, 3 pixels wide, dashed (as opposed to solid, for example), and red in colour.

By combining HTML and CSS we can achieve sophisticated visual effects in our web applications. We'll explore the basics of how HTML and CSS work in more details later this week and we'll discuss advanced HTML and CSS features in weeks 7 and 8.

Before we move on let's commit our code, push it to Github and switch Driver/Navigator Roles again&nbsp;:twisted_rightwards_arrows:

Next up, we'll see if we can modularise some of our code into a _view_.

[Go to part 5](sinatra_5.md)

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
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/sinatra_4.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/sinatra_4.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/sinatra_4.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/sinatra_4.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/sinatra_4.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
