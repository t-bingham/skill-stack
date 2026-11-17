---
name: setup
description: Configure the stack for a project or machine — which models fill which roles, and any project rules. Use once per project/machine, or when changing model roles.
---

# setup

Pick the roles once; write them where the agent reads them.

- Assign models to roles: builder (deep work), reviewer (interrogate/council), cheap worker (swarm slices, bulk reads).
- Record them in the project's `AGENTS.md`/`CLAUDE.md`, not in a skill file — so skill updates don't overwrite your config.
- Note any project rule the agent must always follow there too.
- Keep it one short block. Revisit when a better model lands (try new things).
