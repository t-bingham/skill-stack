---
name: sequence-verifiable-units
description: Break work into small steps that can each be verified and committed on their own. Every commit leaves the tree green. Use on any task bigger than a single change.
---

# sequence-verifiable-units

Small, provable steps. Never a pile of half-done.

- Each step compiles, passes, and could ship on its own.
- One logical change per commit. If the message needs "and," split it.
- Order so dependencies land first; nothing depends on a later step.
- Verify each unit before the next (see `prove-it-works`). A broken middle step is a broken build.
