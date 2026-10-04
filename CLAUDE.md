# CLAUDE.md

This repository is a collection of agent skills (one folder per skill, each with a `SKILL.md`).

@AGENTIC.md

## Claude Code specifics
- Skills here are installed by copying a skill folder into `~/.claude/skills/` or `.claude/skills/`.
- Start new work on a `feature/*` (or `fix/*`, `docs/*`) branch, never on `main`.
- Commit with Conventional Commits and keep the `Co-Authored-By` trailer provided by the harness.
- Create PRs with `gh pr create`; on Windows use `--body-file` for bodies with quotes or multiple lines.
- After adding or removing a skill, update the README skills table and badge in the same PR.
