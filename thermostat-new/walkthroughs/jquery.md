# Walkthrough - Thermostat: jQuery

[Back to the Challenge](../jquery.md)

First. jQuery. Either download the script or grab one off a [CDN](https://en.wikipedia.org/wiki/Content_delivery_network). Load it in `index.html`.

Download:
```html
<script src="js/jquery.min.js"></script>
```

CDN:
```html
<script src="https://code.jquery.com/jquery-2.1.4.min.js"></script>
```

Before you address the thermostat, make sure that you understand some basic jQuery concepts: `$(document).ready(function() { })`, the jQuery selector, event listeners, and callbacks.

#### $(document).ready(function() { })

This utility function translates to "only execute the function when the document is ready", i.e. when the DOM is loaded. This is a good idea because it's difficult (but not impossible!) to attach an event listener to something that isn't there. Forgetting to wrap jQuery code in this is a common source of bugs.

#### jQuery selector

The jQuery selector generally works like this:

```javascript
$('element')
```

where `element` is a CSS selector, or a tag name. Chrome Dev Tools actually comes with a very similar feature, so you can try it out on any page. Try selecting some `.classes`, `#ids` and HTML tags.

#### Event listeners

In longhand, these usually look like

```javascript
$('element').on('event', function() {

})
```

where `event` is an action you would like to listen for on the page. Popular events include clicks, scrolls, typing and generally any kind of page interaction. The most popular ones generally have convenient shortcut functions, so you can write `$('element').click(function() { })`, for example.

#### Callbacks

Callback are generally a source of massive confusion, so this explanation will be a simplistic explanation suitable for understanding what role they play in jQuery. You've actually been using them in Jasmine without even knowing! The callback is the anonymous function passed as last argument to the event handler:

```javascript
$('#some-heading').click(function() {
  // this function is the callback!
})
```

In this case, the callback is the function passed to the `click` function, that executes at some point in the future. The plain English translation would be "when there is a click on the element with the ID `some-heading`, run the function".

Enough theory! Let's start by getting the initial temperature to display when the page loads.

>This walkthrough is written with one possible workflow when developing UIs with jQuery, which may or may not be to everyone's personal taste. Try it out though and see what you think.

Bust out the console, and find the element to be manipulated using the jQuery selector.

```javascript
// console
$('.temperature') // [] - nope
$('#tamparatare') // [] - you drunk?
$('#temperature') // [   <h1 id="temperature"></h1>] - bingo!
```

Now build up what you're trying to do. We want to manipulate the text of this `h1`, so find the right jQuery function. jQuery is such a vast library that if you type what you think you're trying to do into the documentation, there's probably a function to do it. You're trying to alter the text, so let's see if that works.

```javascript
// console
$('#temperature').text('hello jQuery world!');
```

Success! We want to set this to the thermostat's temperature, so we'll need a new thermostat.

```javascript
// console
var thermostat = new Thermostat();
$('#temperature').text(thermostat.temperature);
```

Now we can put this in our actual interface file, wrapped in a `$(document).ready(function() {})`, so that it only triggers when the DOM has finished loading.

```javascript
// interface.js
$(document).ready(function() {
  var thermostat = new Thermostat();
  $('#temperature').text(thermostat.temperature);
})
```

Let's go for something a bit more complex, like changing the temperature. jQuery allows you to attach **event listeners** to elements in the DOM, allowing the page to react to user input. The functions we want to run when the event happens are passed in an **anonymous function** (which in this case is also a **callback**). Those terms in bold are important, but we'll get to them once our thermostat does stuff!

Take a second to think about the flow of what happens when a user interaction happens:

**user input -> event listener -> update model -> update view to reflect change in model**

In code:

```javascript
$('#temp-up').on('click', function() { // event listener
  thermostat.increaseTemperature(); // update model
  $('#temperature').text(thermostat.temperature); // update view
})
```

And the same again for decreasing the temperature:

```javascript
$('#temp-down').click(function() { // this is an alternate version of .on('click'), with a sprinkle of jQuery syntactic sugar
  thermostat.decreaseTemperature();
  $('#temperature').text(thermostat.temperature);
})
```

Looks like there's something repeated 3 times, so it's probably time to refactor updating the temperature to its own clearly-named function:

```javascript
function updateTemperature() {
  $('#temperature').text(thermostat.temperature);
}
```

Hooking the other buttons up should be relatively straightforward, resulting in something like this:

```javascript
// interface.js
$(document).ready(function() {
  var thermostat = new Thermostat();
  updateTemperature();

  $('#temp-up').click(function() {
    thermostat.increaseTemperature();
    updateTemperature();
  });

  $('#temp-down').click(function() {
    thermostat.decreaseTemperature();
    updateTemperature();
  });

  $('#temp-reset').click(function() {
    thermostat.reset();
    updateTemperature();
  });

  $('#psm-on').click(function() {
    thermostat.powerSavingModeOn();
    $('#power-saving').text('on')
    updateTemperature();
  })

  $('#psm-off').click(function() {
    thermostat.powerSavingModeOff();
    $('#power-saving').text('off')
    updateTemperature();
  })

  function updateTemperature() {
    $('#temperature').text(thermostat.temperature);
  };
});
```

The last piece of the puzzle is to colour the display according to the energy usage. As you saw when building the business logic, the JavaScript code wasn't responsible for presentation. It might be tempting to do something like this:

```javascript
function updateTemperature() {
  $('#temperature').text(thermostat.temperature);
  if(thermostat.energyUsage() === 'low-usage') {
    $('#temperature').css('color', 'green')
  } else if(thermostat.energyUsage() === 'medium-usage') {
    $('#temperature').css('color', 'black')
  } else {
    $('#temperature').css('color', 'red')
  }
}
```

What's wrong with this code? Firstly, there's a big `if/else if/else` statement, which is usually a code smell. Secondly, there's subtle duplication - this is just a repeat of the logic within the thermostat itself. Thirdly, you can see that the code is very interested in CSS - so, why not delegate to the CSS itself, and just change the class so that the CSS can decide how to handle colour?

```javascript
function updateTemperature() {
  $('#temperature').text(thermostat.temperature);
  $('#temperature').attr('class', thermostat.energyUsage());
}
```

And now the CSS can handle colour (don't forget to place this in its own file and link it in with the appropriate tag):

```css
.low-usage {
  color: green;
}

.medium-usage {
  color: black;
}

.high-usage {
  color: red;
}
```

[Forward to the Challenge Map](../README.md)


![Tracking pixel](https://githubanalytics.herokuapp.com/course/thermostat/walkthroughs/jquery.md)
