---
name: refactoring
description: Playbook for behavior-preserving structural change. Pin behavior with tests, change shape, prove nothing moved. Use when restructuring without changing what the code does.
---

# refactoring (playbook)

1. Pin current behavior: ensure tests cover it, or add behavior tests first (`test-behavior-not-implementation`).
2. Subtract before adding (`subtract-before-you-add`). Delete what the new shape makes dead.
3. Change structure in small units; green after each (`sequence-verifiable-units`).
4. Converge on the target shape — no compat shims left (`outcome-oriented-execution`).
5. Prove behavior is identical. If a test changed, you changed behavior — stop.
