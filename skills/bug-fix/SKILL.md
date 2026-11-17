---
name: bug-fix
description: Playbook for broken behavior. Reproduce, root-cause, fix, prove. Use for any defect.
---

# bug-fix (playbook)

1. Reproduce. Capture the failing evidence (input → wrong output). No repro, no fix.
2. Root-cause: trace to the first place state went wrong (`fix-root-causes`). If fixes keep failing, `attack-the-premise`.
3. Fix there, smallest change (`laziness-protocol`).
4. Prove the same path now passes (`prove-it-works`). Add a behavior test if it pays (`test-behavior-not-implementation`).
5. Send it (`sendmode` defaults).
