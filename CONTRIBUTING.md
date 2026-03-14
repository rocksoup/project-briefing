# Contributing

Use this repo to improve the `project-briefing` skill without tying it to a single project.

## Contribution Rules

- Keep the installed skill agent-agnostic.
- Keep `SKILL.md` concise and push detail into references when needed.
- Preserve the fixed output shape unless there is a strong reason to change it.
- Prefer source adapters and fallback rules over project-specific special cases.
- Test changes with realistic prompts before treating them as ready.

## What To Update

- `project-briefing/SKILL.md` for the main workflow and trigger behavior
- `project-briefing/references/` for examples, adapters, and calibration material
- `evals/` for reusable test prompts and evaluation checks
- `README.md` when the sourcing model, installation guidance, or repo intent changes

## Adapter Guidelines

When adding a new tracker adapter:

- keep the final briefing format unchanged
- document what the adapter should read and what signals matter
- explain fallback behavior if the tracker is unavailable or stale
- avoid overfitting to one team's vocabulary or workflow

## Quality Standard

Each revision should make the skill better at:

- fast orientation
- plain-language translation
- identifying real milestones instead of raw ticket counts
- distinguishing fact from inference
- handling repos with imperfect or incomplete project hygiene
