# Developer Tooling

For the most part, the environment you develop in is a matter of personal
choice. However, there are a few tools which you are required to use to help
your work cohere with the rest of the team.

## Prettier

We use `prettier` for code formatting. You should ensure that the code editor
you use has a plugin for `prettier` which is configured to run on save. We have
better things to do than argue about code style, so we delegate `prettier` to be
the ultimate arbiter on any matter of style.

Ensure your code editor is configured to use the `prettier` instance which is
bundled with the project, rather than some instance which may be bundled with
the editor or plugin, so we don't have different instances switching the code
formatting back and forth over a long period of time.

## ESLint

We use `eslint` to perform static analysis on our code, detecting early bugs,
and warning developers away from language features which are commonly misused or
misunderstood. As with `prettier` you should ensure that your code editor has
some `eslint` plugin installed and configured to detect code issues while you
work.

Your code should pass `eslint` without errors or warnings. If there is a
compelling reason to use a feature which `eslint` cautions against, you may
disable `eslint` checking for that line or few lines, but you should also
include a comment explaining why that was the correct choice.

## Gitleaks

We use `gitleaks` to detect the accidental inclusion of security and
authentication tokens in our codebase. You should ensure that `gitleaks` is
installed; we have a commit hook configured to run gitleaks on every commit and
this hook will fail without gitleaks installed.

[Home](../README.md)
