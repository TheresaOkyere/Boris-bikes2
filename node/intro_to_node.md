# Introduction to Node

Many thanks to [Spike](http://github.com/Spike01) for the original design of this walkthrough

If you haven't heard of Node, here is a short list of what Node is and what Node isn't:

* Node is a server-side implementation of JavaScript, using Google's extremely powerful V8 engine  
* Node is extremely good at handling large numbers of simultaneous requests or connections  
* Node is deliberately very minimal, encouraging users to write and use their own packages to extend functionality  
* Node is growing at an incredible rate. Its ecosystem is massive, with the number of published `npm` packages rapidly overtaking Ruby's gems - though fewer are regularly maintained
* Node is NOT multi-threaded; it's just very smart with how it deals with these requests  
* Node is NOT mature - while currently stable, it is nowhere near a 1.0 release  
* Node is NOT a magic bullet - despite what the Internet may say, Node is not suited to every task  
* Node is NOT easy - first of all, it's all JavaScript (tricky!) and has lots of new and strange conventions and techniques  

BUT

* Node is a lot of fun  
* Node is a different way to think about programming, so even if you don't find it fun, you will hopefully learn something!

Before we start, you should definitely read [Roi's introduction to Node](https://github.com/makersacademy/course/blob/main/pills/node.md), which explains the concepts behind non-blocking I/O and callbacks. Also, [Why the hell would I use Node?](http://www.toptal.com/nodejs/why-the-hell-would-i-use-node-js) and [Convincing the boss](http://nodeguide.com/convincing_the_boss.html) are great articles on what Node is good for.

It is also assumed that you have worked through the following:
* :pill: [node](https://github.com/makersacademy/course/blob/main/pills/node.md)
* :pill: [npm](https://github.com/makersacademy/course/blob/main/pills/npm.md)
* :pill: [grunt](https://github.com/makersacademy/course/blob/main/pills/grunt.md)
* :pill: [jshint](https://github.com/makersacademy/course/blob/main/pills/jshint.md)

Additionally, [this Node style guide](https://github.com/felixge/node-style-guide) will help you write code that is clear and readable.

## What we will be covering

Node is a whole new environment, so we will be covering __a lot__ of ground in a short space of time. Don't worry if you feel lost at any point, as there is huge amount of information to take in. Also, you are working in a new, unfamiliar paradigm. Where possible, examples linking Node back to more familiar concepts in Ruby will be used.

Here is a broad outline of what we hope to cover this week:

* Setting up your Node environment/starting a project
* Unit testing with `jasmine-node`/Node modules
* Node good practices: `npm`, `grunt`, JavaScript linters
* Feature testing with `webdriver-io`
* Starting a web server with Express
* Building an API with node
* Consuming that API with jQuery

## Setting up your Node environment/starting a project

Please install Node with `brew install node` and follow any additional instructions.  Note that this can cause problems if you already have a node version manager (e.g. n, nvm, `nodenv`) installed.  Please contact a coach or alumni helper if you are having trouble with your node install. Please refer to :pill: [npm](https://github.com/makersacademy/course/blob/main/pills/npm.md) :pill: when setting up your project.



Create a new directory for the project - for this example, let's call it '/starting-node'.

Navigate into the directory and run `npm init` and follow the on-screen instructions, hitting enter every time. You should generate the following package.json:  

`package.json`  
```json
{
  "name": "starting-node",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
```

Interesting, but not very useful. Let's start adding some testing tools so we can start playing with Node.  

## Unit testing with `jasmine-node`/Node modules

At this point, it's a good idea to create a `.gitignore` file and add `node_modules` to it, as we don't want to add our local dependencies to Git, and ultimately to Github.

Next, install `jasmine-node` (which is exactly what you think it is!), first locally to your `dev-dependencies` (`npm install --save-dev jasmine-node`), then, if you want, install it globally (`npm install -g jasmine-node`).

Now we can start doing TDD in Node. Modify the `scripts` section of your `package.json` as follows:

`package.json`  
```json
  "scripts": {
    "test": "node_modules/jasmine-node/bin/jasmine-node spec/ --verbose"
    },
```

We can now run our tests using the command `npm test`. `jasmine-node` has to be told which folder to look in, and will automatically detect any files ending in `*Spec.js`. Also, the `--verbose` flag means that we can see the spec list every time we run our test suite. Let's write a failing test, in this case for a hypothetical bowling scoring program:

`spec/gameSpec.js`
```javascript
describe('Gutter game', function(){

  const game = new Game();

  it('Scores 0 on a gutter game', function(){
    for(let i = 0; i < 20; i++){
      game.roll(0);
    }
    expect(game.score).toEqual(0);
  });
});
```

As usual, we can begin to try to pass this test by creating the file `src/game.js` and creating a Game function (equivalent to a Ruby class):

`src/game.js`
```javascript
function Game(){

}
```

We will also need to require it at the top of the spec file:

`spec/gameSpec.js`
```javascript
const Game = require('../src/game');
```

*(if that `require` seems a bit strange, all will be explained...)*

However, if we run `npm test`, we will get the following useful error, which will not change whatever we do to `game.js`:

```shell
TypeError: object is not a function
```

Thanks JavaScript. To explain this one, we need to take a brief sidestep and understand one of Node's key concepts: Node modules.

### Node modules

One of Node's guiding principles is that your app should be made of many small modules, each of which does one thing very well. This encourages code re-use, unit testing and decoupled architecture. Sound familiar? These are all concepts that you have encountered in Ruby & Unix and are important elements of writing good code.

So how does this all work in practice? The main difference between Ruby and Node is that Node requires you to explicitly declare what parts of your module are accessible to other modules. So, with our example above, we can make the test pass by assigning our Game function to `module.exports`:

`src/game.js`
```javascript
function Game(){

}

module.exports = Game;
```

Now we should expect the following error:

```shell
TypeError: Object #<Game> has no method 'roll'
```

Awesome! Now our spec can see our Game module. Let's continue fixing the errors:

`src/game.js`
```javascript
function Game(){

}

Game.prototype.roll = function(){

}
```

Next error:

```shell
Expected undefined to equal 0.
```

And the fix:

`src/game.js`
```javascript
function Game(){
  this.score = 0;
}
```

...and we should finally have a passing test! High-five your pairing partner and celebrate how fun, obvious and easy testing in Node is*.

_*compared to wrestling a lion._

## Tasks:

* Try repeating the above steps from memory
* Try to convert one of your existing front-end Javascript projects to `jasmine-node`, remembering to use `module.exports` and `require` correctly. Some good project to try converting are Boris Bikes or airport, as they have lots of moving parts that you'll need to fit together.  
* Research how to export multiple functions from a module. Bear in mind that you should not use this technique to export multiple functions that require state - if you find yourself doing this, you probably need a new module.

### Further resources
* [jasmine-node](https://github.com/mhevery/jasmine-node)  
* [Understanding module.exports in Node.js](http://www.sitepoint.com/understanding-module-exports-exports-node-js/)
* [Intro Video by Spike](https://www.youtube.com/watch?v=4J3PCKjRH-8)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=node/intro_to_node.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=node/intro_to_node.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=node/intro_to_node.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=node/intro_to_node.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=node/intro_to_node.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
