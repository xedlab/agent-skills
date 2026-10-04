# AGENTIC.md

Instructions for any AI agent (Claude Code, Codex, Cursor, etc.) working in this repository. Read this file first.

## What this repository is

A collection of reusable **agent skills**. Each skill is a top-level kebab-case folder containing a `SKILL.md` (YAML frontmatter + instructions) and optional `scripts/`, `references/`, `assets/`. The repository contains skills only — no application code, no unrelated tooling.

Current skills are listed in the table in [README.md](./README.md#-skills), which is the source of truth.

## Two ways you may be here

### 1. You are *using* a skill
- Match the user's request to a skill's `description` (frontmatter in each `SKILL.md`).
- Read only the relevant `SKILL.md`, and open `references/` or `scripts/` files only when the skill points to them.
- Follow the skill's steps and output format as written. Do not load skills that are not relevant.
- If installed elsewhere, skills are copied into `~/.claude/skills/` (personal) or `<project>/.claude/skills/` (project).

### 2. You are *maintaining* this repository
Follow the rules below.

## Maintaining skills

### Creating or changing a skill
1. Directory name: kebab-case, equal to the `name` in frontmatter.
2. `SKILL.md` must start with frontmatter containing `name` and `description`. The description says **what** the skill does and **when** to use it — it is what agents match against, so include trigger phrases.
3. Keep `SKILL.md` under ~500 lines. Move large material into `references/` and link to it.
4. Write instructions that are concise, imperative, and testable. No filler.
5. Write skills in English.

### Bookkeeping (keep the repo consistent)
Every change that adds, renames, or removes a skill must, in the same PR:
- update the **Skills table** in `README.md` (name linked to its `SKILL.md`, one-line description, when to use it);
- update the **skills count badge** in `README.md`;
- keep the `name` in frontmatter, the folder name, and the README link identical.

Do not add generated files, build artifacts, or secrets. Do not edit `LICENSE`.

## Git workflow

- Never commit directly to `main`. Branch from an up-to-date `main`.
- Branch names: `<type>/<short-kebab-description>`, e.g. `feature/plan-and-delegate-skill`, `fix/readme-links`, `docs/agent-instructions`.
- One logical change per branch and per PR.
- Open a PR into `main` with an English description: what changed and why.
- Do not force-push shared branches or rewrite history on `main`.

## Commit messages

Use [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<optional scope>): <summary>

<optional body: what and why, wrapped at ~72 chars>
```

- **Types:** `feat` (new skill or capability), `fix`, `docs`, `refactor`, `chore`.
- **Scope:** the skill folder name when the change is limited to one skill, e.g. `feat(plan-and-delegate): add token economy section`.
- **Summary:** English, imperative mood ("add", not "added"), lowercase, no trailing period, ≤ 72 characters.
- Explain *why* in the body when it is not obvious from the diff.
- If the commit was made with an AI agent, keep the attribution trailer the tool requires (e.g. `Co-Authored-By: ...`).

Examples:
```
feat(code-review): add skill for reviewing pull requests
fix(plan-and-delegate): clarify subagent model guidance
docs: update README skills table
chore: ignore IDE files
```

## Pull request checklist
- [ ] Skill folder name, frontmatter `name`, and README entry match
- [ ] Frontmatter `description` states what the skill does and when to use it
- [ ] README skills table and badge count updated
- [ ] `SKILL.md` is under ~500 lines
- [ ] Commits follow Conventional Commits
- [ ] PR description is in English and explains what was added and why

## Boundaries
- Do not install packages, connect services, or run destructive git commands without the user's consent.
- Do not invent facts about tools or APIs inside skills; verify them or leave them out.
- When unsure whether something belongs here, ask the user.
