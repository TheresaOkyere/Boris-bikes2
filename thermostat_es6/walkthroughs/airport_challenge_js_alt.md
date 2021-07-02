# Walkthrough - Airport Challenge in JavaScript

[Back to the Challenge](../airport_challange_js.md)

### The Plane

At this point you should be comfortable with setting up Jasmine, so we'll dive straight in to the code. The first place I prefer to start with this kata is the plane, seeing as it's very simple in its logic and reduced complexity.

We're going to use **strict mode**, which you can read up on here: [MDN - Strict Mode](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode). To invoke strict mode, place this at the top of your file:

```javascript
"use strict";
```

First we want to give the user the ability to create a plane object by running `new Plane();`. Let's set up our test file (and jump right in to writing our first test while we're at it):

```javascript
describe("Plane", function() {
  let plane;

  beforeEach(function() {
    plane = new Plane();
  });

  it("is in-flight when created (for some bizarre reason)", function() {
    expect(plane.isAirborne()).toEqual(true);
  });
});
```

**NOTE** there is premature optimisation in this test file to speed up the pace of the tutorial since you will have been through these set up steps previously in the week.

Now we need to declare a `function` - specifically an `Object()` *constructor function* so that we can use the `new` keyword to **construct an object.**

```javascript
function Plane() {}
```

Now we need to do a little more to make our first test to pass. In an effort to be the first aircraft manufacturer to create a plane whilst it's in the air, we need to make sure that every new `plane` object has a property that reflects the in-flight status as being `true` from the start:

```javascript
function Plane() {
  this.isInFlight = true;
}
```

So here we should notice two things:
1. Our `isInFlight` property is situated between the `{}` of our `Plane` object constructor function.
2. The `this` keyword is employed.

In regards to #1, it's enough right now to be aware that this is where we store the property of an object. However, #2 is going to involve a [little bit of research on your part](http://javascriptissexy.com/understand-javascripts-this-with-clarity-and-master-it/). As a quick summary though, `this` tells the JavaScript interpreter that `isInFlight` belongs to `Plane`.

So now we've set up our *property*, we're in need of a method that interrogates that property and returns the relevant value to us, so that we are using messages (methods) to interact with our object, instead of direct accessing values. You may have noticed that our test references `plane.isAirborne()`. The `isAirborne()` referenced is the method name I am proposing we use.

Notice how we place parenthesis at the end. Why? This is to communicate to the JavaScript interpreter that we want it to execute this function, as opposed to returning the contents.

And now to create our method. As you will have noticed, we place the _properties_ of an object "inside" that object. However, when we are writing methods that relate to the same object, we use a different technique:

### The `prototype` keyword

It's important to understand that unlike Ruby where your instances inherit from a class, when it comes to JavaScript, your instances inherit from other instances. When the JavaScript interpreter cannot find a property or method defined on the current instance it looks to the next instance in the inheritance chain for the missing information.

But for now, we can think of `prototype` as a "storage area" which relates to the object referenced immediately before the `prototype` keyword and stores the function (method) you are defining. Let's look at some code to understand this more thoroughly:

```javascript
Plane.prototype.isAirborne = function() {};
```

In this example, `prototype` binds `isAirborne` to `Plane`, so that you can make an instance of `Plane` which has the method `isAirborne()` available to it. Now, we want `isAirborne()` to return the flying status of the plane, and we achieve this using the following:

```javascript
Plane.prototype.isAirborne = function() {
  return this.isInFlight;
};
```

Now is a fantastic opportunity to take stock of what we have learned here. Firstly, we have created a `Plane` **object constructor**, and given it a **property** of `isAirborne` (the 'is' part of the method name tells the next JavaScript Developer that this method should return a boolean value), and then we used the `prototype` keyword to *associate* or *bind* the `land` function to our `Plane`. Easy huh!

Great! Now we're defying gravity, let's find a way to bring this bird to the ground. Write a test for a `land` method:

```javascript
it("can land", function() {
  plane.land();
  expect(plane.isAirborne()).toEqual(false);
});
```

Looks good to me. Let's write a `land()` method, shall we?

```javascript
Plane.prototype.land = function() {
  this.isInFlight = false;
};
```

Perfect! Now we've grounded our plane, it's time to let that bird soar once more! Since we can follow the pattern we just set down for `land()` (as we just want to create a method that resets `isInFlight` to true), the hardest challenge we face now is coming up with a decent name for our method. I'm going to pull rank and say it's called `takeOff`. Now let's write a test:

```javascript
it("can take off", function() {
  plane.land();
  plane.takeOff();
  expect(plane.isAirborne()).toEqual(true);
});
```

And our method is not far behind...

```javascript
Plane.prototype.takeOff = function() {
  this.isInFlight = true;
};
```

Sweet success! We now have a fully-operational aircraft.

### The Airport

Now would be an excellent time to implement an airport. While our plane was a particularly simple object, our airport is going to need to interact with a second object, adding a dependency on a plane object. Since we test our objects in isolation, this is going to be the perfect time for us to explore doubling objects in JavaScript. I can literally feel your excitement travelling back in time, and bouncing off me while I write this. Incredible work people.

So, in the interest of brevity we're going to race through our test setup and get straight to writing our first test, which wants to make sure an `Airport` is empty upon creation:

```javascript
describe("Airport", function() {
  let airport;

  beforeEach(function() {
    airport = new Airport();
  });

  it("is initially empty", function() {
    expect(airport.planesAvailable()).toEqual(0);
  });

end
```

Let's create an `airport.js` file, require it in our `SpecRunner.html` and put in the `Airport` *object constructor function* so that we can actually make instances of `Airport` to test.

```javascript
function Airport() {};
```

Now I am interested in finding out how many `plane` objects are currently residing in the `Airport`. This sounds like a *property* to me, so I am going to create one for our `Airport`, and I am going to call it `hangar`, because that is where a sensible person might keep a `plane`. I am also going to choose an array as the data structure to house these `plane` objects, because at this point there doesn't seem to be the need for anything more complex:

```javascript
function Airport() {
  this.hangar = [];
};
```

Now you'll note that the test I wrote is looking for a `planesAvailable` method. Why not just access `Airport.hangar` directly? As your Ruby training has hopefully taught you now, we interact with objects via their public interface - an interface being the collection methods available to the object. With `Plane`








[Forward to the Challenge Map](../README.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=thermostat_es6/walkthroughs/airport_challenge_js_alt.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=thermostat_es6/walkthroughs/airport_challenge_js_alt.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=thermostat_es6/walkthroughs/airport_challenge_js_alt.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=thermostat_es6/walkthroughs/airport_challenge_js_alt.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=thermostat_es6/walkthroughs/airport_challenge_js_alt.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
