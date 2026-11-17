---
name: outcome-oriented-execution
description: In migrations and refactors, converge on the target design directly — no throwaway compatibility shims. Change the callers, then delete the old thing. Use for any migration or large change.
---

# outcome-oriented-execution

Aim at the end state. Don't build scaffolding you'll tear down.

- Decide the target shape, then move everything to it. No parallel old/new paths left standing.
- Migrate callers, then delete the legacy API in the same change — don't leave a compat layer "for safety."
- One real cutover beats a long limbo of both worlds.
- If the change is too big for one cut, sequence it (see `sequence-verifiable-units`) — but each step still lands on the target, not a shim.
