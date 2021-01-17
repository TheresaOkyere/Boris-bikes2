# Lambdas

Lambdas are closely related to [procs](https://github.com/makersacademy/course/blob/master/pills/procs.md). In fact, they are a special kind of a proc. You can create a lambda using two approaches:

````ruby
my_lambda = lambda {|name| puts "Hello, #{name}!" }
my_lambda = ->(name) { puts "Hello, #{name}!" }
````

Both syntaxes are equivalent. Lambdas are a flavour of [procs](https://github.com/makersacademy/course/blob/master/pills/procs.md) but there are two subtle differences in behaviour.

Firstly, unlike [procs](https://github.com/makersacademy/course/blob/master/pills/procs.md), lambdas have to be called with the right number of arguments, otherwise an error will be thrown.

Secondly, if you use the return keyword inside a lambda, it will return from the lambda, whereas if you use it inside a proc, it will return from the calling context (a method where the proc or a block was defined) if it's available.

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/lambdas.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/lambdas.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/lambdas.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/lambdas.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=pills/lambdas.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
