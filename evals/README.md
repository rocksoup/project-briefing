# Evals

Use these prompts to forward-test the skill before broad installation.

## Core Prompts

- `Use $project-briefing to get me up to speed on this project.`
- `Use $project-briefing to summarize completed work and what is next.`
- `Use $project-briefing to explain the current milestone in plain English.`
- `Use $project-briefing to give me a longer narrative handoff for this repo.`

## Stress Prompts

- `Use $project-briefing on a repo with no formal tracker and tell me what is inferred.`
- `Use $project-briefing when the tracker and git history disagree.`
- `Use $project-briefing and tell me what is next without dumping ticket IDs.`
- `Use $project-briefing and include risks if the project has many blocked dependencies.`

## What Good Output Should Show

- a clear project objective
- high-signal recent completions
- a real current milestone
- a specific next step
- explicit treatment of uncertainty, stale state, or conflicts

## What To Watch For

- issue-count summaries with no narrative
- commit-log summaries with no project framing
- excessive tracker jargon
- hidden uncertainty when sources disagree
- local housekeeping changes dominating the story
