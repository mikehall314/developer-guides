# Filing Bug Reports

> “The point of writing a bug report is to get bugs fixed”
>
> – Cem Kaner, Florida Institute of Technology

Developers will often have to interact with bug reports. This includes both
reading bug reports to assess, triage, or estimate an issue, and writing bug
reports for bugs discovered over the course of development.

Bug reports which are well written and easy to understand will have a greater
chance of getting fixed, so fixing bugs depends upon how effectively you can
make bug reports.

Not every Jira ticket is a bug report, of course, but many of these principles
can also be applied to feature tickets.

## Provide sufficient pertinent information

> "Everything should be made as simple as possible, but no simpler"
>
> - Albert Einstein (sort of)

It is essential for a good bug report to contain enough pertinent information
about the bug to be useful, without including so much information as to he
unhelpful.

### Poor Bug Reports

- "Homepage doesn't work"
- "There is a bug on the catalog page, please fix"

Neither example here provides enough information about what the bug actually is.
A developer receiving these bug reports will have to spend a significant amount
of time investigating what the bug report means before they are able to tackle
the bug itself.

- "The FizzBuzz service unexpectedly returns 204"
- "The FOOBAR environment variable should be set to `ON` in production"

These reports may contain enough information about the bug itself, but provides
little context about _why_ these are bugs. Why is status 204 a problem? What
should the status be? What is the rationale for that? What does the FOOBAR
environment variable do and why is it being `ON` important in production?

Without a wider context, the developer is left either blindly patching a problem
they do not understand, or will have spend time investigating the context before
tackling the bug.

## What makes a great bug report?

### Title

The title of the bug report should be short and specific. Your aim is to clearly
summarise the issue, which will make it easier to spot and merge duplicates
later. Avoid noise words and clutter.

### Description

You don't need to write an essay about the problem. A short summary, providing
background context about the bug, and steps on how to reproduce the bug should
be enough.

The developer reading your bug report should be able to understand what the bug
is and why that behaviour is undesirable, just from reading your report. Lack of
clarity will lead to misunderstandings, which will delay the patching of the bug
and slow development overall.

## Voice and Tone

It's worth remembering that your fellow developers are human beings. The
language and the tone you choose for a bug report can make a big difference. Bug
reports written in an accusatory or commanding tone can make people feel
defensive.

You should not assume that the developer has made a mistake, or seek to assign
blame. This is unhealthy for the morale of the team and can create an unpleasant
working environment.

The responsibility for the quality of the code lies with the entire team, and
your language should reflect that. Using plural pronouns (we, our) can make a
big difference.

Bad: "Steven's Borglet worker has broken again"

Good: "Our Borglet worker is still throwing intermittently"

## Example

_[BE] Borglet Service: Status should be 201_

_The HTTP spec recommends the use of code 201 to indicate a resource has been
created. Our Borglet API currently returns 200 OK in response to a `/create`
request. We should amend to return 201, per the spec._

This report is concise, describes what the bug is, and where it is located. It
describes the desired result of the fix, and provides a rationale for why that
is better.

[Home](../README.md)
