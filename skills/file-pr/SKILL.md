---
name: file-pr
description: Open a short PR that leads with the problem, not an inventory of changes. Use whenever you open a pull request.
---

# file-pr

Lead with why. The diff speaks for the what.

- First line: the problem this solves or the behavior it adds. One sentence.
- Then the approach, briefly — and any decision a reviewer would question.
- Skip the file-by-file list; the diff shows it. Link the issue if there is one.
- Keep it short enough to read in 30 seconds. Format comments cleanly (`leaving-pr-comments`).
- `unslop` the description and commit messages before they ship — no filler, no AI tells.
