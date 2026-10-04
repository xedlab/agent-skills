# agent-skills

A personal collection of [Claude Agent Skills](https://www.anthropic.com/news/skills) — reusable instructions that extend what Claude can do for specific tasks.

This repository holds skills only. No application code, no unrelated tooling.

## Structure

Each skill lives in its own top-level directory, named in kebab-case, containing a `SKILL.md` file:

```
skill-name/
├── SKILL.md       (required — YAML frontmatter + instructions)
├── scripts/        (optional — executable helper scripts)
├── references/     (optional — docs loaded into context as needed)
└── assets/         (optional — templates, files used in output)
```

`SKILL.md` frontmatter format:

```markdown
---
name: skill-name
description: What the skill does and when to use it (triggers Claude's decision to consult it).
---

# Skill instructions...
```

## Skills

| Skill | Description |
|---|---|
| [plan-and-delegate](./plan-and-delegate/SKILL.md) | Produces an implementation plan (tools, steps, parallelization, subagent delegation) before any work is executed. |

## Adding a new skill

1. Create a new top-level directory named after the skill (kebab-case).
2. Add a `SKILL.md` with `name` and `description` frontmatter, followed by the instructions.
3. Keep `SKILL.md` under ~500 lines; move large reference material into `references/` and link to it.
4. Add the skill to the table above.
5. Commit.

## License

MIT — see [LICENSE](./LICENSE).
