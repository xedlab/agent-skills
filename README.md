# 🧰 agent-skills

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)
[![Skills](https://img.shields.io/badge/skills-1-brightgreen.svg)](#-skills)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-orange.svg)](#-adding-a-new-skill)

A personal collection of reusable **agent skills** — small, self-contained instruction packs that teach an AI agent (such as [Claude](https://www.anthropic.com/news/skills)) how to perform a specific workflow: planning, delegating to subagents, reviewing code, and more.

This repository contains skills only — no application code, no unrelated tooling.

## 📚 Skills

| Skill | What it does | When to use it |
|---|---|---|
| [plan-and-delegate](./plan-and-delegate/SKILL.md) | Produces an implementation plan (tools, steps, parallel blocks, subagent delegation) *before* any work is executed. | "Make a plan", "plan this out", "parallelize", or when you want to know which tools, skills and plugins fit a task. |

## 🚀 Quick start

1. Clone the repository:
   ```bash
   git clone https://github.com/xedlab/agent-skills.git
   ```
2. Copy the skill folder you want into your agent's skills directory. For Claude Code:
   ```bash
   # personal (all projects)
   cp -r agent-skills/plan-and-delegate ~/.claude/skills/

   # or project-level
   cp -r agent-skills/plan-and-delegate <your-project>/.claude/skills/
   ```
3. Ask the agent to do something the skill covers (e.g. *"make a plan for migrating this service"*). The agent picks the skill based on its `description`.

## 🗂️ Repository structure

Each skill lives in its own top-level kebab-case directory:

```
skill-name/
├── SKILL.md        (required — YAML frontmatter + instructions)
├── scripts/        (optional — executable helper scripts)
├── references/     (optional — docs loaded into context as needed)
└── assets/         (optional — templates and files used in output)
```

`SKILL.md` starts with frontmatter:

```markdown
---
name: skill-name
description: What the skill does and when to use it (this is what the agent matches against).
---

# Skill instructions...
```

## ➕ Adding a new skill

1. Create a top-level directory named after the skill (kebab-case).
2. Add a `SKILL.md` with `name` and `description` frontmatter, followed by the instructions.
3. Keep `SKILL.md` under ~500 lines; move large reference material into `references/` and link to it.
4. Add the skill to the [Skills](#-skills) table above and bump the badge count.
5. Open a pull request.

## 📄 License

MIT — see [LICENSE](./LICENSE).
