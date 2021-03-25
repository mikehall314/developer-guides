# Application Logging

In maritime history, the ship's logbook was used to make regular records of a
vessel's position, speed, and heading, alongside other contextual data such as
the wind speed and the weather.

In the event of an official inquiry, the logbook would allow officials to
reconstruct the course of the ship and a timeline of events. In the worst case,
where a ship sinks, a recovered logbook would be vital in determining what
happened.

## Software Logs

Software application logs serve a similar purpose. In the case of some
investigation, the application log helps us understand what was happening in the
application, and understand why a particular problem occurred.

When considering what and when to log, we should be mindful of this purpose and
ensure the logs we provide are useful for reconstructing the state of the system
during a post-mortem.

## What makes a good logline?

A good logline is designed with consideration to four key factors.

1. What is the purpose of this logline? Is it a debugging message that should be
   deleted before committing? Is it meant to notify of some change in the state
   of the system? Is it meant to record that an event has occurred? Does it
   contain enough information to be useful for its purpose?

2. What is the context of the data? Commonly, we record the date and time of a
   log entry, but there are other contextual factors to consider. Is it useful
   to log the ID or hostname of the instance? Would it be useful to record the
   origin of an event or request?

3. How important is this logline? Are we logging because we have detected some
   security breach? Or just because the garbage collector ran? These events have
   very different levels of importance! Log with the appropriate level for the
   message and ensure important loglines are easily identifiable.

4. How will people read my logs? Who do you expect to be reading these logs, and
   how will they consume them? If you’re expecting these logs to be processed
   e.g., by Splunk - or even just `grep` - ensure that you format the message so
   those tools work well with your logs. Can someone quickly filter to see every
   time there was an error? Or every time a user authenticates? Can you make it
   easier for them to do that?

## Good reasons to emit a logline

We can often fall foul of logging too much or too little. When emitting a
logline, we need to be sure we are doing it for a good reason and tailor it for
the intended audience.

### What is happening

Good logs should record which actions are being taken by the system, and what
the results of those actions were, including any exceptions. This will help
system administrators and engineers understand what an application is doing.

### How we got here

Tracing logs record changes to the state of a system over time, so engineers
debugging the system later can reconstruct the execution path which led to that
state. Did the user initiate an action? Was it a message from another service?
Was it a scheduled event? How has the state of the system changed as a result of
this event? Good logs can help answer these questions.

### Is everything okay?

Audit logs verify a system is functioning the way we expect, and enable someone
auditing our system to accurately understand its function. If a user requests
the creation of an asset, does the log also show an asset subsequently created?
If a team member is removed from a project, does the log also show the project
updated to reflect that? Good logs are self-consistent.

## Cruft and noise

There are several reasons we have noisy logs. We have all accidentally committed
leftover debugging statements, or a huge object which swamps other messages.
Cruft in our logs makes them difficult to follow; when so much of the data is
noise it’s difficult to pick out the useful parts.

One common source of noise is stack traces. A stack trace is useful for
engineers debugging a problem, but for most other readers they are just noise.
Before logging the full stack trace of an exception, consider if it makes sense
to do so. It is useful to see the full trace for a
`throw new UserNotFoundException();`? Or would logging the error message be
sufficient?

## Personal data

The handling of personally identifiable information (PII) is the subject of
strict legislation at regional, national, and international levels, for example,
CCPA or GDPR. While careful and robust data handling procedures are in place in
most companies now, log files can be overlooked. If we aren’t paying close
attention, we could be accidentally dropping PII into our logs in plain text.
PII, especially access tokens and plaintext passwords, should always be redacted
before being emitted to the log.

## TLDR

1. Consider your reader. Who is this log for? Does it give them data they can
   use?
2. Avoid personal data. Redact tokens, passwords, and other key PII before
   logging.
3. Is there a good reason for this log? Are you providing useful information?
   Avoid noise and cruft.
4. Is there a good reason we haven't logged? Our colleagues will be relying on
   our logs to improve the product. Empty log files tell them nothing at all.

[Home](../README.md)
