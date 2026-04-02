---
name: cc-bugfix-orchestrator
description: Orchestrate Claude Code plus Superpowers and GSD for bugfix and small-feature work. Use when the user needs a minimal-invasion fix, narrow enhancement, incident follow-up, or small change in an existing codebase and wants step-by-step instructions that keep context and docs small.
---

# CC Bugfix Orchestrator

Use this skill when the task is a bugfix, hotfix, small feature, or narrow refactor inside an existing codebase.

## Goal

Deliver the smallest safe change with the least context growth.

## Default tool roles

- **Superpowers**: brainstorming, implementation plan, TDD, debugging, review
- **GSD**: scope lock, phase context, progress/state, verification

## Operating rules

1. Prefer **one short planning pass** and **one short execution pass**.
2. Keep docs minimal: only write or update the smallest useful state file.
3. Avoid new specs unless the task truly needs clarification.
4. Do not let both suites generate competing plans.
5. Keep changes limited to the targeted files or behavior.

## Recommended flow

### 1. Scope lock
Use GSD only to define:
- current target
- non-goals
- success criteria
- files/modules in scope

Keep this to a short phase context or state note.

### 2. Brainstorm the fix
Use Superpowers to produce:
- 2-3 implementation options
- trade-offs
- safest option
- likely risk points
- minimal test idea

Do not ask for a long design doc.

### 3. Execute
Use Superpowers to plan and drive the change:
- smallest patch
- no unrelated cleanup
- add tests only when they directly protect the fix

### 4. Verify
Use Superpowers for review/debug if needed, then GSD to record:
- what changed
- what passed
- what remains

## Step-by-step prompt pattern

### Prompt 1: lock scope
"Use GSD only to lock scope for this bugfix/small feature. Keep it short. Define target, non-goals, success criteria, and in-scope files. Do not create long specs."

### Prompt 2: choose an approach
"Use Superpowers brainstorming for this scoped task. Give me 2-3 fix options, trade-offs, the safest recommendation, and the minimum tests. Keep the answer compact."

### Prompt 3: produce the patch plan
"Using the chosen approach, create a minimal patch plan. No unrelated cleanup, no architecture rewrite, no extra docs. Focus only on the current scope."

### Prompt 4: execute and verify
"Execute the plan. If blocked, switch to Superpowers debugging. When done, use GSD only to record what changed, what passed, and what remains."

## Best combinations

- **Superpowers brainstorming → GSD scope lock → Superpowers execution plan**
- **GSD scope lock → Superpowers minimal patch plan → GSD verify**
- **Superpowers debug → GSD state update**

## Avoid

- Superpowers brainstorming + GSD discovery in the same round
- GSD phase docs plus a full Superpowers plan for the same decision
- generating separate long specs, retros, and reports unless explicitly needed
- re-planning after code already started unless a blocker appears

## Output discipline

Prefer:
- bullets over prose
- one decision per line
- one state file over many docs
- short summaries over narrative
