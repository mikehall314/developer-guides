# Emergencies

Sometimes there are emergency PRs that must pass through the entire code review
process as quickly as possible.

## What Is An Emergency?

An emergency PR would be a **small** change that: allows a major launch to
continue instead of rolling back, fixes a bug significantly affecting customers
in production, handles a pressing legal issue, closes a major security hole,
etc.

In emergencies we really do care about the speed of the entire code review
process, not just the [speed of response](speed.md). In this case _only_, the
reviewer should care more about the speed of the review and the correctness of
the code (does it actually resolve the emergency?) than anything else. Also
(perhaps obviously) such reviews should take priority over all other code
reviews, when they come up.

However, after the emergency is resolved you should look over the emergency PRs
again and give them a [more thorough review](looking-for.md).

## What Is Not An Emergency?

To be clear, the following cases are _not_ an emergency:

- Wanting to launch this week rather than next week (unless there is some actual
  hard deadline for launch).
- The developer has worked on a feature for a very long time and they really
  want to get the PR in.
- It is the end of the day on a Friday and it would just be great to get this PR
  in before the developer leaves for the weekend.
- A manager says that this review has to be complete and the PR checked in today
  because of a soft (not hard) deadline.
- Rolling back a PR that is causing test failures or breaking the build.

And so on.

## What Is a Hard Deadline?

A hard deadline is one where **something disastrous would happen** if you miss
it. For example:

- Merging your PR by a certain date is necessary for a contractual obligation.
- The product will completely fail in the marketplace if not released by a
  certain date.

Most deadlines are soft deadlines, not hard deadlines. They represent a desire
for a feature to be done by a certain time. They are important, but you
shouldn’t be sacrificing code health to make them.

If you have a long release cycle (several weeks) it can be tempting to sacrifice
code review quality to get a feature in before the next cycle. However, this
pattern, if repeated, is a common way for projects to build up overwhelming
technical debt. If developers are routinely submitting PRs near the end of the
cycle that "must get merged" with only superficial review, then the team should
modify its process so that large feature changes happen early in the cycle and
have enough time for good review.
