---
description: Scrape hackathon submissions and analyze repos, videos, and timelines to catch cheaters and recycled projects
argument-hint: [hackathon name or Devpost URL]
---

# Hackathon Cheater Catcher

You coordinate a swarm of research agents to scrape every submission from a hackathon and analyze them for cheating patterns. This is the tool organizers wish they had and competitors use to level the playing field.

## Step 1: Get Hackathon Context

Read `.hackathon/hackathon.md` and `.hackathon/rules-analysis.md` if they exist. If `$ARGUMENTS` is a URL, use that directly. Otherwise WebSearch for the Devpost gallery.

**Critical**: You need to know the hackathon start date to detect pre-existing code.

Ask the user:

> Before I start scanning, a few questions:
>
> 1. **Hackathon dates**: When did it officially start and end? (I need exact dates to check git history)
> 2. **Scope**: Do you want me to scan:
>    - **All submissions** (thorough but slow, uses many agents)
>    - **Winners and top submissions only** (faster)
>    - **Specific projects** (list them)
> 3. **What to check**: Select all that apply:
>    - [ ] Git history (commits before hackathon start)
>    - [ ] Code reuse (forked repos, copied code)
>    - [ ] Recycled projects (submitted to other hackathons)
>    - [ ] Video authenticity (pre-recorded vs live, edited vs raw)
>    - [ ] Team member history (serial hackathon recyclers)
>    - [ ] All of the above
>
> This will spawn many parallel agents. Depending on submission count, it could take a while.

Wait for answers before proceeding.

## Step 2: Gather Submission List

Use WebSearch and WebFetch to scrape the Devpost gallery page(s).

For each submission, extract:
- Project name
- Team members (usernames)
- Devpost project URL
- GitHub repo URL (if linked)
- Video URL (if linked)
- Prize tracks submitted to
- Description summary

Save this list to `.hackathon/submissions-raw.md` as a table.

Tell the user how many submissions you found and confirm before proceeding.

## Step 3: Launch Analysis Agents

**IMPORTANT**: Use the Agent tool to spawn parallel subagents. Each agent analyzes one or a batch of submissions. This is the key to making this fast.

For each submission (or batch of 3-5 if there are many), spawn an agent with these instructions:

### Per-Submission Analysis

Each agent should check:

#### Git History Analysis (if repo linked)
- When was the repo created? Before hackathon start = flag.
- First commit date vs hackathon start date
- Commit frequency pattern (all commits in last 2 hours = suspicious)
- Large initial commits (pasting in pre-written code)
- Contributors not on the team roster
- `.git` history showing force-pushes or history rewrites during hackathon
- Dependencies or frameworks set up before hackathon
- README written before hackathon

#### Cross-Submission Check
- Has this project been submitted to other Devpost hackathons?
- Search for the project name or repo URL across Devpost
- Check team members' Devpost profiles for similar past submissions
- Same tech stack + same team + similar description = recycled

#### Code Originality
- Is the repo a fork? Of what?
- Does the README match a template or tutorial?
- Are there tutorial artifacts (example data, placeholder text, default configs)?
- Ratio of boilerplate to original code

#### Video Check (if video linked)
- Is the video URL from a date before the hackathon?
- Does the video description mention another hackathon?
- Is the video length within rules? (from rules-analysis.md)

#### Team Check
- Do team members have Devpost history of submitting similar projects?
- Are team members from an organization excluded by eligibility rules?

### Agent Output Format

Each agent returns a structured report:

```markdown
## [Project Name]
**Devpost**: [url]
**Repo**: [url]
**Team**: [members]

### Flags
- [FLAG_LEVEL]: [description]

Flag levels:
- CLEAN: No issues found
- YELLOW: Suspicious but could be legitimate
- RED: Strong evidence of rule violation
- CRITICAL: Clear cheating

### Evidence
[specific evidence for each flag, with URLs and dates]

### Notes
[anything else notable]
```

## Step 4: Compile Report

After all agents return, compile findings into `.hackathon/cheater-report.md`:

```markdown
# Cheater Analysis: [Hackathon Name]
*Analyzed: {date}*
*Submissions scanned: [N]*

## Summary
- Total submissions: X
- Clean: X
- Yellow flags: X
- Red flags: X
- Critical flags: X

## Critical Flags (Likely Cheating)
[Each project with CRITICAL flags, with evidence]

## Red Flags (Probable Rule Violations)
[Each project with RED flags, with evidence]

## Yellow Flags (Suspicious, Investigate Further)
[Each project with YELLOW flags, with evidence]

## Patterns Observed
- [pattern 1]: e.g., "3 teams submitted forked versions of the same tutorial repo"
- [pattern 2]: e.g., "2 teams have overlapping members submitting to different tracks"

## Methodology
What was checked, what wasn't, and limitations of the analysis.
```

## Step 5: Save State

Save the raw data and analysis state so it can be resumed or re-run:

```
.hackathon/
  submissions-raw.md      # all submissions found
  cheater-report.md       # compiled analysis
  cheater-cache/          # individual project analyses (one file per project)
```

## Rules for Agents

- Only flag with evidence. "This looks suspicious" without specifics is useless.
- Check git dates against hackathon dates. A repo created 6 months ago with the hackathon submission = red flag.
- A repo created 1 day before = could be legitimate (some people set up repos early). Flag yellow, not red.
- Boilerplate and starter templates are NOT cheating unless rules prohibit pre-existing code.
- Using agents/subagents is critical here because you're doing N independent analyses. Parallelize aggressively.
- If you can't access a repo (private), note it but don't flag it.
- Be fair. The goal is catching actual cheaters, not generating false positives.

## Anti-Slop Principles

- Real evidence only. Dates, URLs, commit hashes.
- If you can't determine something, say "unable to verify" not "appears legitimate."
- Don't flag people for being fast builders. Some teams are just good.
- The most common real cheat is recycled projects. Focus there first.
- Second most common: repos with significant code before the hackathon start.
