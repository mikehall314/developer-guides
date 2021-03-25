# Branching Workflow Guide

Our current branching model is based on Gitflow, a model for Git version control
originally
[described by Vincent Driessen](https://nvie.com/posts/a-successful-git-branching-model/).
Gitflow is sometimes seen as a little old-fashioned, but is a good fit for our
deployment model.

## Key Benefits

1. **Clear Branching Strategy** Gitflow provides a clear and organized branching
   strategy. It defines specific branches for different purposes, such as
   feature development, bug fixing, and hotfixing. This structure makes it
   easier for developers to understand and follow a consistent workflow.

2. **Isolation of Features and Releases** The model encourages the isolation of
   new features, and bug fixes in dedicated branches. This helps in keeping the
   main development branch (`develop`) stable while allowing developers to work
   on new features without affecting the main codebase.

3. **Parallel Development** Gitflow allows for parallel development by enabling
   multiple teams or developers to work on different features simultaneously.
   Each feature or bug fix can be developed in its own branch, making it easier
   to manage and merge changes without conflicts.

   Although interruptions are A Bad Thing™, if you are asked to switch from one
   task to another, all you need to do is commit your changes and then create a
   new feature branch for your new task. When that task is done, just checkout
   your original feature branch and you can continue where you left off.

4. **Versioned Releases** The `main` branch is reserved for production-ready
   releases, and version tags are applied to mark specific points in the
   project's history. This makes it straightforward to track and deploy specific
   versions of the software.

5. **Hotfixes for Quick Production Fixes** The model includes a mechanism for
   handling critical production issues through hotfix branches. Hotfixes allow
   developers to address urgent problems in the production environment while
   still following a controlled and versioned release process.

6. **Collaboration** Feature branches make it easier for two or more developers
   to collaborate on the same feature, because each feature branch is a sandbox
   where the only changes are the changes necessary to get the new feature
   working. That makes it very easy to see and follow what each collaborator is
   doing.

7. **Maintenance of a Stable `develop` Branch** The `develop` branch serves as a
   stable integration branch where developers can merge their features for
   testing and preparation for the next release. This helps maintain a clean and
   stable version of the codebase for ongoing development.

   As new development is completed, it is merged back into the `develop` branch
   where it can be automatically deployed to a shared development instance. The
   `develop` branch is always production-ready, which also means releases can be
   created from it without accidentally deploying broken or unfinished work.

## How it works

- [The Basics](basics.md)
- [Feature Branches](features.md)
- [Hotfix Branches](hotfixes.md)
- [Don't Break the Build](dont-break-the-build.md)
