# Feature Branches

Feature branches are used to develop new features and non-urgent for some
upcoming release. When starting development of a new feature or a bug fix, the
target release may well be unknown.

The essence of a feature branch is that it exists as long as the feature is in
development, but will eventually be merged back into `develop` (to definitely
add the new feature to the upcoming release) or discarded (in case of a
disappointing experiment).

## Naming Convention

Branches should clearly identify the relevant JIRA reference, and a short
description of the feature being implemented. e.g.

- `TICKET-123-paypal-integration`
- `TICKET-456-rebuild-headers-file`

JIRA can provide suggested branch names for you automatically, based on the
ticket name and number. You can choose this by selecting 'Create Branch' from
the right hand sidebar, though the names can be verbose if the ticket name is
long. See also [Bug Reports](../bugs/index.md).

## What to include?

A finished feature branch should contain the implementation of the required
feature, including test cases and documentation where appropriate. In the case
of a bugfix, the branch should include a test case for that bug to prevent
regression in future.

Your colleagues will be reviewing your work before it is merged, so you should
aim to make it clear, self-explanatory, and to the standard you would expect to
see from others.

## When to push

You should commit to your feature branch frequently, and push frequently during
development. This affords the opportunity for your colleagues to examine a
work-in-progress, backs your code up to the server, and allows the CI system to
check that your work remains [backward compatible](dont-break-the-build.md).

## What happens next?

When a feature is complete and is ready to be integrated into the `develop`
branch, you should create a [pull request](../pulls/index.md), and ask your
colleagues to review and approve the work.

Next: [Hotfixes](hotfixes.md)
