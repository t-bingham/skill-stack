---
name: why
description: Explain why something was built this way, from commit and PR history. Use before changing code whose reasoning isn't obvious — don't undo a decision blind.
---

# why

The code says what. History says why.

- Read the commit that introduced it and the PR around it. Look for the problem it solved.
- Check for a fix-commit lineage — what broke before this existed.
- Separate real constraint from accident. Some "why" is just the day it was written.
- Output: the reason, with the commit/PR as evidence. Now you can change it knowingly.
