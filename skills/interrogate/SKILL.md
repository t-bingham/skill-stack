---
name: interrogate
description: Have a different model try to break your diff; keep only findings proven by running code. Adversarial review on every non-trivial change. Use before sending anything that matters.
---

# interrogate

Build with one mind, break with another.

- Hand the diff to a different model with one job: find what's wrong.
- Demand a repro for each finding — run it. Keep only what's proven; discard speculation.
- Fix the real findings at the root (`fix-root-causes`).
- A clean interrogation is your green light to send. A noisy one that proves nothing is noise.
