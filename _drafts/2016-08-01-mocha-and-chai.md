# TDD in JavaScript

## mocha

[mocha](https://mochajs.org/#getting-started)

`npm install mocha`

in package.json

```js
"scripts": {
    "test": "mocha"
},
```

## How to write tests

- SUT - stuff under test
- AAA - arrange / act / assert

From a pure TDD point of view, we should write test first.

### arrange

use `describe` and `it`

describe() is simply a way to group tests in Mocha. Tests can be grouped as deep as necessary.

describe() takes two arguments, the first is the name of the test group, and the second is a callback function.

it() is used for an individual test case. it() takes two arguments, the first is the expression about what the test should do, and a callback function which contains the arrange / act / assert.

- only
- skip

```js
describe("Array", function() {
  describe("#indexOf()", function() {
    it("should return index of first found when the value is not present", function() {
      assert.strictEqual(1, [1, 2, 3].indexOf(2));
    });

    it("should return -1 when the value is not present", function() {
      assert.strictEqual(-1, [1, 2, 3].indexOf(4));
    });
  });
});
```

after run

```js
Array
  #indexOf()
    ✓ should return index of first found when the value is not present
    ✓ should return -1 when the value is not present

2 passing (9ms)
```

setup and cleanup
With its default BDD-style interface, Mocha provides the hooks before(), after(), beforeEach(), and afterEach(). These should be used to set up preconditions and clean up after your tests.

### act

You have an expectation, act is the part to get the calculated value, assert is to compare values or confirm some steps are executed.

in the it, call the functions

time and duration

- slow
- timeout

### assert

By default, [assert in nodejs](https://nodejs.org/api/assert.html) is used.

Or use the BDD style, like [chai](https://www.chaijs.com/) which uses expect(), assert() and should-style assertions.

## Asynchronous

## CLI

`mocha -V`

## chai

Chai has several interfaces that allow the developer to choose the most comfortable. The chain-capable BDD styles provide an expressive language & readable style, while the TDD assert style provides a more classical feel.

[chaijs](http://www.chaijs.com/)

`npm install chai`

### Jest

### Jasmine

### SinonJS

[sinonjs](http://sinonjs.org/)

[sinonjs on devdocs](https://devdocs.io/sinon~7/)

## TDD in TypeScript

`npm install chai mocha ts-node @types/chai @types/mocha --save-dev`

## Resources

[Official](https://mochajs.org/)

[JsDoc](http://usejsdoc.org/)

[unit-testing-nodejs](https://app.pluralsight.com/library/courses/unit-testing-nodejs)

[chai](https://www.chaijs.com/)

[a-quick-and-complete-guide-to-mocha-testing](https://blog.logrocket.com/a-quick-and-complete-guide-to-mocha-testing-d0e0ea09f09d)
