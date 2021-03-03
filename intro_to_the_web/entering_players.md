# Entering Players

[Back to the Challenge Map](README.md)

We have a basic project structure. Let's consider our first User Story:

```
As two Players,
So we can play a personalised game of Battle,
We want to Start a fight by entering our names and seeing them
```

In this challenge, you will allow players to enter their names and see them on-screen.

### Learning Objectives covered
- Use `params` to extract information from a request
- Write a feature test using Capybara
- Pass a feature test using Capybara

### To complete this challenge, you will need to:

- [ ] In `spec/features`, add a new Capybara feature test that expects players to fill in their names (in a form), submit that form, and see those names on-screen
- [ ] Create a `get '/'` route that renders a`index.erb` view with a form
- [ ] Point the `index.erb` form action to a `post '/names'` route
- [ ] Create a `post '/names'` route that uses `params` to render a `play.erb` view that displays the names
- [ ] Pass the feature test you wrote.

### Resources

- [Capybara Cheat Sheet](https://www.launchacademy.com/codecabulary/learn-test-driven-development/rspec/capybara-cheat-sheet)
- :pill: [`params`](../pills/params.md)
- [My First HTML form (MDN)](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Forms/My_first_HTML_form)
- [How are parameters sent in an HTTP POST request? (Stack Overflow)](http://stackoverflow.com/questions/14551194/how-are-parameters-sent-in-an-http-post-request)
- [Relish notes on feature specs with Capybara](https://www.relishapp.com/rspec/rspec-rails/docs/feature-specs/feature-spec)
- [Avoiding False Positives with Capybara and Sinatra](https://blog.makersacademy.com/avoiding-false-positives-with-capybara-and-sinatra-1c827b221001)

### [Walkthrough](walkthroughs/entering_players.md)

[Previous challenge](getting_test_infrastructure_set_up.md) - [Next challenge](post_redirect_get_pattern.md)
<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=intro_to_the_web/entering_players.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=intro_to_the_web/entering_players.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=intro_to_the_web/entering_players.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=intro_to_the_web/entering_players.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=intro_to_the_web/entering_players.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
