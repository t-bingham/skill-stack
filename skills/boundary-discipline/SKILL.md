---
name: boundary-discipline
description: Guard at the edges of the system; keep the core pure. Validation, IO, and side effects live at boundaries, not threaded through business logic. Use when designing modules or untangling IO-soaked code.
---

# boundary-discipline

Dirty at the edges, pure in the middle.

- Do validation, auth, IO, and serialization at the boundary. The core takes clean types and returns values.
- Business logic should be testable with no network, DB, clock, or filesystem.
- Inject side-effecting dependencies; don't reach for globals from the core.
- A function deep in the core doing IO is a smell — push it out.
