---
description: Snapshot current hackathon session state so you can resume in a fresh context window
argument-hint: [optional label for this snapshot]
---

# Save Hackathon State

Snapshot everything about the current hackathon session into a single resumable state file.

## Step 1: Gather Current State

Read all files in `.hackathon/` directory. For each file that exists, note:
- Filename
- Key content summary (2-3 lines max per file)
- Whether it's complete or in-progress

Also check:
- Current git branch and recent commits related to the hackathon project
- Any agent memory in `.claude/agent-memory/` relevant to this hackathon
- Time remaining (from `.hackathon/hackathon.md` if it has end time)

## Step 2: Write State File

Save to `.hackathon/state.md`:

```markdown
# Hackathon State: [label or hackathon name]
*Saved: {date and time}*

## Status
[One sentence: where the team is in the hackathon lifecycle]

## Completed Steps
- [x] [step]: [what was decided/produced]

## In Progress
- [ ] [step]: [what's been started, what's left]

## Not Started
- [ ] [step]: [what still needs doing]

## Key Decisions Made
- [decision 1]: [why]
- [decision 2]: [why]

## Current Idea/Project
**Name**: [if decided]
**One-liner**: [if decided]
**Track**: [if decided]
**Verdict**: [BUILD/PIVOT/SCRAP from stress-test if run]

## Files in .hackathon/
| File | Status | Summary |
|------|--------|---------|
| hackathon.md | complete | [summary] |
| ... | ... | ... |

## Resume Instructions
When resuming in a new context window:
1. Read `.hackathon/state.md` (this file)
2. Read the files listed above that are marked as complete
3. Continue from the "In Progress" section
4. The user's next command should be: [suggested next command]
```

## Step 3: Confirm

Tell the user:

> State saved to `.hackathon/state.md`.
>
> To resume in a fresh context window, just tell Claude:
> "Read `.hackathon/state.md` and pick up where we left off."
>
> Or run any `/hack:` command and it will auto-read context from `.hackathon/`.

## Rules

- Keep it scannable. This file is for machine consumption (next Claude session), not human reading.
- Include enough context that a fresh Claude instance can resume without asking 10 questions.
- Don't dump entire file contents into the state. Just summaries and pointers.
- If the user gave a label in $ARGUMENTS, use it in the filename: `.hackathon/state-{label}.md`
