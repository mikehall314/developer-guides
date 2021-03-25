# Writing good PR descriptions

A PR description is a public record of **what** change is being made and **why**
it was made. It will become a permanent part of our version control history, and
will possibly be read by people other than your reviewers over the years.

Future developers may search for your PR based on its description. Someone in
the future might be looking for your change because of a faint memory of its
relevance but without the specifics handy. If all the important information is
in the code and not the description, it's going to be a lot harder for them to
locate your PR.

## Subject Line

- Short summary of what is being done (aim for 50 characters)
- Complete sentence, written as though it was an order.

Like commit descriptions, PRs should follow the
[Conventional Commits](../commits/index.md) standard.

The **subject line** of a PR description should be a short summary of
_specifically_ **what** _is being done by the PR_, followed by a blank line.
This is what most future code searchers will see when they are browsing the
version control history of a piece of code, so this first line should be
informative enough that they don't have to read your PR or its whole description
just to get a general idea of what your PR actually _did_.

By tradition, the first line of a PR description is a complete sentence, written
as though it were an order (an imperative sentence). For example, say
"**Delete** the FizzBuzz RPC and **replace** it with the new system." instead of
"**Deleting** the FizzBuzz RPC and **replacing** it with the new system." You
don't have to write the rest of the description as an imperative sentence,
though.

## Body is Informative

The rest of the description should be informative. It might include a brief
description of the problem that's being solved, and why this is the best
approach. If there are any shortcomings to the approach, they should be
mentioned.

You should also include and contextual information about the PR. Why does that
problem need to be solved? What is the business values of the PR?

If you include links to external resources consider that they may not be visible
to future readers due to access restrictions or retention policies. Where
possible include enough context for reviewers and future readers to understand
the PR.

Even small PRs deserve attention to detail. Put the PR in context.

## Bad PR Descriptions

"Fix bug" is an inadequate PR description. What bug? What did you do to fix it?
Other similarly bad descriptions include:

- "Fix build."
- "Add patch."
- "Moving code from A to B."
- "Phase 1."
- "Add convenience functions."
- "kill weird URLs."

They do not provide useful information and are not serving the purpose of a PR
description.

## Good PR Descriptions

Here are some examples of good descriptions.

### Functionality change

Example:

> feat: Remove size limit on RPC server message freelist.
>
> Servers like FizzBuzz have very large messages and would benefit from reuse.
> Make the freelist larger, and add a function that frees the freelist entries
> slowly over time, so that idle servers eventually release all freelist
> entries.

The first few words describe what the PR actually does. The rest of the
description talks about the problem being solved, why this is a good solution,
and a bit more information about the specific implementation.

### Refactoring

Example:

> feat: Construct a Task with a TimeKeeper to use its TimeStr and Now methods.
>
> Add a Now method to Task, so the borglet() getter method can be removed (which
> was only used by OOMCandidate to call borglet's Now method). This replaces the
> methods on Borglet that delegate to a TimeKeeper.
>
> Allowing Tasks to supply Now is a step toward eliminating the dependency on
> Borglet. Eventually, collaborators that depend on getting Now from the Task
> should be changed to use a TimeKeeper directly, but this has been an
> accommodation to refactoring in small steps.
>
> Continuing the long-range goal of refactoring the Borglet Hierarchy.

The first line describes what the PR does and how this is a change from the
past. The rest of the description talks about the specific implementation, the
context of the PR, that the solution isn't ideal, and possible future direction.
It also explains _why_ this change is being made.

### Small PR that needs some context

Example:

> feat: Create a Python3 build rule for status.py.
>
> This allows consumers who are already using this as in Python3 to depend on a
> rule that is next to the original status build rule instead of somewhere in
> their own tree. It encourages new consumers to use Python3 if they can,
> instead of Python2, and significantly simplifies some automated build file
> refactoring tools being worked on currently.

The first sentence describes what's actually being done. The rest of the
description explains _why_ the change is being made and gives the reviewer a lot
of context.

## Review the description before merging the PR

PRs can undergo significant change during review. It can be worthwhile to review
a PR description before merging, to ensure that the description still reflects
what the PR does.

Next: [Small PRs](small.md)
