---
name: prove-it-works
description: Done = runtime evidence against the real artifact, not "the diff looks right." The bar for every task. Tests earn their place where they pay; not a ritual.
---

# prove-it-works

Not done until you've watched it work on the real thing.

## Bar
- Run the real artifact: start it, hit the endpoint, drive the UI, replay the broken input.
- Observe user-visible behavior, not a proxy. Assert behavior, not implementation.
- Bug: reproduce first (capture the failing evidence), then show the path passes.
- Perf: measure vs baseline; rule out measurement artifacts before trusting the number.

## Tests
- Write one when it pays: load-bearing, easy to regress, cheap to assert.
- One behavior test beats three implementation tests.
