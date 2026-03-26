---
description: Structure your hackathon pitch for judges with a memorable hook and Q&A prep
argument-hint: [idea name]
---

# Prep Hackathon Pitch: $ARGUMENTS

You are structuring a 3-5 minute hackathon demo pitch. This is NOT an investor pitch. No TAM slides, no revenue models, no business fluff.

Hackathon judging reality:
- Judges do NOT score on a rubric. They stack rank favorites. It is gut feeling.
- The question is: "Does a judge think 'that's one of the 3 coolest things I've seen today'?"
- If there is a Shark Tank stage 2, business stuff matters there. Stage 1 is creativity + execution.
- The demo IS the pitch. Structure around showing, not telling.

## Step 1: Gather Context

Read the following files if they exist (skip any that don't):
- `.hackathon/demo-script.md` — what the demo flow looks like
- `.hackathon/scope.md` — what was actually built
- `.hackathon/tracks.md` — which tracks are being targeted and their criteria

Summarize what you learned in 2-3 sentences before proceeding.

## Step 2: Structure the Pitch

Write the full pitch outline to `.hackathon/pitch-outline.md` with these sections:

### One-Liner (memorize this)
One sentence that explains the entire project. Must pass the "told at a party" test — if someone who knows nothing about tech hears it, they get it and think it is cool.

### Judge Hook
The ONE thing you want judges to remember after seeing 50 projects. Pick one format:
- A statistic: "X costs $Y per Z"
- A comparison: "We do in 30 seconds what takes 3 hours"
- A "what if" framing: "What if your phone could see through walls?"

This is the single data point or framing that sticks in their brain during deliberation.

### Pitch Structure (timed for 3-min pitch)

```
0:00-0:20  Hook + problem (ONE sentence of context, then the judge hook)
0:20-0:40  Solution (ONE sentence, then SHOW it)
0:40-2:00  Live demo (this is 60% of your pitch — show the thing working)
2:00-2:30  How it works (brief technical architecture, 1 diagram max)
2:30-2:50  Impact / what's next (keep grounded, no fantasy scale claims)
2:50-3:00  Close — repeat the one-liner
```

If the pitch is 5 minutes, expand the demo to 3:00 and add 30s to technical architecture.

### Slides (if used, max 5)

| Slide | Content | Time |
|-------|---------|------|
| 1 | Hook + problem statement | 0:00-0:20 |
| 2 | Solution one-liner + transition to demo | 0:20-0:40 |
| 3 | LIVE DEMO (screen share, no slides) | 0:40-2:00 |
| 4 | Architecture diagram | 2:00-2:30 |
| 5 | Impact + closing one-liner | 2:30-3:00 |

Most of the pitch IS the demo. Slides are scaffolding, not the main event.

### Q&A Prep

Provide concise answers (2-3 sentences max each) for these 5 likely judge questions:
1. "How does [core technical thing] work?" — explain simply, no jargon dump
2. "What's the hardest technical challenge you solved?" — show depth, pick ONE thing
3. "How is this different from [existing thing]?" — acknowledge it exists, explain your angle
4. "What would you do with more time?" — show you have vision but shipped what matters
5. "Who would use this?" — name a specific person or scenario, not a market segment

### Track-Specific Angles

If `.hackathon/tracks.md` exists and the project targets multiple tracks, write a short section:
- For [Track A]: emphasize X aspect of the project
- For [Track B]: emphasize Y aspect of the project

Explain what to adjust in the pitch (which hook, which demo moment) for each track.

## Output Rules

- Keep the full pitch outline to roughly 80-90 lines
- Stay under 1500 words total
- Zero business fluff: no TAM, no revenue projections, no CAC, no market sizing
- Every section should be concrete and specific to this project, not generic advice
- The demo section should reference actual features from the demo script or scope

End the file with:

> Rehearse this 3 times before presenting. Time yourself.
