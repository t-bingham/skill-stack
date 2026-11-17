---
name: autonomous-run
description: Playbook to drive a long task to completion without stopping. Set the goal, loop, verify, don't block. Use for work that will take many steps unattended.
---

# autonomous-run (playbook)

1. Write the success criterion as something you can check (`prove-it-works`).
2. Open a todo list; work it top to bottom. Never block on the human (`never-block-on-the-human`).
3. After each unit: verify, commit, continue (`sequence-verifiable-units`).
4. Stuck twice on one assumption? `attack-the-premise`. Hit a true wall? Record state, take the best path, keep moving.
5. Stop only at the criterion or an irreversible/out-of-repo gate. Report the decisions made.
