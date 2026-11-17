---
name: multi-phase-plan
description: Playbook for work that spans phases or stacked PRs. Sequence the phases, keep each shippable, track state. Use when one change is too big to land at once.
---

# multi-phase-plan (playbook)

1. Break into phases that each land green and add value on their own.
2. Order by dependency; each phase builds on merged work, not a pending branch.
3. For stacked PRs, keep the stack rebased and land bottom-up (`shipping`).
4. Track phase state somewhere durable so the plan survives a restart or handoff.
5. Prove each phase before starting the next.
