---
description: Analyze prize tracks and pick the best submission strategy for your idea
argument-hint: [idea name]
---

# Pick Track

Analyze all hackathon prize tracks and recommend the best submission strategy for the idea: **$ARGUMENTS**

## Step 1: Load Track Info

Read `.hackathon/hackathon.md` for the list of prize tracks. Each track should have: name, sponsor, prize amount, requirements, and judging criteria.

If tracks are missing or the file does not exist, stop and ask the user:

> I need the prize track info. Please list each track with: **track name**, **sponsor**, **prize**, and **requirements/judging criteria**. I'll save them to `.hackathon/hackathon.md`.

## Step 2: Load the Idea

Find the idea from:
1. The `$ARGUMENTS` if provided
2. Files in `.hackathon/validation/`
3. `.hackathon/ideas.md`

If no idea is found, ask the user to describe it in one sentence.

## Step 3: Analyze Every Track

For each track, evaluate honestly:
- **Fit (1-5)**: How naturally does the idea align with this track's requirements?
- **Competition (Low/Med/High)**: How many other teams will target this? Be blunt. "Best Use of [popular API]" is always High.
- **Required Integration**: What specific APIs, SDKs, or tools MUST be used to qualify?
- **Your Angle**: What framing of the idea makes it compelling for this track?

## Step 4: Output

Write the full analysis to `.hackathon/tracks.md` and display it. Use this exact format:

---

### Track Analysis

| Track | Prize | Fit (1-5) | Competition | Required Integration | Your Angle |
|-------|-------|-----------|-------------|---------------------|------------|
| ... | ... | ... | L/M/H | ... | ... |

### Recommended Strategy

- **Primary Track**: [name] -- highest expected value (fit x prize / competition)
- **Fallback Track**: [name] -- hedge if primary is too competitive
- **Why**: one sentence justification for each pick

### Required Integrations

For the recommended track(s), list exactly what needs to be built:

| API/Tool | What to Use It For | Depth Needed | Estimated Hours |
|----------|-------------------|--------------|-----------------|
| ... | ... | Deep/Surface | ... |

"Deep" = core of your project depends on it. "Surface" = show it briefly in the demo, mention in writeup.

### Submission Checklist

What the recommended tracks require:

- [ ] Public GitHub repo
- [ ] Demo video (note required length if specified)
- [ ] Devpost description addressing the track criteria
- [ ] Specific API usage demonstrated
- [ ] Any other track-specific requirements

---

## Rules

- Keep output under 1200 words.
- Be honest about competition. Telling the team "this track is easy to win" when it isn't wastes hours.
- If the idea does not fit ANY track well (no track scores above 2), say so clearly and suggest one concrete pivot per top-3 track.
- Do not invent track information. Only use what is in `.hackathon/hackathon.md` or what the user provides.
- Always end with: **Next step**: Run `/hack:cut-scope` to plan what to build, or `/hack:script-demo` to plan your demo.
