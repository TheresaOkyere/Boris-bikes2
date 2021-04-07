# Walkthrough - FizzBuzz in JavaScript

[Back to the Challenge](../fizzbuzz_in_javascript.md)

If you struggled and clicked through before attempting a complete solution of your own, here is a step-by-step walkthrough: :pill: [JavaBuzz pill](/pills/javascript&JasminePill.md)

Here is one possible TDD implementation of FizzBuzz, after refactoring - if yours looks different (it will!) discuss the differences with your pair partner.

- What did you start by testing?
- Did you directly translate your Ruby version or did you TDD from scratch?
- When/why did you refactor your code?
- Did you use `beforeEach` to set up your object?
- Did you use nested `describe` blocks to organize your tests?

```javascript

// spec/fizzBuzzSpec.js

describe('FizzBuzz', () => {

  let fizzBuzz

  beforeEach(() => {
    fizzBuzz = new FizzBuzz();
  });

  describe('multiples of 3', () => {
    it('fizzes for 3', () => {
      expect(fizzBuzz.play(3)).toEqual('Fizz');
    });

    it('fizzes for 6', () => {
      expect(fizzBuzz.play(6)).toEqual('Fizz');
    });
  });

  describe('multiples of 5', () => {
    it('buzzes for 5', () => {
      expect(fizzBuzz.play(5)).toEqual('Buzz');
    });

    it('buzzes for 10', () => {
      expect(fizzBuzz.play(10)).toEqual('Buzz');
    });
  });

  describe('multiples of 3 and 5', () => {
    it('fizzbuzzes for 15', () => {
      expect(fizzBuzz.play(15)).toEqual('FizzBuzz');
    });

    it('fizzbuzzes for 30', () => {
      expect(fizzBuzz.play(30)).toEqual('FizzBuzz');
    });
  });

  describe('all other numbers', () => {
    it('1 for 1', () => {
      expect(fizzBuzz.play(1)).toEqual(1);
    });

    it('11 for 11', () => {
      expect(fizzBuzz.play(11)).toEqual(11);
    });
  });
});

// src/fizzBuzz.js

class FizzBuzz {

   _isDivisibleBy(divisor, number) {
        return number % divisor === 0;
   }
   
   play(number) {
     if (this._isDivisibleBy(15, number)) {
        return 'FizzBuzz';
     } else if (this._isDivisibleBy(5, number)) {
        return 'Buzz';
     } else if (this._isDivisibleBy(3, number)) {
        return 'Fizz';
     } else {
        return number;
     }
   }
}


```

Printing the numbers from 1-100 (in the console):

```javascript
let fizzBuzz = new FizzBuzz();

for (let i = 1; i <= 100; i++) {
  console.log(fizzBuzz.play(i));
}
```

[Forward to the Challenge Map](../README.md)

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=thermostat_es6/walkthroughs/fizzbuzz_in_javascript.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=thermostat_es6/walkthroughs/fizzbuzz_in_javascript.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=thermostat_es6/walkthroughs/fizzbuzz_in_javascript.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=thermostat_es6/walkthroughs/fizzbuzz_in_javascript.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=course&prefill_File=thermostat_es6/walkthroughs/fizzbuzz_in_javascript.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
