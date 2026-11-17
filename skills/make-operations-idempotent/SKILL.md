---
name: make-operations-idempotent
description: Design operations to converge to the same end state no matter how many times they run or where a partial run stopped. Use for retries, sync, migrations, and anything that can run twice.
---

# make-operations-idempotent

Running it twice should equal running it once.

- Key writes by identity so a retry updates instead of duplicating.
- Make each step check-then-act: skip what's already done, finish what isn't.
- A half-finished run must be safe to re-run from the top.
- Prefer "set to X" over "increment" wherever you can't guarantee exactly-once.
