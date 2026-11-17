---
name: blast-radius
description: Find what else a change could break, backed by running code — not a guess. Use before a change to shared or load-bearing code.
---

# blast-radius

Before you touch it, find everything that leans on it.

- Find all callers and dependents — search, don't assume. Include dynamic/indirect uses.
- For each, decide: unaffected, needs updating, or needs testing.
- Confirm the risky ones against the running system, don't reason in the abstract.
- Output: the list, grouped by risk. Now the change is informed, not blind.
