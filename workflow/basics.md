# How it Works

Git is a distributed version control system, which means that no single node
inherently contains the canonical version of the codebase. However, for our
purposes it is useful to nominate one node as containing _the_ canonical
version. In truth, this node is no different to any other, but we can treat it
like it is.

In our case the canonical origin is GitHub.

Developers push and pull their code from GitHub, which maintains two special
branches, `main` and `develop`.

## The Main Branch

The branch named `main` will always contain a production-ready version of the
project. Typically, it will match the version of the application currently in
production. The only time where this may not be true is during a release cycle,
when it will contain the next edition of the project as it undergoes QA testing.

Typically, you would not expect to branch from `main`; the exception is for the
creation of a [hotfix](hotfixes.md). Otherwise, new features and non-urgent bugs
should be branched from `develop`.

## The Develop Branch

The branch named `develop` contains the next edition of the project, including
new features and bug fixes. [Features](features.md) and non-urgent bugs are
usually branched from `develop`, and merged back to `develop` when complete.

Feature branches should have code frequently committed, and changes frequently
pushed. Once a the feature is complete, or if you just want some feedback on
your code, you should open a [pull request](../pulls/index.md).

The latest version of the `develop` branch will be automatically deployed the
`dev` environment, so merging broken code into `develop` will spoil everyone's
day. It is imperative you [avoid breaking the build](dont-break-the-build.md).

## A Push is a Promise

When you push code to the origin you are making a promise about the stability of
that code, and specifically its history.

Code which exists on your own machine may be reworked, revised, rebased, and
merged in whatever ways you see fit, but as soon as your code is _pushed_ you
are vouching for the history of that code to your colleagues.

Once pushed, other developers may be reading your code, suggesting changes, or
otherwise working with it. Not only does a rebased branch require a force-push,
but it can break the work of anyone using that branch.

**Avoid rebasing code you have pushed**.

Next: [Feature Branches](features.md)
