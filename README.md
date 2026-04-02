# agents-md

Engineering principles for AI coding agents — `AGENTS.md` (cross-agent standard) + `CLAUDE.md` (Claude Code).

Based on Beck (XP, TDD, Tidy First), Martin (Clean Code), Fowler (Strangler Fig, CI), and [ETH Zurich research](https://arxiv.org/abs/2602.11988).

## Files

| File | Who reads it |
|---|---|
| `AGENTS.md` | OpenClaw, Copilot, Cursor, Codex CLI, Paperclip |
| `CLAUDE.md` | Claude Code (imports AGENTS.md) |
| `n8n-practices.md` | Any agent working with n8n workflows |

## Usage

Copy both files to your project root:

```bash
curl -O https://raw.githubusercontent.com/hanno-bot/claude-md/main/AGENTS.md
curl -O https://raw.githubusercontent.com/hanno-bot/claude-md/main/CLAUDE.md
```

Then add project-specific rules below the import in `CLAUDE.md` or directly in `AGENTS.md`.

## Principles

- Only rules the agent cannot discover from code (ETH Zurich golden rule)
- ~30 lines — longer files reduce agent performance
- Authorities cited, not opinions invented
