# Yelp

**Completion time - 1 week**

![Yelp screenshot](https://github.com/makersacademy/course/blob/master/images/yelp.jpg)

This week's project is a clone of [Yelp](http://www.yelp.co.uk). The goal is to introduce you to Rails, focusing especially on:

* Creating Rails applications
* The structure of Rails apps (MVC, the router, helpers)
* TDD in Rails, with RSpec & Capybara
* Associations
* Validations
* AJAX in Rails

**Contents**

Model View Controller (MVC) is an architectural pattern for dividing up concerns in an application. The concerns in Rails are separated thus:

- A '**M** odel layer' for the business logic of an application, wrapped in classes and communicating with the database via Rails' ORM, ActiveRecord
- A '**V** iew layer' for presenting information, and _small_ presentational logic
- A '**C** ontroller layer' for messaging between the model layer and the view layer. Routes are managed by the Rails Router.

Please see this [diagram](http://images.thoughtbot.com/ember-rails-terminology-differences/rails.png). As we go through building Yelp you'll see how Rails works in terms of Models, Views and Controllers.

## Version 1 - MVP

For the initial version we want to duplicate the core functionality of Yelp - users should be presented with a list of restaurants which they can leave reviews for.

Remember to drive the addition of all features using feature tests, and unit tests when needed.

### V1 Specification

- Visitors can create new restaurants using a form, specifying a name and description
- Restaurants can be edited and deleted
- Visitors can leave reviews for restaurants, providing a numerical score (1-5) and a comment about their experience
- The restaurants listings page should display all the reviews, along with the average rating of each restaurant
- [Validations](https://github.com/makersacademy/course/blob/master/walkthroughs/validations.md) should be in place for the restaurant and review forms - restaurants must be given a name and rating, reviews must be given a rating from 1-5 (comment is optional)

## Version 2 - User login

Although our initial version serves its purpose - it's limited in a few respects. Any visitor to the site can freely add, edit or delete. We also have very few options to track or constrain the visitors to our site.

We can solve both of these problems by adding a user login system, as we did with Bookmark Manager. This time though, you should use a popular gem - [Devise](https://github.com/makersacademy/course/blob/master/walkthroughs/devise.md) - to accelarate the implementation of our user system.

### V2 Specification

* Users can register/login

* Some indication should be given on the page (as part of the layout) whether the user is currently logged in, along with links to the available actions (i.e. Logout/Edit account is signed in, otherwise Sign In/Sign Up)
* The email address of the reviewer should be displayed as part of the review
* *Optional* - Users can't review a restaurant which they created
* *Optional* - Users can log in through Facebook, Twitter, Github or another external service

## Version 3 - Setting limits on users

Although our version 2 serves its purpose - it's limited in a few respects. First any user can freely create, delete or edit restaurants. Additionally, a user can leave multiple reviews for the same restaurant - making it easy for restaurant scores to be skewed.

### V3 Specification

* A user must be logged in to create restaurants
* Users can only edit/delete restaurants **which they've created**
* Users can only leave **one review per restaurant**
* Users can delete their own reviews


### Further challenges (OPTIONAL)

Finally, let's focus on uploading images, and creating a better user experience. This will introduce us to Amazon S3, Rails helper methods and using AJAX in conjunction with Rails.

> A helpful gem for uploading files is [Carrierwave](https://github.com/carrierwaveuploader/carrierwave) (which handles uploads) combined with [Fog](https://github.com/fog/fog) (which handles connection to Amazon S3). Heroku does not handle locally-uploaded images properly: so you need to put them somewhere else.

### Further specifications

* Currently, when writing a review, we have to go to a separate page and trigger a page refresh. Migrate the functionality to happen asynchronously with AJAX. We'll also have to set up [Poltergeist](https://github.com/teampoltergeist/poltergeist) to enable us to run JS-enabled tests.
* Create a helper method to allow ratings and average ratings to be displayed as stars (e.g.) rather than numbers
* Use SCSS to enhance the overall design of the site
* Refactor your more complex views to use partials
* Add the ability for users to add an image to a restaurant

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=rails/yelp_project_specification.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=rails/yelp_project_specification.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=rails/yelp_project_specification.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=rails/yelp_project_specification.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=rails/yelp_project_specification.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
