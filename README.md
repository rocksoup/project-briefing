# Project Briefing

Turn tracker state, recent implementation history, docs, and operator context into a fast, business-readable project brief.

This repository is the shared home for a reusable `project-briefing` skill intended to work across projects, computers, and AI agents.

## What It Does

The skill answers prompts such as:

- `get me up to speed`
- `where did we leave this`
- `give me the brief`
- `summarize completed work and what's next`
- `what's the status of this project in plain English`

Its job is not to export tracker data. Its job is to translate project state into a short briefing that helps someone re-enter a project quickly.

## Default Output Shape

The skill is designed to produce five short sections:

1. `Project Objective`
2. `Completed Recently`
3. `Current Milestone`
4. `Next Concrete Step`
5. `Risks / Open Questions`

The intended result should read like a project handoff, not a changelog.

## How The Skill Gathers Source Material

This skill does not rely on a single source. It builds a briefing by combining the project's planning system, recent implementation history, and the highest-signal documentation in the repo.

Source order:

1. Repository instruction files such as `AGENTS.md`, `CLAUDE.md`, `.github/copilot-instructions.md`, and `README.md`
2. The primary project tracker, such as beads, GitHub Issues, Jira, or Linear
3. Recent git activity, including recent commits, branch state, and local working tree status when relevant
4. High-signal documentation such as `docs/`, runbooks, architecture docs, strategy docs, plans, notes, and recent reports
5. User-provided context from the current conversation

The skill uses each source differently:

- Tracker: intended milestones, open work, blockers, and next actionable steps
- Git: what actually landed recently and whether the tracker appears current
- Docs: project objective, architecture, operating model, and business context
- User context: recent validations or decisions that may not yet be recorded elsewhere

The skill prefers concise, high-signal sources over exhaustive scanning. It reads enough to explain:

- what the project is trying to achieve
- what was completed recently
- what the current milestone is
- what should happen next
- what risks or open questions remain

If sources disagree, the skill should call that out explicitly instead of hiding the mismatch.

## Design Principles

This repository follows a few hard rules:

- Plain business language first
- Consistent output shape across projects
- Tracker-aware but not tracker-dependent
- Evidence over guesswork
- Short by default, longer only on request
- Agent-agnostic instructions and references

The skill should work for any capable agent or human operator that can inspect repo state and follow documented workflows.

## Best-Practice Influences

The skill design follows current guidance from both OpenAI and Anthropic:

- OpenAI guidance on strong prompting for coding agents, clear task specification, and eval-driven iteration
- Anthropic guidance on prompt structure, explicit task framing, and modular agent skills

Those influences show up here as:

- fixed output structure
- clear source precedence
- concise instructions
- explicit separation between facts and inference
- examples for calibration
- forward-testing before distribution

Reference sources:

- OpenAI: GPT-5 Codex Prompting Guide
- OpenAI: Evals design guide
- Anthropic: Prompt engineering overview
- Anthropic: Agent Skills best practices
- Anthropic: Building effective agents

## Repository Layout

```text
project-briefing/
├── README.md
├── CONTRIBUTING.md
├── evals/
│   └── README.md
└── project-briefing/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    └── references/
        ├── output-examples.md
        └── source-adapters.md
```

The nested `project-briefing/` directory is the installable skill. The repo root can contain supporting material such as README content, eval guidance, and contribution rules without polluting the skill folder itself.

## Installation

Install the `project-briefing/` directory, not the entire repository root, into whatever skill directory your agent system uses.

Recommended approaches:

- for resilient day-to-day use, copy `project-briefing/` into the target global skills directory
- for development-only workflows, symlinks are acceptable if you want edits in the repo to reflect immediately in a local install
- treat this repo as the canonical source of updates, even if installed copies are distributed elsewhere

Examples:

- OpenAI Codex-style local skills: copy `project-briefing/` to `~/.codex/skills/project-briefing`
- Anthropic local skills on this machine: copy `project-briefing/` to `~/.claude/skills/project-briefing`
- Shared dotfiles or bootstrap setup: clone this repo and recreate the copied install on each machine
- Other agent systems: point them at the installable skill folder anywhere a skill is expected to be a directory containing `SKILL.md`

The repo itself is for sharing, versioning, and iterating on the skill. The nested skill directory is the portable artifact.

## Supported Source Patterns

Version 1 is designed around these inputs:

- tracker-backed repos, especially beads-backed repos
- git-backed recency checks
- docs-heavy repos with architecture and runbook material
- conversation context that fills gaps not yet captured in the repo

Future adapters can support additional systems without changing the final narrative format.

## What Good Output Looks Like

A good briefing should:

- explain the project goal in one or two sentences
- name only the most important recent completions
- identify the current milestone, not just the highest-priority ticket
- pick the next highest-leverage step
- surface blocker chains, stale tracker state, or unresolved validation gaps

A bad briefing usually looks like one of these:

- a dump of issue counts
- a list of ticket IDs without translation
- a commit log with no project narrative
- an overconfident summary that hides source conflicts

## Example

`Project Objective:` Build a hosted data platform that can ingest domain data, support remote agent workflows, and eventually produce higher-level intelligence and outputs.

`Completed Recently:` The platform foundation and first live ingestion milestone are complete. Recent work focused on proving that browser-based cloud coding sessions can authenticate to the hosted environment and perform the required operations safely.

`Current Milestone:` Turn the proven remote access path into the standard operating workflow for the real agent environment.

`Next Concrete Step:` Validate the same remote workflow from the second cloud coding provider so the operating model is genuinely portable.

`Risks / Open Questions:` The backlog remains dependency-heavy, and the latest manual validation may not yet be fully reflected in the tracker.

## Development Workflow

When improving the skill:

1. Update the skill instructions or references
2. Validate the skill structure
3. Run forward tests with realistic project prompts
4. Compare output quality against the evaluation prompts in `evals/`
5. Refine before installing or publishing broadly

## Repository Intent

This repo is meant to become the shared source of truth for the `project-briefing` skill so it can be:

- reused across many repos
- synced across multiple computers
- shared with collaborators
- installed into local agent skill directories when desired

## External References

- OpenAI Codex Prompting Guide: <https://developers.openai.com/codex/prompting-guide>
- OpenAI Evals Design Guide: <https://platform.openai.com/docs/guides/evals-design>
- Anthropic Prompt Engineering Overview: <https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview>
- Anthropic Agent Skills Best Practices: <https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices>
- Anthropic Building Effective Agents: <https://www.anthropic.com/engineering/building-effective-agents>
