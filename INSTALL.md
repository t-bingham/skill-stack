# Install

Portable Agent Skills (`SKILL.md`). Pick your platform(s) — same files, same behavior.

## Claude Code
```bash
cp -R skill-stack/skills/* ~/.claude/skills/
```

## Codex
```bash
cp -R skill-stack/skills/* ~/.codex/skills/
```

## Cursor
```bash
cp -R skill-stack/skills/* ~/.cursor/skills/
```

## ChatGPT (no native skills directory)
Paste [`chatgpt/project-instructions.md`](chatgpt/project-instructions.md) into a ChatGPT **Project**'s instructions (or [`AGENTS.md`](AGENTS.md) into custom instructions). The skills become the Project's operating rules; invoke a playbook by name — `sendmode: <task>`.

## Any agent that reads AGENTS.md
[`AGENTS.md`](AGENTS.md) at the repo root carries the core defaults, so the behavior holds even where skill routing isn't supported.

---

Entry: start any non-trivial task with **`sendmode`**. Customise per project in `CLAUDE.md` / `AGENTS.md` (model choices, stack notes) so skill updates don't overwrite your settings.
