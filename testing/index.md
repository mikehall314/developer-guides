## Testing Your Code

Automated software testing offers developers and other stakeholders confidence
that the programs we create function as expected. There are two parts to
software testing:

1. Does the program behave the way we expect it to behave?
2. Does the program not behave the way we do not expect it to behave?

The second of these parts is generally agreed to be the more difficult.

Good software tests should consider:

- **Correctness**: Does the program meet the specified requirements?
- **Robustness**: Does the program respond correctly to all kinds of inputs?
- **Reliability**: Does the program function under required conditions?

# How to test software

It is expected that all new PRs should be accompanied by matching tests. New
features should include tests to offer confidence the feature is correctly
implemented. Bug fixes should include tests to prevent the bug from re-occuring
(a regression test).

The test suite will be run automatically for all new PRs and must pass before
the patch can be merged. It is also good practice to run the test suite locally
before you push.

- [Unit Testing](unit.md)
- [Testing Box Model](box.md)
- [Know your Framework](framework.md)
