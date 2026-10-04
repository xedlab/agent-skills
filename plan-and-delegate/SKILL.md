---
name: plan-and-delegate
description: Produces an implementation plan before any work is executed. Use when the user asks to "make a plan", "plan this out", "parallelize", or wants to know which tools, skills, and plugins (including Claude Marketplace) fit a task. The output is a plan ready to hand off to an executor agent.
---

# Plan and Delegate

## Goal
Produce a clear implementation plan that accounts for the available tools, skills, and plugins. Plan first, execute later. Minimize token usage and wall-clock time.

## Steps

### 1. Inventory (brief)
- List only the tools, skills, and connectors relevant to the task. Do not enumerate the rest.
- Check whether suitable options exist in the Claude Marketplace (plugins, skills, connectors).
- Never install or connect anything without the user's consent. Propose options with a short rationale and discuss them.

### 2. Clarifying questions
- Ask only about non-obvious points that change the plan: goal, constraints, output format, tool choice.
- Batch all questions into a single block. Make reasonable assumptions for everything else and label them as assumptions.

### 3. Plan
Break the work into steps. For each step, state:
- what is done and the expected result;
- which tool or skill is used;
- dependencies on other steps.

### 4. Parallelization
- Mark steps that can run concurrently: no shared dependencies, and no writes to the same files or resources.
- Group them into parallel blocks and keep sequential steps separate.

### 5. Subagents (for the executor agent)
Include this instruction in the plan:
> The executor agent may spawn subagents for independent, parallel steps. Subagents must be lightweight models (GPT Luna or Claude Sonnet 5.5 medium) to save time and tokens. Larger models are reserved for coordination and for steps that require complex decisions.

For each subagent, specify a narrow task, its inputs, and the expected compact output.

### 6. Token economy
- Give subagents only the context they need, not the full history.
- Require short, structured responses from subagents.
- Do not re-read files or repeat results already obtained.

## Output format
1. Assumptions and open questions (if any)
2. Recommended tools, including Marketplace options (marked "requires consent")
3. Plan with steps, dependencies, and parallel blocks
4. Subagent instructions
5. Definition of done
