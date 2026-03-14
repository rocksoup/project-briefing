---
name: project-briefing
description: Produce a short, business-readable project briefing from the available tracker, git history, docs, and notes. Use when asked to get someone up to speed, explain where a project stands, summarize completed work and what is next, provide a handoff-style status update, or translate tracker state into plain English.
---

# Project Briefing

## Overview

Produce a short handoff-quality briefing that explains what the project is trying to do, what changed recently, where work is currently concentrated, what should happen next, and what risks remain.

Prefer plain business language over tracker jargon, issue-ID dumps, or changelog-style output.

## Workflow

### Step 1: Establish the project objective

Determine what the project is trying to achieve before summarizing status.

Preferred sources, in order:

1. Primary tracker epics, parent issues, or milestone descriptions
2. Key architecture, strategy, or runbook docs
3. Recent shipped work that clarifies the operating model
4. User-provided notes

If the objective is inferred rather than directly stated, say so.

### Step 2: Gather recent completed work

Identify the most important completed work, not every finished item.

Focus on:

- completed milestones or epics
- recently validated operational capabilities
- recent code or documentation changes that materially changed how the project works

Use recent git activity to confirm recency and reality, but do not let git replace the tracker when the tracker is healthy.

### Step 3: Determine the current milestone

Find the most immediate workstream that best explains where the project currently sits.

Prefer:

- the open epic or parent issue with the most downstream impact
- the active milestone implied by recently completed prerequisites
- the nearest unblocked work that unlocks more work behind it

Do not present a leaf task as the whole project unless the project is genuinely that narrow.

### Step 4: Identify the next concrete step

Choose the next actionable step with the highest leverage.

Prefer the step that:

- is unblocked now
- unlocks multiple downstream tasks
- reduces ambiguity or operational risk

If more than one next step matters, name the primary one first and keep the rest brief.

### Step 5: Surface risks and open questions

Call out the things most likely to confuse or delay the next session.

Examples:

- blocked dependency chains
- stale tracker state
- mismatch between tracker state and landed code
- missing validation in a second environment or provider
- known operational gaps

### Step 6: Write the briefing

Use this default section order:

1. `Project Objective`
2. `Completed Recently`
3. `Current Milestone`
4. `Next Concrete Step`
5. `Risks / Open Questions`

Keep the default answer short enough to scan quickly. Expand only when asked.

## Source Order

Use this precedence unless there is a strong reason not to:

1. Primary project tracker
2. Recent git activity
3. Project docs and runbooks
4. User notes or saved thoughts

When sources conflict, prefer the more explicit source and mention the discrepancy.

## Adapters

Support multiple project setups without changing the final output shape.

### Tracker-backed repos

If the project has a real tracker, use it to identify:

- major completed milestones
- current milestone
- next unblocked work
- blocker chains

For tracker-specific guidance, read [references/source-adapters.md](./references/source-adapters.md).

### Tracker-light repos

If no reliable tracker exists, build the briefing from git plus docs and explicitly say the summary is inferred from implementation state rather than a formal backlog.

## Output Rules

- Use plain business language first.
- Mention tracker IDs only when they materially improve clarity.
- Separate facts from inference.
- Use concrete dates when "recent" would otherwise be vague.
- Prefer narrative sentences over raw status labels.
- Do not dump long lists of issue IDs, commits, or file paths.
- Optimize for quick orientation, not completeness.

## Calibration

If tone or structure needs calibration, read [references/output-examples.md](./references/output-examples.md).

## Quality Bar

The final output should read like a concise project handoff:

- easy to scan
- grounded in real sources
- clear about what is done
- clear about what is next
- clear about uncertainty
