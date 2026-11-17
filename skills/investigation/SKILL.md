---
name: investigation
description: Playbook for read-only questions about how or why code works. Answer from the running system and the source, not guesses. Use when the task is to understand, not change.
---

# investigation (playbook)

1. State the exact question in one line.
2. Find the real code path — search, don't assume. Route wide reads to a subagent (`guard-the-context-window`).
3. Confirm against the running system where you can: log it, run it, read the actual output.
4. Answer with evidence — file:line and observed behavior. No change, no PR.
