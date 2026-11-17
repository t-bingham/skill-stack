---
name: test-behavior-not-implementation
description: Assert user-observable behavior, not internal structure. Tests should survive a refactor. Use when writing any test.
---

# test-behavior-not-implementation

Test what it does, not how it does it.

- Assert on inputs and outputs the user or caller sees — not private methods, call counts, or internal state.
- A refactor that keeps behavior should not break a single test.
- Mock only true boundaries (network, clock). Don't mock the thing under test.
- If a test knows the implementation, it's a change-detector, not a safety net — rewrite it.
