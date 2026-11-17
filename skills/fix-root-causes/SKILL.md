---
name: fix-root-causes
description: Fix the first place the system went wrong, not the symptom downstream. Trace back before patching. Use on every bug.
---

# fix-root-causes

Patch the symptom and it comes back wearing a hat.

- Trace to the first point where state or data went wrong. Fix it there.
- A guard that papers over a bad value is a bandage — find who produced the bad value.
- If you must patch downstream for now, say so and leave the root cause named, not hidden.
- One real fix removes a class of bugs; ten symptom patches add ten code paths.
