---
name: model-the-domain
description: Encode the domain in types and structures, not in scattered conditionals. Make the code mirror the real problem. Use when logic is drifting into special cases and flags.
---

# model-the-domain

If the domain has three kinds of thing, the code should too.

- Turn clusters of booleans and string flags into named states/variants.
- A branch that keeps reappearing is a missing type — introduce it.
- The rules of the domain belong in the structure, so invalid combinations can't be built.
- When the model is right, new requirements slot in; when it fights you, remodel.
