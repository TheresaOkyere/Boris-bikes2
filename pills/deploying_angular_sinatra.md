# Deploying your Sinatra / Angular application to Heroku

Deploying an Angular app that is hosted on a Sinatra backend can be somewhat frustrating. The reason being that Heroku will either assume that you are deploying a Node application and therefore ignore your Sinatra server, or it will install a ruby app but fail to run npm - therefore ignoring all your npm and bower components.

To get around this, follow these steps:

1. Move your bower_components directory to public/bower_components
2. Create a `.bowerrc` file in the top level of your application, and add the following text to it:
  ```
  {
    "directory": "public/bower_components"
  }
  ```
3. Add a buildpack to your Heroku env variables like so: ``` heroku config:add BUILDPACK_URL=git://github.com/qnyp/heroku-buildpack-ruby-bower.git#run-bower ```
4. Push to Heroku
5. Profit!

# Background reading
* [Heroku Buildpacks](https://devcenter.heroku.com/articles/buildpacks)
* [Bower Configuration](http://bower.io/docs/config/)
* [Deploying Sinatra plus Angular to Heroku (gist)](https://gist.github.com/giusepped/a7196e3ec7b0946b9121)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=pills/deploying_angular_sinatra.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=pills/deploying_angular_sinatra.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=pills/deploying_angular_sinatra.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=pills/deploying_angular_sinatra.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=pills/deploying_angular_sinatra.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
