---
name: worktree-cleanup
description: Playbook to prune merged or abandoned worktrees and stale branches, safety-gated. Use when the workspace is cluttered with old worktrees/branches.
---

# worktree-cleanup (playbook)

1. List worktrees and branches with their state: merged, abandoned, active.
2. Confirm each candidate is truly done — merged upstream or explicitly dead. Never guess.
3. Remove only the confirmed-safe ones. Stop and ask on anything with unmerged work (out-of-repo / hard-to-undo).
4. Leave active and uncertain worktrees untouched. Report what was pruned.
