---
description: Script your hackathon demo with wow moment positioning and fallback plans
argument-hint: [idea name]
---

Script the exact live demo for **$ARGUMENTS**. What to show first, where the "wow moment" hits, what to fake, and fallback plans if things break.

The demo IS the product. Grand prize winners show something visceral in the first 60 seconds. ONE sentence of setup, then the demo does the work. Apply that principle here.

## Steps

1. Read `.hackathon/scope.md` to understand what is actually built vs mocked/faked.
2. Read `.hackathon/hackathon.md` for the demo time limit and track/category metadata.
3. If demo time is not specified in the metadata, ask the user: "How long is your demo slot? (e.g., 2 min, 3 min, 5 min)"
4. Script each segment of the demo with precise timestamps based on the time limit.
5. Write the full script to `.hackathon/demo-script.md` using the structure below.

## Output Structure

Write `.hackathon/demo-script.md` with ALL of the following sections. Target ~80-90 lines, under 1500 words. Lead with the SOLUTION then the problem — never inverted.

### One-Sentence Setup

Write the single sentence of context spoken before the demo starts. Format: "Every year, X happens and Y suffers." Then immediately show the product. No slides, no background, no team intros. One sentence, then demo.

### Demo Flow (timed)

Create a timed breakdown based on the demo slot length. Example for a 3-minute demo:

```
0:00-0:15  [Setup sentence + open the app]
0:15-0:45  [THE WOW MOMENT — the thing that makes judges lean forward]
0:45-1:30  [Core workflow — show the main feature working end to end]
1:30-2:00  [Second feature or deeper dive]
2:00-2:30  [Results/impact — what the user actually gets]
2:30-3:00  [Close — repeat one-liner, mention the track]
```

Scale timestamps proportionally if the demo slot is not 3 minutes. The wow moment MUST land within the first 60 seconds or serve as the climax.

### Wow Moment

Define clearly:
- **What it is**: the single most impressive thing the demo shows
- **When it hits**: timestamp in the demo flow (within first 60 seconds or as the climax)
- **How to set it up**: what must be on screen, what to click, what triggers it
- **Why it works**: "judges haven't seen X before" or "the visual is immediately visceral" — be specific

### Live vs Pre-recorded

Create a table:

| Feature | Live? | If Not, What Instead |
|---------|-------|---------------------|

For each feature in scope.md, decide: runs live in the demo, or show a video clip, or show a screenshot, or skip entirely. Be honest — if it's flaky, pre-record it. A smooth pre-recorded clip beats a broken live demo every time.

### Fallback Plan

Write concrete fallbacks:
- **Primary demo path fails**: [specific backup action]
- **API is slow or down**: [pre-recorded video of it working, with exact file path]
- **WiFi dies**: [local demo with cached/seeded data]
- **Feature X crashes**: [skip to feature Y, mention X verbally]

Every critical path in the demo needs a fallback. No "hope it works" entries.

### Setup Checklist

What must be running and visible BEFORE the demo starts:

- [ ] App running on localhost at [port]
- [ ] Browser tab open to [specific URL]
- [ ] Terminal visible with [specific command ready to paste/run]
- [ ] Demo data seeded/loaded (specify how)
- [ ] Screen resolution and font size set for projector readability
- [ ] Notifications silenced on machine
- [ ] Backup video file ready at [path]

Add or remove items based on what the project actually needs.

### Things NOT to Show

List features, screens, or flows to actively avoid during the demo:
- Half-built features that would raise questions you cannot answer
- Edge cases or inputs that cause crashes or weird behavior
- Slow operations that kill momentum (anything over 3 seconds of loading)
- Configuration screens, settings pages, or anything that is not the core value prop

Be specific. Name the exact features or flows to skip and why.

### 5 Ws and How Narrative

Weave these into the demo flow — each gets ONE sentence max, spoken naturally during transitions:
- **Who** uses this
- **What** it does
- **Where** it applies (context/industry/situation)
- **When** they need it (the trigger moment)
- **Why** it matters (the pain it removes or value it creates)
- **How** it works (one-line technical insight, only if it impresses)

Do not present these as a list during the demo. They should feel like natural narration over the live product.

## Design Rules

- The visual must be immediately impressive. Context comes from ONE sentence only.
- Lead with the solution working, then briefly mention the problem it solves.
- Never open with a slide deck, team intro, or problem statement monologue.
- If a feature takes more than one click to show, script the exact click path.
- Time every segment. No segment should be "and then we show some stuff."
- End the script with this line:

> Run `/hack:prep-pitch` to structure your pitch around this demo.
