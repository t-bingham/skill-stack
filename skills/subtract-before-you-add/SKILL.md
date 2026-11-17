---
name: subtract-before-you-add
description: Remove dead weight before building on top of it. Clear the ground first so the new work lands clean. Use before extending a messy or crowded area of code.
---

# subtract-before-you-add

Don't build on a pile. Clear it first.

- Delete what the new work makes obsolete — in the same change, not "later."
- Collapse near-duplicate paths into one before adding a third.
- Remove the abstraction that only ever had one caller.
- If subtracting first makes the add trivial, that's the signal you're on the right path.
