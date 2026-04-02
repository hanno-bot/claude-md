# AGENTS.md

Global guidance for all projects. Only rules the agent cannot discover from code.

## Philosophy (Beck, Martin, Fowler)

- Simplest thing that works — a 3-line edit beats a 200-line new script
- YAGNI — don't build for hypothetical future requirements
- Read before write — find what exists before creating anything new
- Tidy First — separate structural changes from behavioral changes, never mix in one commit (Beck 2023)
- Make it work → make it right → make it fast, in that order

## TDD cycle (Beck)

1. Write a failing test first. You must see it fail.
2. Write the minimum code to make it pass — no more.
3. Refactor only when tests are green.
4. One test at a time. Run all tests after each change.

## Commits (XP + CI)

- Each commit is one logical change — structural OR behavioral, never both
- All tests passing before commit
- Small and frequent over large and infrequent
- Replace existing systems gradually (Strangler Fig), never big-bang rewrite

## Discipline (Martin)

- One change, one purpose — don't mix a bugfix with a refactor
- Change only what was asked — don't "improve" adjacent code
- If something is unclear, ask immediately — don't build on assumptions

## External systems

n8n, Airtable, GitHub Actions, CI/CD are code. Before building anything new:
1. List what exists in that system
2. Read the relevant parts fully
3. Identify the smallest change that solves the problem

## Language

Respond in Estonian. Code, comments, and commits in English.
