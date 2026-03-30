---
description: Initialize hackathon project context in the current repo with persistent state
argument-hint: [hackathon name]
---

# Initialize Hackathon Project

Set up the `.hackathon/` directory in the current repo to give all `/hack:*` commands persistent project context.

## Step 1: Check for Existing State

Check if `.hackathon/hackathon.md` already exists. If it does, show the user what's there and ask if they want to reset or update it.

## Step 2: Gather Context

Ask the user these questions (skip any they've already answered via $ARGUMENTS):

> Setting up hackathon context for this project. A few quick questions:
>
> 1. **Hackathon name**: What hackathon is this for?
> 2. **Devpost URL**: Link to the hackathon page (if on Devpost)
> 3. **Duration**: When does it start and end? (dates + times + timezone)
> 4. **Tracks/prizes**: What prize categories are available?
> 5. **Team**: Who's on the team? (names + skills, e.g., "Alice: frontend, Bob: ML")
> 6. **Theme**: Is there an official theme or prompt?
> 7. **Constraints**: Any specific rules you already know about? (e.g., "must use Sponsor X API")

Wait for answers. Don't require all fields. Fill what you get, mark the rest as TBD.

## Step 3: Create .hackathon/ Structure

Create the directory and initial files:

```
.hackathon/
  hackathon.md          # Core context (name, dates, tracks, team)
  state.md              # Session state (what's been done, what's next)
  .gitignore            # Optional: user chooses whether to track in git
```

### hackathon.md format:

```markdown
# [Hackathon Name]

**Devpost**: [url or TBD]
**Dates**: [start] to [end] ([timezone])
**Time Remaining**: [calculated from dates]

## Theme
[theme or TBD]

## Tracks
| Track | Sponsor | Requirements | Notes |
|-------|---------|-------------|-------|

## Team
| Name | Skills | Role |
|------|--------|------|

## Constraints
- [any known rules]

## Current Idea
[TBD until stress-tested]
```

### state.md format:

```markdown
# Hackathon State
*Initialized: {date}*
*Last updated: {date}*

## Phase: SETUP

## Completed
- [x] Project initialized

## Available Next Steps
- `/hack:tech-scan` to scan trending tech
- `/hack:analyze-rules` to extract hackathon rules
- `/hack:past-winners` to research what won before
- `/hack:deep-research [topic]` to explore a domain
- `/hack:gen-ideas` to brainstorm ideas

## Artifacts
| File | Status | Command |
|------|--------|---------|
| hackathon.md | created | /hack:init |
```

## Step 4: Ask About Rules

If the user provided a Devpost URL, ask:

> Want me to analyze the hackathon rules now? I can extract submission requirements, deadlines, and gotchas. Run `/hack:analyze-rules`.

## Step 5: Ask About .gitignore

> Should `.hackathon/` be tracked in git?
> - **Yes**: Good for team collaboration, keeps context in the repo
> - **No**: I'll add it to `.gitignore`. Good if you don't want hackathon artifacts in your project history.

## Step 6: Confirm

> Hackathon project initialized in `.hackathon/`.
>
> All `/hack:*` commands will now read context from this directory. State persists across sessions.
>
> Suggested next step: `/hack:tech-scan` or `/hack:analyze-rules [hackathon name]`
