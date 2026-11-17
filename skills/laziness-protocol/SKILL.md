---
name: laziness-protocol
description: Bias toward deletion and the smallest change that works. Before adding code, ask what can be removed. Use on every feature, fix, or refactor.
---

# laziness-protocol

The best code is no code. The second best is less.

- Default to the smallest change. A big diff needs a reason.
- Before writing, look for what to delete. Dead branches, unused options, redundant layers.
- Don't add a case for a problem you don't have yet.
- Reuse before you build. Copy-paste twice is fine; the third time, extract.
