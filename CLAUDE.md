# hstack

Hackathon command pack for Claude Code. Commands live in `.claude/commands/hack/`.

## Commands

| Command | Purpose |
|---------|---------|
| `/hack:tech-scan` | Scan trending tech and APIs, build tech context |
| `/hack:gen-ideas` | Brainstorm 5 ideas scored on hackathon dimensions |
| `/hack:stress-test` | Score one idea on 6 dimensions, build/pivot/scrap |
| `/hack:cut-scope` | Ruthless MVP scoping with timeline and build vs fake |
| `/hack:pick-track` | Analyze prize tracks, pick best submission strategy |
| `/hack:past-winners` | Research what won at this hackathon before |
| `/hack:script-demo` | Script live demo with wow moment and fallbacks |
| `/hack:prep-pitch` | Structure hackathon pitch with judge hook and Q&A |
| `/hack:split-work` | Assign parallel workstreams by skill and time |
| `/hack:plan-video` | Video production plan with Remotion prompt and Gemini voiceover |
| `/hack:write-memo` | Technical memo or LaTeX research paper |
| `/hack:write-devpost` | Devpost submission with bold formatting and 5Ws |
| `/hack:deep-research` | Deep domain research across Devpost, Twitter, GitHub |
| `/hack:full-run` | Run entire flow from tech scan to demo script |

## Conventions

- All artifacts go to `.hackathon/` folder
- Commands read `.hackathon/hackathon.md` for shared context (duration, tracks, team)
- Commands read `.hackathon/tech-context.md` for trending tech
- Each command writes one output file; re-running overwrites
- Output is under 1500 words per command

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
