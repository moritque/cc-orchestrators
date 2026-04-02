---
name: cc-project-orchestrator
description: Orchestrate Claude Code plus Superpowers and GSD for small to medium full-project work under about 100k LOC. Use when the user wants a step-by-step workflow for planning, building, verifying, and resuming an entire project while controlling document growth and context rot.
---

# CC Project Orchestrator

Use this skill for full-project work in a small to medium codebase, roughly under 100k lines, where you need durable phase control without drowning in documents.

## Goal

Keep the project moving through phases while preventing context rot and spec sprawl.

## Default tool roles

- **GSD**: project skeleton, roadmap, phase context, state, verification, resume
- **Superpowers**: brainstorming, implementation planning, TDD, debugging, review

## Operating rules

1. Treat GSD as the project spine, not as an excuse to generate every template.
2. Keep only the smallest set of project files that actually help resuming work.
3. Use Superpowers at decision points; use GSD for phase boundaries and continuity.
4. Never let planning documents outgrow the code task.
5. If a document does not help the next step, do not create it.

## Recommended flow

### 1. Project start
Use Superpowers brainstorming first when the idea is still fuzzy.
Then use GSD to create the smallest project skeleton:
- project goal
- roadmap with phases
- current state
- only the requirements that are needed now

### 2. Phase setup
Before each phase, use GSD to lock:
- phase goal
- non-goals
- constraints
- decision points

If a phase needs deeper thinking, use Superpowers to generate options and trade-offs, then feed the result back into GSD context.

### 3. Build
Use Superpowers to create the execution plan for the current phase:
- task breakdown
- tests
- risks
- review checklist

Then execute the work without creating new specs unless the scope changes.

### 4. Verify and resume
Use Superpowers for review/debug when needed.
Use GSD to record only:
- phase progress
- decisions made
- blockers
- next action

## Step-by-step prompt pattern

### Prompt 1: explore and slice
"Use Superpowers brainstorming first. Explore 2-3 implementation directions, trade-offs, and recommend an MVP slice. Keep it compact and avoid long specs."

### Prompt 2: create the minimum project spine
"Now use GSD to create only the minimum project skeleton: project goal, roadmap, current state, and only the requirements needed now. Do not generate every template."

### Prompt 3: lock one phase
"Use GSD to define the current phase only: goal, non-goals, constraints, and decisions to lock. Keep it short."

### Prompt 4: plan execution
"Use Superpowers to produce the execution plan for this phase: task breakdown, risks, tests, and review checklist. Do not expand scope beyond the current phase."

### Prompt 5: execute and record
"Execute the phase. Use Superpowers review/debug if needed. Then use GSD only to record progress, decisions, blockers, and next action."

## Best combinations

- **Superpowers brainstorming → GSD new-project**
- **Superpowers brainstorming → GSD discuss-phase**
- **GSD execute-phase → Superpowers plan/TDD/review**
- **Superpowers review/debug → GSD verify-phase/next**

## Avoid

- running GSD discovery, discuss, and execute as full docs all at once
- letting both suites create competing design artifacts
- writing long requirement specs before the first phase is understood
- using deep research workflows unless the project truly needs them

## Low-bloat defaults

Prefer these defaults unless the user asks for more:
- one project skeleton
- one roadmap
- one state file
- one phase context file at a time
- short verification notes
- no duplicate summaries
