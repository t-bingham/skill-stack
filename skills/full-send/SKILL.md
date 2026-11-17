---
name: full-send
description: Take a change from working tree to merged in one unbroken run — prove, review, file, babysit, merge. The default autonomy level. Use when told to ship it end to end.
---

# full-send

All the way to merged, no stops.

1. Prove it works on the real artifact (`prove-it-works`).
2. Stress-test the diff (`interrogate`).
3. File the PR (`file-pr`).
4. Babysit to green (`babysit-pr`).
5. Merge. Confirm live. Report decisions made.

Stop only at an irreversible/out-of-repo gate, or if the task asked for merge-ready instead of merged.
