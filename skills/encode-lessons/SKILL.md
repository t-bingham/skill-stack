---
name: encode-lessons
description: Turn a lesson learned into a lint, test, type, or script — not a note nobody reads. Make the mistake impossible to repeat. Use after a bug or a review catch that could recur.
---

# encode-lessons

A rule in your head is forgotten. A rule in the build is enforced.

- Just fixed a recurring mistake? Encode it: a lint rule, a test, a type that forbids it, a CI check.
- Prefer the mechanism that fails loudly and early over documentation.
- If it can't be automated, put it in `AGENTS.md`/`CLAUDE.md` where the agent reads it — not a buried comment.
- The goal: the next person (or agent) can't make the same mistake without the build complaining.
