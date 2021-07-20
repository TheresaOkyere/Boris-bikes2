# REST

In the bad old days of building URLs there was no way of structuring them
properly. It was pretty common for a simple set of URLs for doing basic actions
like create, read, update and delete (CRUD) on something like adding a
restaurant to a database to look as messy as this:

* `new_restaurant`
* `update_restaurant/123`
* `deleteRestaurant/123`
* `get_restaurant?id=123`

Here we have nothing standardised, it's hard to understand what's going on and
hard to structure our app so that all of these routes point to the same
controller in our framework.

## Roy Fielding to the rescue!

When Roy Fielding published his doctorate on Representational State Transfer
(REST), he probably didn't realise it would end up transforming the entire
structure of the web.

In REST, URLs aren't just vague strings we make up on the spot. Instead they map
onto a *resource*. The idea of a *resource* is pretty much the same idea as an
object in OOP, it's just a **noun** that matches to something in the real world. So in the previous example, our resource would be `restaurants`, since this is what we're
creating/reading/updating/deleting.

The second idea of REST is that we can use a set of actions that HTTP allow us
to specify when we create a request. In HTTP, when you visit http://google.com
in your browser, behind the scenes Google Chrome actually sends a `GET` request
to the server and waits for a response.

![a GET
request](https://www.safaribooksonline.com/library/view/head-first-servlets/9780596516680/httpatomoreillycomsourceoreillyimages1377903.png.jpg)

But HTTP also allows us to use other verbs like `POST`, `PATCH` and `DELETE`
when sending requests. Fielding realised that these verbs matched perfectly
onto CRUD. Using this knowledge, he showed how we could tidy up our URLs by
rather than having a different URL/resource for each action, having one resource
for everything we want do:

* CREATE - POST /restaurants
* READ - GET /restaurants/123
* UPDATE - PATCH /restaurants/123
* DELETE - DELETE /restaurants/123

See how much tidier that is? Now we have one URL (although of course when
creating we don't have the ID as we don't know what it is until we've created it) rather than the mess of URLs we had previously.

Although there's of course much more to REST, understanding that it's all about
*resources*/*nouns* (like restaurants in this example), and *verbs*
(POST/GET/PATCH/DELETE) is the main thing you need to understand.

## Routing for a real application

When you want to write a web app, you need a few more routes on top of the basic create, read, update and delete.  You need:

* A route for listing all the records for a certain resource (e.g. all the restaurants).
* A route to show a web form for entering the details of a new record.
* A route to show a web form for entering the new details of an existing record.

Rails has a set of conventions for what URLs to use for these extra things:

```sh
Verb    URI Pattern            Controller#action
------  ---------------------  ------------------
GET     /restaurants           restaurants#index
POST    /restaurants           restaurants#create
GET     /restaurants/new       restaurants#new
GET     /restaurants/:id/edit  restaurants#edit
GET     /restaurants/:id       restaurants#show
PATCH   /restaurants/:id       restaurants#update
PUT     /restaurants/:id       restaurants#update
DELETE  /restaurants/:id       restaurants#destroy
```

## More Resources (geddit?)

- [Slides based on this pill](http://slides.com/makersacademy/rest)
- [A beginners guide to REST](https://codeplanetio.wordpress.com/2013/12/31/principles-good-restful-api-design/)
- [A simple guide to HTTP](https://www.safaribooksonline.com/library/view/head-first-servlets/9780596516680/ch01s08.html) - click on the next link on the top right to keep reading, there's some good diagrams here!
- [GitHub has a well-designed RESTful API that's worth taking a look](https://developer.github.com/v3/)

## Exercises

- Design the URL schema for a RESTful API for the MakersBnb project (a clone of Airbnb)
- Design a RESTful API schema for Gmail

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/rest.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/rest.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/rest.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/rest.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/rest.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
