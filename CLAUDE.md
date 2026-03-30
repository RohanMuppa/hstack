# hstack

Hackathon command pack for Claude Code.

## Architecture

hstack uses Skills 2.0 where possible. Key commands run as **forked subagents** with dedicated personas, tool restrictions, and persistent memory. Legacy commands in `.claude/commands/hack/` still work.

### Custom Agents (`.claude/agents/`)

| Agent | Purpose | Memory |
|-------|---------|--------|
| `hack-judge` | Ruthless 4-persona judge panel. Powers grill and stress-test. | project |
| `hack-researcher` | Deep research across Devpost, GitHub, Twitter, HN, arxiv. | project |

Agents accumulate knowledge across sessions via `.claude/agent-memory/`. The judge learns which questions trip teams up. The researcher learns what wins at specific hackathons.

### Skills 2.0 (`.claude/skills/`)

These run in **forked subagent contexts** with dynamic context injection:

| Skill | Agent | What's different from v1 |
|-------|-------|--------------------------|
| `/hack-grill` | hack-judge | Isolated context, auto-reads all `.hackathon/` files, agent memory |
| `/hack-stress-test` | hack-judge | Same judge persona, web search for novelty verification |
| `/hack-deep-research` | hack-researcher | Isolated context, persistent research memory |

### Legacy Commands (`.claude/commands/hack/`)

| Command | Purpose |
|---------|---------|
| `/hack:tech-scan` | Scan trending tech and APIs, build tech context |
| `/hack:gen-ideas` | Brainstorm 5 ideas scored on hackathon dimensions |
| `/hack:cut-scope` | Ruthless MVP scoping with timeline and build vs fake |
| `/hack:pick-track` | Analyze prize tracks, pick best submission strategy |
| `/hack:past-winners` | Research what won at this hackathon before |
| `/hack:script-demo` | Script live demo with wow moment and fallbacks |
| `/hack:prep-pitch` | Structure hackathon pitch with judge hook and Q&A |
| `/hack:split-work` | Assign parallel workstreams by skill and time |
| `/hack:plan-video` | Video production plan with Remotion prompt and Gemini voiceover |
| `/hack:write-memo` | Technical memo or LaTeX research paper |
| `/hack:write-devpost` | Devpost submission with bold formatting and 5Ws |
| `/hack:full-run` | Run entire flow from tech scan to demo script |
| `/hack:analyze-rules` | Extract submission requirements, constraints, deadlines from rules |
| `/hack:catch-cheaters` | Mass scrape submissions and analyze for cheating with parallel agents |
| `/hack:save-state` | Snapshot hackathon session state for resuming in fresh context |
| `/hack:init` | Initialize hackathon project context in current repo |

## Conventions

- All artifacts go to `.hackathon/` folder **in the project repo** (not in hstack)
- Run `/hack:init` in your project repo to set up `.hackathon/` with persistent context
- Commands/skills read `.hackathon/hackathon.md` for shared context (duration, tracks, team)
- Commands/skills read `.hackathon/tech-context.md` for trending tech
- `.hackathon/state.md` tracks session progress and persists across context windows
- Skills 2.0 auto-inject context via `!` shell commands (no manual reading needed)
- Each command writes one output file; re-running overwrites
- Output is under 1500 words per command
- To resume in a fresh context: read `.hackathon/state.md` or run `/hack:save-state` before switching

## Scoring Dimensions (used by stress-test and gen-ideas)

1. **Demo-ability** (1-5): Can you show it live in under 3 min?
2. **Novelty** (1-5): Have judges seen this before?
3. **Theme Fit** (1-5): Aligned with hackathon theme and tracks?
4. **Build Feasibility** (1-5): Can your team build it in time?
5. **Wow Factor** (1-5): Does it make people lean forward?
6. **Pitch Clarity** (1-5): Can you explain it in one sentence?

Verdicts: BUILD (25-30), PIVOT (18-24), SCRAP (<18)

## Hard Rules

- Prototype done 3 hours before presentation. Always.
- Lead with solution, then problem. In demos and videos. Not inverted.
- Never optimize for business viability over demo impact. Judges don't care about TAM.
- The Judge Test: "Does a judge walk up, watch 2 minutes, and think 'that's one of the 3 coolest things I've seen today'?"
- Brainstorming, not specs. Don't produce architecture fiction.

## Devpost MCP

Separate repo: https://github.com/RohanMuppa/devpost-mcp-server
Configure it via npx in your Claude Code MCP settings to give `/hack:past-winners` and `/hack:deep-research` structured access to Devpost data.

## TODO

### /hack:find-papers — Research paper discovery for hackathon ideas
Find relevant academic papers and extract implementable ideas. Not to cite or use their code, but to steal mental models and have credible technical backing for your pitch.

What it would do:
- Take your hackathon idea as input
- Search for related papers (arxiv, Semantic Scholar, Google Scholar)
- For each paper: extract the one transferable idea, whether it provides usable code/architecture, and the "judge credibility sentence" (one sentence you can say in a pitch that sounds informed)
- Flag papers with open source implementations vs theory only

Needs: an academic paper API or MCP. Options to evaluate:
- Semantic Scholar API (free, no key needed, good search + citation data)
- arxiv API (free, search + full text)
- Existing MCP: search for "arxiv mcp" or "semantic scholar mcp" on GitHub
- Could also use Perplexity or web search as a fallback