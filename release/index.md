# Branching Model and Release Process

We current use a continuous deployment model based on GitFlow. GitFlow is a
popular branching model for Git, created by Vincent Driessen. It has fallen in
popularity in recent years, in favour of trunk-based models.

However, GitFlow has several benefits which will be of benefit to the project;
notably the **support for emergency fixes**. These can be used to make an
emergency change, safe in the knowledge that the next deploy will only contain
your emergency fix. There’s no risk that you’ll accidentally deploy new features
at the same time.

### How it Works

Developers push and pull their code from GitHub, which will maintain two special
branches, named `main` and `develop`.

A branch named `main` will nearly always contain a production-ready version of
the project, usually the currently published version. We would branch only
**emergency fixes** from the `main` branch, and merge them back to both `main`
(for a hotfix release) and `develop` (to prevent regression on the next
release). We never create new features from `main`.

A second branch named `develop` contains the next edition of the project. New
features are branched from `develop`, and merged back into `develop` once
complete. Non-urgent fixes are also be branched from `develop`.

## Usual Release Process

The release cycle uses GitHub Actions to automate deployment of the product to
`dev`, `stg`, and `prod`.

### Dev

At any given time, the latest `develop` branch will be deployed to the `dev`
environment. This is an automatic process, which is triggered any time new code
lands in the `develop` branch.

Once a merge/commit is available on the `dev` environment, it should be checked
by it's author to ensure that it works as intended.

### Stg

When the `develop` branch is ready to be moved into production, a PR is raised
to merge `develop` into the `main` branch.

When the code lands in `main`, we automatically tag with a version number, which
is derived automatically by looking at the commit history.

When a new tag is pushed, this triggers a checkout and build of the tagged
version on the `stg` environment.

### Prod

When a `stg` build is completed and tested, we re-point the `latest` tag to
point at the new version. When GitHub Actions detects a change to the `latest`
tag, it will automatically deploy the build `latest` to `prod`.

## Hotfix Release Process

The hotfix is prepared and tested locally, using a branch created from `main`.
When finished, a PR is raised to merge the fix into `main`. When merged, this
will kick off the deploy to `stg` and tag with a version number. The process
proceeds otherwise as described above.

## Rapid Rollbacks

If we need to rollback to a previous version, all we need to do is point the
`latest` tag to a previous version and push it. This will then prompt GitHub
Actions to deploy that version number.
