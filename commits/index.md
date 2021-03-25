# Conventional Commits

[Conventional Commits](https://www.conventionalcommits.org/) is a lightweight
standard for writing version control commit descriptions, to help readers of
your commits better understand the intent, scope, and impact of that commit.

Our commit messages should follow Conventional Commits v1.0.0.

## The Structure of a Commit

A commit message should be structured as follows:

> type(optional scope): description
>
> optional body
>
> optional footer(s)

This makes use of the following structural elements, to communicate intent to
other users of this commit.

### Types

There are three principal types of commit.

1. `fix:` a commit of the type **fix** patches a bug in the codebase.
2. `feat:` a commit of the type **feat** introduces a new feature to the
   codebase, but does not introduce any breaking changes.
3. `BREAKING CHANGE:` a commit of the type **BREAKING CHANGE**, introduces a
   breaking API change (one in which requires existing consumers of this API to
   update their integration)

Types other than `fix:` and `feat:` are permitted, for example `docs:`,
`refactor:`, `test:`, where commits are neither fixes nor features. However,
care must be taken not to mislead someone reading the git history as to the
extent and impact of the commit.

### Scopes

An optional scope may be provided to a commit’s type, to provide additional
contextual information and is contained within parenthesis, e.g.
`feat(parser): Add the ability to parse arrays.`

### Description

A description immediately follows the colon and space after the type/scope
prefix. The description is a short summary of the code changes, written as an
_imperative sentence_. e.g.
`fix: Delete the FizzBuzz RPC and replace it with the new system.`

### Body

A longer commit body may be provided after the description, providing additional
contextual information about the code changes, one blank line after the
description. A commit body is free-form and may consist of any number of newline
separated paragraphs.

This may include a brief description of the problem being solved, why this is
the best approach, and any known shortcomings and bugs.

### Footers

One or more footers may be provided after the body. Footers provide a list of
references which are relevant to this commit.

- `See-also: d3adb3ef` to reference another commit id
- `Co-authored-by: J Doe` to reference a contributor to this commit
- `See-also: https://some.relevant.link/some/relevant.post`
- `Fixes: https://link.to.jira/ticket/123`

Footers can also reference just the bug number itself.

- `Fixes: TICKET-123`

### What to avoid

Commit messages are meant to help your colleagues understand the context of your
work, as well as help track project changes between releases, e.g. to assist the
creation of release notes. Commit messages like this provide no context for your
work and are not helpful to the rest of the team, so should be avoided.

```bash
$ git commit -m 'fix'
$ git commit -m 'update variable'
$ git commit -m 'wip'
```

[Home](../README.md)
