# Unit Tests

Unit tests are often the foundation of any effort to test a software system.
"Unit" in this case refers to a "unit of work" - typically a single function or
perhaps several methods of the same class. These "units" will be called at
various times by the rest of the application, and our unit tests should test the
behaviour of that unit.

The nature of the unit test will depend upon what we expect the unit to do. A
unit could:

- Modify the state of the system
- Call into some other unit or API
- Return some value or throw some exception

Therefore, we want our tests to be able to call into the unit and then assert
that the state was modified, an expected value was returned, or the required API
called.

## Single Responsibility

A good unit test should test **one specific thing**.

It can be tempting, especially in cases where a test requires significant setup,
to test several things at once but this can make it more difficult to identify
the source of an error when a specific test fails.

Similarly, each thing should be **tested only once**. Testing the same behaviour
multiple times only forces you to update multiple tests if and when that
behaviour changes.

Avoid making unnecessary assertions and examine only the specific behaviour
you're testing. Asserting things which are also asserted elsewhere will increase
the number of failures when something breaks, without improving test coverage.
Unit tests do not have to observe every single thing the code does.

## Write your code to be tested

You will find it much easier to write effective and useful tests if your code is
written with testing in mind. This means you should encapsulate functionality to
allow each unit to be tested independently. Poor encapsulation will result in
many overlapping tests and so failures in one unit will cascade and cause
failures everywhere.

If your code does not lend itself to being easily tested, consider refactoring
or rearchitecting the code.

## Orthogonal testing

Good unit tests should be independent of each other. The correct function of one
test should never depends on the execution of another test. This means we must
to mock external services and state so that tests cannot influence each other.

## Setup Code

Avoid using common setup code for tests which are not related. This makes it
more difficult for anyone reading your tests to understand which assumptions and
preconditions your test actually relies on.

It's often preferable to run the setup code for each test as part of that test,
unless you're testing a group of similar units which **all use the same setup**.

## Naming Conventions

Your unit tests should be named consistently and clearly, describing the
**subject** of the test, the **context** of the text, and the expected
**behavior** of the unit. For example, a test which ensures a ticket purchase
will fail when the product is sold out might be:

```js
describe('PurchaseController', () => {
  describe('when sold out', () => {
    it('should refuse sale', () => {
      // Your test code here
    });

    it('should notify metrics endpoint', () => {
      // Your test code here
    });
  });
});
```

## Avoid Commenting Out Tests

Tests may be commented out because they're failing, because they're producing
false negatives, or because they are slow. None of these are good reasons to
comment or disable a test. Rather than comment or disable, you should fix the
test or remove it from the test suite altogether.

## Using logic in tests

One common error in poor unit tests is to reproduce the functionality of the
unit within the unit test. For example:

```js
// 😞
function sum(a, b) {
  return a + b;
}

it('should sum 2 + 2 = 4', () => {
  const v = sum(2, 2);
  expect(v).toBe(2 + 2);
});
```

Clearly this is a trivial example, but the principle should be clear. The unit
test merely recreates the logic of the unit; if one misbehaves then both will
misbehave. It is better to statically define the expected result:

```js
// 😃
function sum(a, b) {
  return a + b;
}

it('should sum 2 + 2 = 4', () => {
  const v = sum(2, 2);
  expect(v).toBe(4);
});
```

This also extends to the use of control structures in unit tests, such as ifs
and loops. Control structures and other logic in our tests can obscure the flow
of the test, and may lead to accidentally sharing state.

## Don't test third party code

The purpose of unit testing is to verify the behaviour of **our code**. Testing
code which does not belong to us is a waste of time.

```js
// ☹️
function getItems() {
  const items = getItemsFromDb();
  return lodash.sortBy(items, 'date');
}

// All we're doing is testing lodash!
it('should sort by date', () => {
  const sorted = getItems();
  expect(sorted).toEqual([{ date: '2021-01-01' }, { date: '2021-01-02' }]);
});
```

Next: [Testing Box Model](box.md)
