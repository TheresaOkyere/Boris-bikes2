# Walkthrough - JavaScript basics

[Back to the Challenge](../javascript_basics.md)

Let's write some JavaScript!

Fire up Chrome (you can do this in Safari or Firefox, but the Chrome DevTools console is extremely well designed and user friendly). Next, find the DevTools console - the ninja way (and therefore the best way) is to use a keyboard shortcut - `Cmd`-`Opt`-`j` on a Mac, and `Ctrl`-`Shift`-`j` elsewhere. Otherwise, you can right-click anywhere on the page and select "Inspect element" (`Cmd`-`Opt`-`i` or `Ctrl`-`Shift`-`i` if you prefer shortcuts!) to show the DevTools, and then click on "Console".

First things first: `console.log()` is the equivalent of `puts`, `print` or `p` in Ruby, and you will probably use it a lot to debug your code. Chrome DevTools is really good at giving you as much information about objects and functions that you log to the console - always remember the debugging mantra: **"if in doubt, log it out"**

Hello world is relatively simple: `console.log('Hello world!')`.

To create a `Greeting` object, we use the `class` keyword:

```javascript
class Greeting {

}
```

To define a method:

```javascript

class Greeting {
   hello(person) {
     return 'Hello, ' + person + '!';
   }
}
```

And to use it:

```javascript
var greeting = new Greeting();
greeting.hello('Maker'); // 'Hello, Maker!'

/*
Note:
- Single line comments in JavaScript use '//'
- Multiline comments look like this comment
But, you should almost never need these as your code should explain itself! =)
*/
```

For a standalone function that takes no arguments:

```javascript
function hiTimmy() {
  return 'Hi, Timmy!';
}
```

And to use it:

```javascript
hiTimmy(); // 'Hi, Timmy!'
```


For a standalone function that takes arguments:

```javascript
function hi(person) {
  return 'Hi, ' + person + '!';
}
```

And to use it:

```javascript
hi('Jenny'); // 'Hi, Jenny!'
```

While you are here, take a minute with your pair partner to take a glance at the different parts of Chrome's DevTools, especially the "Elements" tab - you will be using these a lot in the future.

### Experimenting with basic JavaScript language features

#### Strings and numbers

Strings are stringy, and behave most of the time.

As a general rule, don't mix numbers and strings (this is a good idea in general anyway), because strange things happen.

```javascript
'1' + 1 // '11'
'1' - 1 // 0
```

Another thing to be aware of is `NaN`, which means "not a number", as well as JavaScript's [approach to equality](https://dorey.github.io/JavaScript-Equality-Table/) (`==` and `===`) - tl;dr, just use `===` unless you have good reason not to.

#### Arrays

Arrays are very much like their Ruby counterparts:

```javascript
var array = [1, 2, 3, 4]
array[0] // 1
array.length // 4
array.pop() // 4
array // [1, 2, 3]
array.push(5) // array is now [1, 2, 3, 5]
```

#### Objects

Most things in JavaScript (other than [primitives](https://developer.mozilla.org/en-US/docs/Glossary/Primitive)) are objects. Objects are used like hashes in Ruby:

```javascript
var myObject = {} // you can make empty objects
var myOtherObject = {
                      some: 'stuff',
                      goes: 'in',
                      here: 123,
                      arrays: ['woah', 'check', 'it'],
                      nestedObject: {another: 'object'},
                      functionsToo: function(foo) { return foo }
                    }
// or objects with stuff in them - check out the fact you can put functions in, too

myOtherObject['some'] // 'stuff'
myOtherObject['here'] // 123

// so far, so Ruby. But you can also access stuff through "dot notation" - more like a normal object in Ruby

myOtherObject.arrays // ['woah', 'check', 'it']
myOtherObject.nestedObject.another // 'object'

// and, you can also get to functions. To call them, however, you have to use ()

myOtherObject.functionsToo // function(foo) { return foo }
myOtherObject.functionsToo('hi!') // 'hi!'
```

For further practice, you can check out the [Javascripting workshopper](https://github.com/sethvincent/javascripting).

Once you feel comfortable with JavaScript and using the browser's JavaScript console to play with code ideas, let's start writing some TDD JavaScript.

[Forward to the Challenge Map](../README.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=thermostat_es6/walkthroughs/javascript_basics.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=thermostat_es6/walkthroughs/javascript_basics.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=thermostat_es6/walkthroughs/javascript_basics.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=thermostat_es6/walkthroughs/javascript_basics.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=thermostat_es6/walkthroughs/javascript_basics.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
