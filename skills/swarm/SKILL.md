---
name: swarm
description: Run N parallel workers on different independent slices of one task, then aggregate. Use when work splits cleanly into pieces that don't depend on each other.
---

# swarm

Many workers, different slices, one report.

- Split the task into slices with no shared state and clear interfaces.
- Launch a worker per slice in parallel. Each verifies its own slice (`prove-it-works`) and returns a summary, not a dump (`guard-the-context-window`).
- Integrate the results; resolve interface mismatches at the seams.
- If slices turn out to depend on each other, it wasn't a swarm — re-split or sequence it.
