---
name: minimize-reader-load
description: Cut the layers and hidden state a reader must hold to follow the code. Optimize for the next person reading it cold. Use when writing or reviewing anything non-trivial.
---

# minimize-reader-load

Code is read far more than written. Spend the effort there.

- Keep related logic together; don't scatter one decision across files.
- No hidden state. What affects behavior should be visible at the call site.
- Name for what it does, not how. Delete comments that restate the code; keep the ones that explain why.
- Fewer indirections. Each hop the reader follows is a cost.
