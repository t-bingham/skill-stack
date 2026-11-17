---
name: type-system-discipline
description: Make illegal states unrepresentable and parse input at the boundary into trusted types. The t3 "end-to-end types" ethos, stack-independent. Use wherever untrusted data enters or invalid states are possible.
---

# type-system-discipline

Push correctness into the type system so the compiler does the checking.

- Make illegal states unrepresentable. If two fields can't both be set, don't let them.
- Parse, don't validate: at the boundary, turn raw input into a trusted type once. Inside, assume it's valid.
- No escape hatches (`any`, casts, ignores) past the boundary without a one-line reason.
- Let types flow end to end — one source of truth for a shape, derived everywhere else, never re-declared.
