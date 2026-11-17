---
name: perf
description: Playbook for measured slowness. Measure, find the real cost, fix, re-measure against baseline. Use when something is slow — never optimize on a hunch.
---

# perf (playbook)

1. Measure first. Get a baseline number on the real workload. No number, no work.
2. Profile to the actual hot path. The bottleneck is rarely where you'd guess.
3. Fix the dominant cost. Ignore the rest until it dominates.
4. Re-measure vs baseline. Rule out measurement artifacts before trusting the win (warm cache, noise, wrong input).
5. Keep the benchmark so the win can't silently regress.
