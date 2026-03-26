---
description: Scan trending tech and APIs to build context for hackathon ideation
argument-hint: [topic area or blank for general scan]
---

# Tech Scan

You are building a tech context file that other hstack commands will reference. The user is physically at a hackathon. They are the primary source of signal -- web search only fills gaps.

## Step 1: Check for existing context

Check if `.hackathon/tech-context.md` exists in the current project directory.

- If it exists, show the user when it was last scanned (read the date from the file) and ask: "Tech context already exists from {date}. Want me to **update** it with new info or **start fresh**?"
- If it does not exist, proceed directly to Step 2.

## Step 2: Gather ground truth from the user

Ask the user these 3 questions. Present them all at once so the user can answer in a single message:

1. "What tech or APIs have you seen sponsors pushing at this hackathon?" (e.g., Convex, Groq, Cloudflare Workers, etc.)
2. "Any new tools, frameworks, or APIs you've been seeing buzz about this week?" (Twitter/X, Discord, hallway chatter)
3. "Any specific tech you're excited to use or want to explore?"

If the user provided a `$ARGUMENTS` topic area, tailor the questions toward that domain. For example, if the argument is "AI agents", ask specifically about AI agent frameworks, orchestration tools, and related APIs.

Wait for the user's response before proceeding.

## Step 3: Verify and enrich with web search

Based on what the user mentioned, run **2-3 targeted WebSearch queries** max. Do NOT search for every single thing. Focus searches on:

- Tech the user seemed unsure about ("I think it was called...")
- Filling in missing details (pricing tier, docs URL, what it actually does)
- Identifying what's trending in the topic area if the user gave one

For each piece of tech, determine:
- **Name**: Official name
- **One-line description**: What it does in plain english
- **Docs link**: Official documentation URL
- **Integration effort**: Easy / Medium / Hard (based on typical hackathon integration)

## Step 4: Synthesize and identify patterns

Look across everything gathered and identify:
- **Emerging patterns**: Combinations of tech that multiple teams are likely building with
- **Combo opportunities**: Novel intersections the user might NOT have considered -- the non-obvious pairings that could differentiate a project

## Step 5: Write the context file

Create the directory `.hackathon/` if it doesn't exist, then write `.hackathon/tech-context.md` with this exact structure:

```markdown
# Tech Context
*Scanned: {YYYY-MM-DD}*

## Sponsor Stack
| Tech/API | Sponsor | What It Does | Docs | Integration Effort |
|----------|---------|--------------|------|--------------------|
| {name} | {sponsor or "—"} | {one-line} | {url} | {Easy/Medium/Hard} |

## Trending Now
| Tech | Why It's Hot | Good For | Effort |
|------|-------------|----------|--------|
| {name} | {reason} | {use cases} | {Easy/Medium/Hard} |

## Emerging Patterns
- **{Pattern name}**: {description} (combining {X} + {Y})

## Combo Opportunities
Novel intersections worth exploring:
- **{Tech A} + {Tech B}** = {interesting idea angle}
- **{Tech C} + {Tech D}** = {interesting idea angle}
```

## Constraints

- The output file must be **under 1000 words**. This is a reference doc, not an essay.
- Aim for **65-75 lines** in the output file.
- User input is the primary signal. Web search is supplemental. Do not override what the user tells you with web results.
- Keep tables compact. One line per entry, no multi-sentence descriptions.
- Every tech entry needs: name, one-line description, and integration effort at minimum.

## Finish

After writing the file, confirm with:

> Tech context saved to `.hackathon/tech-context.md` with {N} technologies cataloged.
>
> Run `/hack:gen-ideas` to brainstorm ideas using this context.
