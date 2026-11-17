---
name: sendmode
description: Entry point for any non-trivial task. Routes to a playbook and sets the operating defaults — go deep, parallelise, prove it against the real artifact, carry it to merged. Use at the start of anything bigger than a one-line edit.
---

# sendmode

Entry skill. Capable model, trusted operator. *Send* = all the way, no hanging.

Invoke as `/sendmode`, or it triggers on any non-trivial task. **It's a mode, not a one-shot:** once engaged, the defaults below govern the whole session until you override them.

## Defaults (override only if the task says so)

- **Full send.** Code → verify → PR → merge, no approval stops. Confirm only irreversible / out-of-repo acts: force-push a shared branch, push to a remote you don't own, destructive ops on non-local data, deleting user data, prod deploys, spending money.
- **Fearless parallelism.** Independent slices → `swarm`. Competing approaches → `arena`. Every non-trivial diff → `interrogate`. Keep bulk work off-thread → `guard-the-context-window`.
- **Prove it works.** Runtime evidence on the real artifact → `prove-it-works`.
- **Never block.** Proceed and present → `never-block-on-the-human`.

## Route

| Task | Playbook |
|---|---|
| how / why code works | `investigation` |
| broken behavior | `bug-fix` |
| measured slowness | `perf` |
| new / changed behavior | `feature` |
| behavior-preserving cleanup | `refactoring` |
| settle a design question | `prototype` |
| pixel-exact UI | `visual-parity` |
| drive a PR to merged | `autopilot-full` |
| resume another agent's work | `session-pickup` |
| multi-day effort | `orchestrate` |
| new project, no stack yet | `kickoff` |

Open a todo list from the chosen playbook's steps, then run it. Load the principle skills it names. Stay in mode across follow-ups — don't drop the defaults between turns.
