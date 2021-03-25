# Know your Framework

When creating great tests, it is useful to have a broad understanding of your
testing framework. This will not only make your tests easier to write, but will
also help reduce the amount of logic in your test cases.

We currently use [Jest](https://jestjs.io/) as our testing framework. Jest is
well-maintained and well-used framework built by Facebook. Though it is focuseed
on simplicity, it has a relatively large API with a wide range of **matchers**
used during verifiation. It also bundles its own **stubbing and spying** library
for mocking underlying APIs.

## Matchers

Matchers are used to make assertions on the state of the system after you have
executed test code. The most common matchers you'll use are probably going to be
`.toEqual()` and `.toBe()`.

`expect(value).toBe(expectedValue)` asserts that `value` is exactly the same
object as `expectedValue`. For primitive values (`Number`, `String`, `Boolean`,
`BigInt`, `undefined`, `Symbol`, `null`) this just means that the values are the
same.

However, for complex types, like `Array`, `Object`, `Map`, `Set` etc, the values
are compared by reference. This means that `value` must be **literally the same
object** as `expectedValue` for the assertion to hold true.

Contrast with `expect(value).toEqual(expectedValue)`, where even complex types
are compared by value. This assertion will hold true so long as `value` and
`expectedValue` serialize to the same type.

These are only two of the many dozens of matchers available in Jest, and it is
worth [familiarizing yourself](https://jestjs.io/docs/expect) with the available
matchers, as they cover a wide variety of use cases.

## Stubs and Spys

Jest also offers functions to create mock implementations of APIs which might be
called by our code unit. These implementations can either **spy** on the API,
recording which calls are made and with which arguments (but otherwise allowing
the API to run as normal), or **stub** the API where calls are intercepted and
we can control what is returned.

It is also worth becoming
[familiar with these functions](https://jestjs.io/docs/mock-function-api)

[Home](../README.md)
