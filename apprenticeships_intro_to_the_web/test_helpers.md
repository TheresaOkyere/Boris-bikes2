# Test Helpers

[Back to the Challenge Map](README.md)

We've implemented two user stories, but our tests are starting to repeat themselves. They're duplicating the same user actions again and again:

- visiting the home page,
- entering names, and
- signing in.

We can use a **helper** to avoid this constant repetition. Helpers are small objects that provide basic functionality that isn't related to the main aim of a program. They are almost always used to DRY up code.

In this challenge, we will DRY up our tests using a **helper**.

### Learning Objectives Covered

In this challenge, you'll DRY up your tests and the helpers that you create will make it easier to write the tests for every subsequent user story.  This is another _best practice_.

### To complete this challenge, you will need to:

- [ ] Make a new file, `spec/features/web_helpers.rb`
- [ ] `require` this file inside your `spec_helper.rb`
- [ ] Define a method inside this file, `sign_in_and_play`
- [ ] Extract code from your two feature tests that:
  - visits the homepage,
  - fills in the fields, and
  - clicks submit
- [ ] Place this extracted code inside `sign_in_and_play`
- [ ] Replace these lengthy lines in your feature tests with a call to `sign_in_and_play`.
- [ ] Explain how these steps improved the quality of your code base

### Resources

- [Helper class (Wikipedia)](https://en.wikipedia.org/wiki/Helper_class)

### [Walkthrough](walkthroughs/test_helpers.md)

[Previous challenge](viewing_hit_points.md) - [Next challenge](attacking_player_2.md)
<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=apprenticeships_intro_to_the_web/test_helpers.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=apprenticeships_intro_to_the_web/test_helpers.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=apprenticeships_intro_to_the_web/test_helpers.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=apprenticeships_intro_to_the_web/test_helpers.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy/course&prefill_File=apprenticeships_intro_to_the_web/test_helpers.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
