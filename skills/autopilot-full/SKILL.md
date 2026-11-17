---
name: autopilot-full
description: Playbook to take one unit of work all the way to merged, unattended. The default end-to-end run. Use when told to just ship it.
---

# autopilot-full (playbook)

1. Build the change (`feature`/`bug-fix`/`refactoring` as fits).
2. Prove it on the real artifact (`prove-it-works`).
3. Stress-test the diff with a different model (`interrogate`).
4. Open the PR (`file-pr`), babysit to green (`babysit-pr`).
5. Merge (full send). Confirm live. Report the decisions.

Stop before merge only if the task said merge-ready, or at an irreversible/out-of-repo gate.
