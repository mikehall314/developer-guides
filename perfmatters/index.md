# Performance

## TLDR

Performance matters.

## Should I care about performance?

Performance and the perception of performance directly impact customer
engagement, traffic and ultimately revenue.

The BBC reports that for every additional second their site took to load they
lost an additional 10% of visitors. Google reports that 53% of mobile sites are
abandoned by customers if pages take longer than three seconds to load. Mobify
reports that every 100ms decrease in homepage load speed worked out to a 1.1%
increase in conversions, amounting to \$380k in additional revenue.

Reports of this sort are common.

## Caching solves this, right?

Customers with a hot cache will always have a better experience than customers
who are coming to the site for the first time, but _every customer has a cold
cache the first time they visit the site_.

We cannot naively rely on service worker or Redis to deliver performance for
just the second, third, fourth page load. If the first page load goes badly, we
may not get a second or third; the case we must optimize for is a cold cache.
Returning customers with a hot cache will simply get a double-quick experience.

## Tools not Rules

Nothing in this documentation should be construed to support micro-benchmarking,
or other pseudoscientific methods of performance optimisation. We have all heard
stories about how loops are faster when you decrement the counter instead of
increment it, or a `while` is faster than a `for` because of some estoteric
reason at the assembler level.

We improve performance, not by slavishly following a set of Holy Performance
Axioms, but by measuring bottlenecks in our code, identifying where the
performance is weak, and then fixing it.

There is no quick fix for performance optimisation, no magic bullet, no
prescriptive solutions. We should be profiling the code, understanding what it
is doing, and fixing actual bottlenecks.

## Network Quality

We are often privileged to be able to develop in ideal conditions, with high
quality hardware, and performant networking; but customers often do not
experience our product in ideal conditions.

They may have poor connectivity at home, because of cheap aluminum cabling. They
may be on the very edge of cell service, using weak 3G or worse. They may be on
a train, switching from mast to mast as they speed by. They may be using a
metered data plan, or roaming, or running low on battery, and will appreciate it
if we limit our use of their cellular radios. **It is lazy to assume that even
an affluent customer always has a performant client.**

[Home](../README.md)
