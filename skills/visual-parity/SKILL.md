---
name: visual-parity
description: Playbook for pixel-exact UI equivalence between two implementations or against a design. Compare rendered output directly, don't eyeball. Use when a UI must match a reference.
---

# visual-parity (playbook)

1. Get both rendered: the reference and your version, same viewport and state.
2. Compare directly — screenshot diff or overlay, not from memory.
3. Fix the largest visible delta first; re-render; repeat.
4. Check the states that aren't the happy path: hover, empty, error, long content, narrow width.
5. Done when the diff is noise. Prove it with the side-by-side.
