---
name: shipping
description: Playbook to land a green change. Verify, land bottom-up, confirm it's live. Use when work is done and needs to go out.
---

# shipping (playbook)

1. Confirm green: everything proven on the real artifact (`prove-it-works`), CI clean.
2. For a stack of changes, land bottom-up — each must be green before the one above it.
3. Open the PR problem-first (`file-pr`); babysit through CI and bots (`babysit-pr`); merge (full send).
4. Confirm it's actually live where it matters, not just merged.
