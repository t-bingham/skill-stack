---
name: code-mode
description: When a runtime can execute code and call tools, orchestrate through one written script instead of many one-shot tool calls — load tools on demand, filter in code, compose in a single pass. Use for multi-tool, high-fan-out, or large-output tasks.
---

# code-mode

Don't round-trip the model for every tool call. Write the program that does the orchestration.

## The move
- One script calls the tools, joins/filters/loops over results in code, and returns only the distilled answer to the thread.
- The model writes and runs the code; raw intermediate data never enters context.

## Use it when
- A task chains several tools, or fans out over many items.
- Tool output is large but you only need a slice (filter/aggregate in code).
- You'd otherwise make N near-identical tool calls (loop instead).

## How
- Discover and load only the tools the script needs — not the whole surface.
- Call them from code; do the filtering, joining, and control flow there.
- Return the result, not the material (pairs with `guard-the-context-window`).
- No reusable runtime? It degrades to direct tool calls — fine for small tasks.

## Needs a runtime
A sandbox / bash / code-execution tool (Claude Code's Bash, the API `code_execution` tool, or an MCP code-execution server). Run generated code sandboxed, least-privilege, and never let secrets leak into the script's output.
