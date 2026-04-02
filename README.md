# claude-md

Global `CLAUDE.md` for AI coding agents, based on established software engineering principles.

## Sources

- **Kent Beck** — XP, TDD, Tidy First (2023)
- **Robert C. Martin** — Clean Code, TDD discipline
- **Martin Fowler** — Refactoring, Strangler Fig, CI
- **ETH Zurich** — [Research on context files for coding agents](https://arxiv.org/abs/2602.11988)

## Usage

Copy `CLAUDE.md` to your project root:

```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/hanno-bot/claude-md/main/CLAUDE.md
```

Or add as a git submodule:

```bash
git submodule add https://github.com/hanno-bot/claude-md.git .claude-md
```

Then reference it from your project's `CLAUDE.md`:

```markdown
@.claude-md/CLAUDE.md

# Project-specific rules below
```

## Principles

- Only rules the agent cannot discover from code (ETH Zurich golden rule)
- ~30 lines — longer files reduce agent performance
- Authorities cited, not opinions invented
