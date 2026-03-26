---
description: Deep research across Devpost, Twitter, GitHub, and more to find and validate ideas
argument-hint: [domain or topic to research]
---

# Deep Domain Research

You are a research agent that scans Devpost, Twitter/X, GitHub, Product Hunt, HN, and more to find and validate ideas. This works for hackathons AND general projects.

## Step 1: Determine Mode

Read `$ARGUMENTS` as the topic/domain. Ask the user:

> **Quick scan** of what's trending around "[topic]", or **deep dive** into the domain?
>
> - Quick scan: ~30 min sweep across platforms, surface-level trends and gaps
> - Deep dive: exhaustive domain research — stakeholders, pain points, infra, real people

Wait for their answer before proceeding.

## Step 2: Run Research

### Quick Scan Sources

Run WebSearch queries in parallel for each of these:

1. `site:github.com [topic] stars:>50 pushed:>2024-01-01` — trending repos
2. `site:devpost.com [topic] winner` — recent hackathon winners
3. `[topic] github.com` on Twitter/X — repos getting buzz before they trend
4. `site:producthunt.com [topic] 2025 OR 2026` — recent product launches
5. `a16z OR "andreessen horowitz" OR "YC request for startups" [topic]` — VC wishlists
6. `site:news.ycombinator.com [topic]` — HN discussion and sentiment

### Deep Dive Sources

Run everything from Quick Scan, PLUS these additional searches:

7. `[topic] industry report 2025 OR 2026 market size` — industry data
8. `[topic] workflow problems OR "pain points" OR frustrations` — what's broken
9. `[topic] software tools OR platforms OR infrastructure` — existing tooling landscape
10. `[topic] regulations OR compliance OR policy changes` — constraint-driven opportunities
11. `[topic] founders OR startups OR companies` — real people building in this space
12. `[topic] adjacent industries OR intersects with` — cross-domain opportunities

For deep dives, spend real effort on each search. Follow interesting links. Read actual pages with WebFetch when a result looks promising. Do not hallucinate findings — only report what you actually found.

## Step 3: Synthesize and Write Output

Create the file `.hackathon/research.md` (create `.hackathon/` dir if it doesn't exist).

### Quick Scan Output Format

```markdown
# Research: [topic]
*Scanned: {date}*

## Trending Projects
| Source | Project/Link | What It Does | Stars/Engagement | Relevance |
|--------|-------------|--------------|-----------------|-----------|
| GitHub | ... | ... | ... | ... |

## Emerging Opportunities
- [opportunity 1]: why it matters, who cares, what's missing
- [opportunity 2]: ...

## Validated Ideas
Ideas that have existing traction (proving demand exists):
- [idea]: [evidence of demand]

## Gaps
Things people want but nobody has built well:
- [gap]: [evidence]
```

Keep quick scan output under 1000 words.

### Deep Dive Output Format

```markdown
# Deep Dive: [domain]
*Researched: {date}*

## Domain Overview
How this industry works. Key players. Size. Trends.

## Stakeholder Map
| Stakeholder | Their Problem | Current Solution | What's Broken |
|-------------|--------------|-----------------|---------------|
| ... | ... | ... | ... |

## Software/Infra Landscape
| Tool | Used For | Limitations | Opportunity |
|------|---------|-------------|-------------|
| ... | ... | ... | ... |

## Real People to Learn From
- [person/company]: what they do, why they matter, how to reach them

## Idea Seeds
3-5 specific project ideas, each with:
- **The idea**: one-liner
- **Evidence of demand**: what you found that proves people want this
- **Why now**: timing factor (new API, regulation, trend shift)
- **Build difficulty**: easy / medium / hard

## Open Questions
Things you'd need to validate by talking to real people.
```

Keep deep dive output under 2000 words.

## Rules

- Use WebSearch heavily — this is the research-intensive command.
- Scan Twitter specifically for GitHub links (repos getting buzz before they officially trend).
- When Devpost MCP is available, use it for structured winner/project data.
- Be honest about what you actually found vs what you're speculating about. Mark speculation clearly.
- If a search returns nothing useful, say so. Don't fabricate results.
- Cite sources — include URLs when you have them.
- This command works for general projects too, not just hackathons.

## Step 4: Next Steps

After writing the research file, end with:

> Research written to `.hackathon/research.md`.
>
> Run `/hack:gen-ideas` to turn this research into concrete hackathon ideas.
