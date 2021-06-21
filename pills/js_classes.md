# Classes in JavaScript

The `class` keyword was introduced in ES6.


### Defining a class
In Ruby, we define and instantiate a class like this:
```ruby
class Dog

end

dog = Dog.new
```

In JavaScript, this looks like:
```javascript
class Dog {

}

var dog = new Dog();
```
Under the hood, JavaScript classes are actually types of functions. Try running `alert(typeof Dog);` The `class` syntax creates a function which is called `Dog`.

If you would like more background reading on functions, check out the [JS functions pill](https://github.com/makersacademy/course/blob/master/pills/js_functions.md) in the Makers Course repository

### Initialisation code
In Ruby, we have an `initialize` method, which is called when a new object is created:
```ruby
class Dog
  def initialize(breed)
    @breed = breed
  end
end
```

In JavaScript, the `constructor` method is called.
```javascript
class Dog {
  constructor(breed) {
    this.breed = breed;
  }
}

var barney = new Dog('Pug');
```
> inside the function, `this` will be the newly created object.

In Javascript, there are no `attr_reader` or `attr_accessor`. Instead, instance variables are accessible to the outside by default so this code will return `'Pug'`

```javascript
var barney = new Dog('Pug');
barney.breed
```




## Defining methods

In Ruby, we define a method like so:
```ruby
class Dog
  def bark(name)
    "#{name} says Woof!"
  end
end
```

In Javascript, this would look like:
```javascript
class Dog {
  bark(name) {
    console.log(name + ' says Woof!');
  }
}
```
The `bark` method is stored in `Dog.prototype`. You can see this for yourself. Try running the following in the Web Console:
```javascript
var fido = new Dog();
console.log(fido);
```
By expanding the `Dog {}` that's returned, you can see that `bark` is found under the `__proto__`.

It's easy to think of `bark` as being a method of `Dog`.  But it isn't.  Objects in JavaScript are just bags of properties.  So `fido` is just a bag of properties, some of which it inherits from the prototype of `Dog`.


We can then call the `bark` method on any instance of `Dog` like so:
```javascript
fido = new Dog('Basset Hound');
fido.bark('Fido');
```

## Final structure

Here's the dog class, with the two previous methods.

```javascript
class Dog {
  constructor(breed) {
    this.breed = breed;
  }

  bark(name) {
    console.log(name + ' says Woof!');
  }
}
```
Here's how to then use this class:
```javascript
var fido = new Dog();
fido.bark('Fido')
```
This will print `Fido says Woof!` to the console.

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/js_classes.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/js_classes.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/js_classes.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/js_classes.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/js_classes.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
