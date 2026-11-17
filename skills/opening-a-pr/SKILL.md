---
name: opening-a-pr
description: Playbook to open a ready PR from ordered commits. Invoked at the end of other playbooks. Use when the work is green and needs a PR.
---

# opening-a-pr (playbook)

1. Confirm the branch is green and commits are clean, one logical change each (`sequence-verifiable-units`).
2. Write the PR problem-first: what was broken/needed and why, then what changed (`file-pr`).
3. Keep it short. Lead with the problem, not an inventory of the diff.
4. Open it, then babysit (`babysit-pr`).
