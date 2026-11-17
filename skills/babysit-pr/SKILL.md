---
name: babysit-pr
description: Watch a PR through CI and review bots and fix the real findings. Use after opening a PR, to drive it to green. Needs an authenticated gh (or equivalent).
---

# babysit-pr

Sit with the PR until it's green, then send it.

- Poll CI. On red, read the actual failure and fix the root cause — not a re-run, not a skip.
- Triage bot/review comments: fix substantive ones, reply to the rest, ignore noise (`leaving-pr-comments`).
- Rebase on conflicts; re-prove anything you touched.
- Merge when green (full send), or hold at merge-ready if the task said so.
