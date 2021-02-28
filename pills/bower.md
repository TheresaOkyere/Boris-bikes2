#Bower

Bower is a package manager, similar to :pill: [npm](https://github.com/makersacademy/course/blob/master/pills/npm.md) but optimized for the front-end. It can be used in conjunction with Sinatra, Node or Rails, to manage your front-end dependencies.

To begin using bower, you will need to have Node installed.

Then you'll need to install bower, don't forget the -g

```
npm install -g bower
```

Let's check everything is okay, run `node -v` and `bower -v` and make sure they both return a version number.

Now let's get some boilerplate working. Make a new directory, cd into it then run:

```
npm install bower --save-dev
bower init
```

To begin with, you can just choose the defaults (keep hitting return) and you're all good. At the end of the init process you will be shown the bower.json that will be generated for you. It is now possible to install packages, in a similar way to installing Node packages. For instance, to install jQuery:

```
bower install jquery --save
```

The --save will add the package into your bower.json file as a dependency. Then when you clone your repo again you can use `bower install` in exactly the same way as you `bundle install` with Ruby - the bower.json will direct bower to install the components in the correct directory.

Most package managers don't work the same way as Ruby gems - Ruby gems are installed against the project's version of Ruby, JS package managers normally download packages into your local folder. Go ahead and do an `ls` and see what has been downloaded. Be aware that like `node_modules` we don't really want to add `bower_components` to our Github repository - most people consider it bad practice. Because we don't want to commit those dependencies, remember to add `bower_components` to our `.gitignore` file.

## External resources

* [Bower documentation](http://bower.io/)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/bower.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/bower.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/bower.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/bower.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/bower.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
