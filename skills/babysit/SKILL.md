---
name: babysit
description: Playbook to drive a PR or stack to merge-ready — resolve conflicts, answer review threads, fix real CI findings. Use when a PR exists and needs to get to green and merged.
---

# babysit (playbook)

1. Rebase/resolve conflicts against the base.
2. Watch CI. On failure, fix the real finding — not a retry, not a skip (`fix-root-causes`).
3. Triage review/bot comments: fix the substantive ones, reply to the rest (`leaving-pr-comments`). Ignore noise.
4. Re-prove anything you changed.
5. Merge when green (full send), or stop at merge-ready if the task said so.
