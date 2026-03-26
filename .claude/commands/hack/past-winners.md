---
description: Research past winners of this hackathon to find patterns and differentiation angles
argument-hint: [hackathon name]
---

Research past winners of the hackathon specified by $ARGUMENTS (or read from `.hackathon/hackathon.md` if no argument given) to find winning patterns, saturated ideas, and differentiation opportunities.

## Step 1: Identify the hackathon

If `$ARGUMENTS` is provided, use that as the hackathon name. Otherwise read `.hackathon/hackathon.md` for the hackathon name and details.

## Step 2: Research past winners

Use WebSearch extensively to find:

1. **This hackathon's past winners** — search Devpost gallery (`site:devpost.com [hackathon name] winners`), the hackathon's official website, and any blog posts announcing results.
2. **Winners of similar hackathons** in the same category or hosted by the same org.
3. **Devpost project pages** for each winner — pull tech stack, team size, and project descriptions.
4. **Social media and blog recaps** — sometimes organizers or participants post retrospectives.

If this is a first-time hackathon with no past winners, search for winners of the closest comparable hackathons instead and note this clearly.

## Step 3: Analyze patterns

From the winners found, identify:
- What types of projects win (technical depth vs polish vs social impact vs creative demo)
- Common tech stacks among winners
- Solo vs team wins
- Whether judges favor working demos or ambitious concepts
- Oversaturated project categories
- What kind of judges this hackathon attracts (technical, business, mixed, sponsor reps)

## Step 4: Write `.hackathon/past-winners.md`

Create or overwrite `.hackathon/past-winners.md` with the following sections. Keep the entire output under 1500 words.

---

### Past Winners

| Year | Project | What It Did | Why It Won | Track/Prize |
|------|---------|-------------|------------|-------------|

Include as many winners as you can find. Add tech stack in the "What It Did" column when available. If data is sparse, say so honestly — do not fabricate entries.

### Winning Patterns

What types of projects consistently win at this hackathon:
- Technical depth vs polish vs social impact vs creative demo?
- Solo vs team?
- Common tech stacks?
- Do judges favor working demos or ambitious concepts?

### Saturated Ideas

Categories that are overdone at this hackathon or hackathons like it. Be specific: "If you build another AI chatbot / expense tracker / dashboard / todo app, you are competing with 10+ other teams who had the same idea."

### Judge Profile

What kind of judges does this hackathon typically have:
- **Technical** (engineers, CTOs) — they value architecture and technical difficulty
- **Business** (VCs, founders) — they value market potential and pitch quality
- **Mixed** — they value the demo experience above all
- **Sponsors** (company reps) — they value creative use of their API/product

State which profile applies and cite evidence (judge bios, sponsor list, past judging criteria).

### Differentiation Opportunities

Specific angles that haven't been tried, based on the winner analysis:
- "[Category X] has never won here. An entry in this space would stand out."
- "No previous winner used [trending tech Y]. First mover advantage."
- "Past winners all focused on [domain]. Going after [other domain] would be novel."
- "[Underused sponsor prize] had few submissions last year — higher odds."

### Competition Size Estimate

How many teams typically participate? Estimate from Devpost submission counts, social media, or organizer announcements. Context matters: 39 teams vs 226 teams require completely different strategies. "At this size, bringing [impressive tech] is like bringing a fighter jet to a go-kart race — or exactly right."

---

Be honest if past winner data is unavailable or incomplete. Say "Could not find winner data for [years]. Analysis is based on [N] data points." Partial data is more useful than fabricated data.

End the file with:

> Run `/hack:gen-ideas` to brainstorm ideas informed by this research.
