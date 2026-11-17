---
name: orchestrate
description: Playbook for a multi-day or multi-stream effort run by one coordinator with subagent fleets. Plan the streams, delegate, integrate. Use for work too big for one linear pass.
---

# orchestrate (playbook)

1. Split the work into independent streams with clear interfaces between them.
2. One coordinator holds the plan and the integration points; it doesn't do the grunt work.
3. Delegate each stream to a worker (`swarm` for parallel slices); each returns a summary, not a dump (`guard-the-context-window`).
4. Integrate as streams land; keep the main build green throughout.
5. Track state so the effort survives a restart (`multi-phase-plan`).
