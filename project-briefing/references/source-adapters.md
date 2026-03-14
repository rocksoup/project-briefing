# Source Adapters

Use this reference when deciding how to gather project state.

## Adapter Priority

1. Tracker
2. Git
3. Docs
4. Notes

The final narrative should stay the same even when the source systems differ.

## Beads Adapter

Use the beads adapter when the repo contains `.beads/`, `AGENTS.md` mentions beads, or the `bd` CLI is available.

### What To Pull

- database overview or status
- ready or unblocked work
- blocked work
- major open epics or parent issues
- recently closed milestones or high-signal tasks

### What To Prefer

- epics and parent issues over leaf tasks
- ready work over raw open counts
- blocker chains over flat blocked lists
- recently closed milestones over old historical completions

### What To Avoid

- repeating every blocked ticket
- presenting counts without explaining what they mean
- assuming the current milestone is the highest-priority ticket if the dependency structure says otherwise

## Git Adapter

Use git to answer:

- what actually landed recently
- whether the tracker appears current
- whether there is unpublished or uncommitted work that changes the story

### High-Value Signals

- recent commits on the current branch
- diff between working tree and HEAD
- branch relationship to origin
- recent documentation or runbook changes

### Use Git Carefully

- Do not turn the briefing into a commit log.
- If a real tracker exists, use git as confirmation, not as the primary narrator.
- If git suggests work landed that the tracker does not reflect, mention the mismatch.
- If the working tree contains obviously meta or housekeeping changes that do not change the project's real milestone, do not let those changes dominate the briefing. Mention them only if the user asks about local state specifically.

## Docs Adapter

Use docs to extract:

- the intended architecture
- operating constraints
- environment or deployment model
- business language that explains technical work cleanly

Prefer architecture docs, strategy docs, and runbooks over low-signal notes.

## Notes Adapter

Use notes or user-provided context to capture:

- recent validations not yet recorded in the tracker
- human decisions or preference changes
- cross-project context the repo does not yet contain

If note-based context changes the apparent status, say so explicitly.

## Fallback Behavior

### No Tracker

Build the briefing from git and docs. State that the summary is inferred rather than tracker-backed.

### Stale Tracker

Use the tracker as the baseline but qualify the result with recent git and docs.

### Source Conflict

Prefer the most explicit source in this order:

1. tracker issue details
2. landed git changes
3. maintained docs
4. informal notes

Always mention the conflict if it changes the story.
