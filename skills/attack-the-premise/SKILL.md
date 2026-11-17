---
name: attack-the-premise
description: After two or more fixes that share an assumption have failed, stop fixing and test the assumption itself. Use when you're stuck in a loop of near-misses.
---

# attack-the-premise

Two failed fixes on one assumption means the assumption is the bug.

- Stop patching. Write down what you've been assuming is true.
- Prove it with evidence — print it, log it, check it directly. Don't reason about it; observe it.
- The wrong layer, the wrong file, a cached build, a different process — the surprise is usually in the premise, not the code.
- Once the premise breaks, the real fix is obvious.
