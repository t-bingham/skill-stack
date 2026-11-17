---
name: tdd
description: Failing test first, then the code to pass it. Use when the behavior is well-specified and you want the test to drive the design. Opt-in — the default bar is prove-it-works, not test-first.
---

# tdd

Red, green, done. Use it where it pays.

1. Write the test for the behavior. Watch it fail for the right reason.
2. Write the least code to pass it (`laziness-protocol`).
3. Refactor with the test holding you (`refactoring`).
- Assert behavior, not implementation (`test-behavior-not-implementation`).
- Reach for this when the spec is clear. For exploratory or UI work, `prototype` then `prove-it-works` instead — don't force test-first.
