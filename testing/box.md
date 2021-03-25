# Testing Box Model

Historically, software tests have been divided into **black-box** testing, and
**white-box** (or clear-box) testing. The principle differentiator being the
approach we take when designing the test.

## Black-box Testing

Black-box or functional testing treats the inner workings of each unit as
unknown. Our tests may only examine the inputs and outputs of the box to see if
they meet the required specification for the unit - we do not assume anything
about the internal implementation of the unit.

Effective black-box testing requires our code units to be thoroughly specified,
so we understand what the expected outputs should be from a given set of inputs.
A signficant advantage is that tests are decoupled from the internal
implementation. Even a major refactor will not break the tests, so long ass the
new implementation still meets the specified requirements. However, since tests
are written without knowledge of the implementation, there may be corner cases
or errors which the tests miss.

## White-box Testing

In white-box testing, testers aim to test the internal structure of a unit
rather than just the interface exposed to the user.

Effective white-box tests will test each possible path through a unit's code,
ensuring the program behaves as expected in all possible scenarios, or at least
the most common scenarios. White-box testing does mean the tests are tightly
coupled to the implementation, and will break if the code is refactored.

## Which should I use?

Unit-testing is typically done with a white-box approach, but black-box tests
can also be valuable when the expected functionality of a code unit is well
specified.

Black-box testing becomes more important when looking at integration tests and
end-to-end testing, where it would be impractical or impossible to test every
possible code path through every code unit at the same time.

Next: [Know Your Framework](framework.md)
