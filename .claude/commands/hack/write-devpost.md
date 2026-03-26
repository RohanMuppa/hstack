---
description: Write your Devpost submission with bold problem/solution and 5Ws format
argument-hint: [idea name]
---

Write a complete Devpost hackathon submission draft for: $ARGUMENTS

## Step 1: Read all hackathon artifacts

Read every file in the `.hackathon/` directory to gather context. Specifically look for:

- `.hackathon/hackathon.md` — event name, dates, theme, sponsors, judging criteria
- `.hackathon/validation/` — all files in this directory for idea validation, user research, problem framing
- `.hackathon/scope.md` — final feature set, tech stack, MVP boundaries
- `.hackathon/tracks.md` — which track(s) we're targeting and the angle for each
- `.hackathon/demo-script.md` — demo flow, what to highlight, wow moments
- `.hackathon/technical-memo.md` — architecture decisions, tradeoffs (if it exists)

If a file doesn't exist, skip it and work with what's available. Do NOT hallucinate details that aren't in the artifacts.

## Step 2: Generate the Devpost submission

Use the information gathered to write the full submission. Follow these rules strictly:

### Formatting Rules (NON-NEGOTIABLE)
- **First two sentences** of the "Inspiration" section MUST be **bold**. Lead with "Simply put" or equivalent.
- **First two sentences** of the "What it does" section MUST be **bold**.
- After the bold sentences, you can continue writing but separate them with a line break and do NOT bold the rest.
- Weave the 5 Ws and How naturally through the sections:
  - **Who** → Inspiration (who has this problem)
  - **What** → What it does (what the project is)
  - **How** → How we built it (tech and process)
  - **When** → How we built it (timeline)
  - **Why** → Throughout, especially Inspiration
  - **Where** → Try it out (links, access)
- Each W must be backed by research or context from the artifacts, not filler.
- No generic platitudes. Every sentence carries information or gets cut.
- Total output: ~80-90 lines, under 1500 words.

### Required Sections

Write these sections in this exact order:

**Project Title** — Catchy, memorable, searchable. Derive from the idea name and artifacts.

**Tagline** — One sentence. Format: "Simply put, [what it does] for [who]."

**Inspiration (What/Why)** — **Bold the first two sentences. Lead with "simply put" or equivalent.** Then elaborate: what problem, why it matters, back it with a stat or testimonial from validation artifacts.

**What it does (What/How)** — **Bold the first two sentences.** Then describe core functionality. What can a user do? What do they see? Reference the demo script.

**How we built it (How/When)** — Tech stack with brief justification for each choice. Architecture overview in 1-2 sentences. Timeline: what was built when during the hackathon.

**Challenges we ran into** — 2-3 real, specific challenges from the build. "We spent 4 hours debugging X because Y" beats "It was hard." Pull from technical-memo if available.

**Accomplishments that we're proud of** — 2-3 specific achievements. Tie to the wow factor from the demo script.

**What we learned** — 1-2 genuine learnings. Not "we learned teamwork is important."

**What's next** — 2-3 concrete next steps. Not a 5-year roadmap.

**Built With** — Comma-separated tech list matching Devpost tag format (lowercase, no versions). Pull from scope.md.

**Try it out** — GitHub link, demo video link, live demo link (if applicable). Use placeholders if links aren't in artifacts yet.

## Step 3: Write the output

Write the completed draft to `.hackathon/devpost-draft.md`.

After writing, print:

> Copy this into your Devpost submission. Adjust team member names and links.
