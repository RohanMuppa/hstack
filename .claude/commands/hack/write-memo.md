---
description: Generate a polished technical memo or LaTeX research paper for your hackathon project
argument-hint: [idea name or "latex" for LaTeX format]
---

Generate a technical memo or research paper for this hackathon project.

## Instructions

You are writing a polished technical writeup of the hackathon project. This is inspired by the Shire AI Technical Memo and NexHacks ML restaurant team's LaTeX paper. The goal: produce something worth attaching to a Devpost submission, sending to sponsors, or adding to a portfolio. Most teams submit a README. You are not most teams.

### Step 1: Gather context

Read all `.hackathon/` artifacts to understand the project:
- `.hackathon/scope.md` (what the project is, goals, constraints)
- `.hackathon/validation.md` (what was tested, outcomes)
- `.hackathon/demo-script.md` (the demo flow)
- `.hackathon/tracks.md` (sponsor tracks being targeted)

Then scan the codebase for architecture context:
- Look for `package.json`, `requirements.txt`, `go.mod`, `Cargo.toml`, or similar to identify the tech stack
- Read main entry points and key modules to understand the architecture
- Identify the most technically interesting code (novel algorithms, clever integrations, hard problems solved)

If any artifacts are missing, work with what exists. Do not hallucinate details.

### Step 2: Determine output format

Check the argument: **$ARGUMENTS**

- If the argument contains "latex" (case-insensitive), output LaTeX format to `.hackathon/technical-memo.tex`
- Otherwise, output Markdown format to `.hackathon/technical-memo.md`

### Step 3: Write the memo

Produce the following sections. Every section is mandatory unless the project genuinely lacks content for it (e.g., no references needed).

---

**Abstract** (3-4 sentences)
State what the project does, the core technical approach, and the key result. No filler. No "In this paper we present..." throat-clearing. Lead with the problem or the insight.

**1. Problem**
- The specific problem being addressed
- Why it matters — include one concrete stat, data point, or testimonial if available from the hackathon artifacts
- Current approaches and their limitations (what exists today and why it falls short)

**2. Approach**
- High-level solution description in 2-3 paragraphs
- Why this approach was chosen over alternatives (what was considered and rejected, and why)
- Key design decisions and tradeoffs made during the hackathon

**3. Architecture**
- System architecture diagram — use ASCII art for Markdown, TikZ or a described figure for LaTeX
- Component breakdown: list each major component and its responsibility
- Data flow description: input -> processing -> output, traced through the system
- Tech stack table with three columns: Component | Technology | Why (justification for each choice)

**4. Implementation**
- Key technical challenges encountered and how they were solved
- Novel techniques, algorithms, or integration patterns used
- 2-3 code snippets showing the most interesting parts (the parts a technical reviewer would want to see)
- Keep snippets short and annotated with comments explaining what matters

**5. Results**
- What works, with evidence: reference demo outcomes, metrics, screenshots described in artifacts
- Performance characteristics if relevant (latency, accuracy, throughput, cost)
- Clearly separate what was validated from what remains a hypothesis — label hypotheses explicitly

**6. Future Work**
- What you would build with another week (not "more time" — be specific)
- Known limitations and failure modes
- Scaling considerations: what breaks first if usage grows 100x

**References** (if applicable)
Papers, APIs, datasets, open-source projects used. Use consistent citation format.

---

### Design rules — follow these strictly

- Target length: ~1500-2000 words. Substantive but not bloated. If a section has nothing meaningful to say, keep it to 2-3 sentences rather than padding.
- Write like a technical professional. No "In conclusion," no "We hope to," no "This project aims to." State facts. Describe systems. Present evidence.
- Every claim must have evidence from the codebase or artifacts, or be explicitly marked as **[hypothesis]**.
- For Markdown output: use clean headers, tables, and fenced code blocks.
- For LaTeX output: use `article` document class, `11pt` font, standard `\section{}` hierarchy. Include a title block with project name, team members (from artifacts if available), and date. Use `listings` package for code snippets, `booktabs` for tables.

### Step 4: Final line

After writing the file, end your response with:

> Memo written to `.hackathon/technical-memo.{md,tex}`. Attach this to your Devpost submission or share with sponsors.
