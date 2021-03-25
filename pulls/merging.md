# Merging your Pull Request

Once a PR has been approved by colleagues, the next step is to merge it into the
codebase. This is typically done in the GitHub UI. We currently requires that
PRs are squashed before being merged into the `main` branch.

## Squash Commits

A single PR may be made up of several commits, written over a period of hours or
days. There may then be even more commits added during review, as you respond to
feedback from your colleagues.

These commits will be 'squashed' before they are merged into `main`, which is
where GitHub will combine all of the changes made into a single commit, and that
is the commit which is ultimately merged.

When this happens, a new commit message is automatically generated, which is
effectively a concatenation of the messages from each commit being squashed into
this merge. Although this avoids discarding information, it also makes our Git
history harder to read, especially for the purposes of audit and review.

## Keeping a readable Git history

When your commit is finally merged in, you should take the time to rewrite the
final commit message so that it reflects the patch which is finally being
merged. This should be done to the same standard as
[any other commit](../commits/index.md), including a subject line, a description
of what has been changed, and links out to JIRA ticket(s) or other relevant
data.

If the commit messages have been properly written for each of the commits
contributing to the patch, then this should be a straightforward process. If the
final commit has changed significantly from its initial implementation, you may
wish to rewrite the entire commit message from scratch.

Sticking to this standard will mean that anyone reading the `git log` should be
able to see the full and clear context of any specific commit, it's type, it's
scope, and it's limitations - without the additional clutter of artefacts from
the code review process.

Anyone reading `git log --oneline` will be able to see an overview of each
commit, including its type and scope, which can be useful in determining if an
upcoming release has breaking changes, and how best to assign a version number
using the [SemVer standard](../semver/index.md), and preparing release notes.

[Home](../README.md)
