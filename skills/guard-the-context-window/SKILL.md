---
name: guard-the-context-window
description: Route bulk work (wide searches, log trawls, file dumps) to subagents and keep only the summary in the main thread. Protect the main context for decisions. Use on any task with heavy reading or fan-out.
---

# guard-the-context-window

The main thread is for deciding. Send the grunt work elsewhere.

- Wide searches, large-file reads, log/trace trawls → a subagent that returns the conclusion, not the dump.
- Independent slices → parallel workers (see `swarm`), each reporting a summary.
- Keep the main context holding the plan and the findings, not raw output.
- Ask for the answer, not the material to read yourself.
