# Claude Code Orchestrator Skills

Two AgentSkills for combining **Superpowers** and **Get Shit Done (GSD)** inside Claude Code without letting planning docs explode.

## Included skills

- `cc-bugfix-orchestrator` — for bugfix, hotfix, and small feature work in existing codebases
- `cc-project-orchestrator` — for small/medium full-project work (roughly under 100k LOC)

## When to use

Use these skills when you want step-by-step Claude Code routing that keeps context small and avoids duplicate plans.

### `cc-bugfix-orchestrator`
Best for:
- bugfixes
- hotfixes
- small features
- narrow refactors
- incident follow-up

### `cc-project-orchestrator`
Best for:
- project setup
- phase-based delivery
- resuming ongoing work
- small/medium full-project workflows

## Core rule

- Let **GSD** own continuity, phase boundaries, and state.
- Let **Superpowers** own option generation, execution quality, debugging, and review.
- Do **not** let both suites produce long competing plans for the same step.

## Low-bloat defaults

- Keep only the smallest useful state files
- Prefer short phase context over long specs
- Avoid duplicate plans and summaries
- Re-plan only when a blocker appears

## Usage pattern

### Bugfix / small feature
1. Lock scope with GSD
2. Explore fix options with Superpowers
3. Produce a minimal patch plan with Superpowers
4. Execute
5. Record a short verification/state update with GSD

### Full project
1. Explore directions with Superpowers
2. Create the minimum project skeleton with GSD
3. Lock one phase at a time with GSD
4. Produce the phase execution plan with Superpowers
5. Execute
6. Review/debug with Superpowers
7. Record progress and next action with GSD

## Files

- skill source folders
- packaged `.skill` artifacts

## Editing

Edit the source folders first, then regenerate the `.skill` artifacts.
