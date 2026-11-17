---
name: session-pickup
description: Playbook to resume or take over another agent's in-flight work. Rebuild context from the artifacts, then continue. Use when inheriting a branch, PR, or paused task.
---

# session-pickup (playbook)

1. Rebuild context from what exists: the branch diff, commits, PR thread, todo list, notes. Not from memory.
2. Establish the current state — what's done, what's green, what's broken. Run it (`prove-it-works`).
3. Find where it was heading; confirm that's still right.
4. Continue from there in verifiable units. Keep the original credit/authorship.
