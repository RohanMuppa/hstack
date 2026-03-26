# hstack

Hackathon command pack for Claude Code. Centralizes the research, ideation, planning, and presentation work that surrounds actually building your project. How Devpost submissions are formatted, how demo videos are structured, what tools winners use, what mistakes and pitfalls they avoid. All of it, kept current as trends and winners change.

See [PHILOSOPHY.md](PHILOSOPHY.md) for the full rationale.

## Install

**Per project (recommended):**
```bash
git clone https://github.com/yourusername/hstack.git /tmp/hstack
cp -r /tmp/hstack/.claude/commands/hack your-project/.claude/commands/hack
cp /tmp/hstack/CLAUDE.md your-project/CLAUDE.md
```

**Global (available everywhere):**
```bash
git clone https://github.com/yourusername/hstack.git ~/.hstack
ln -s ~/.hstack/.claude/commands/hack ~/.claude/commands/hack
```

**Devpost MCP (optional, for structured winner data):**

Separate repo: [devpost-mcp-server](https://github.com/RohanMuppa/devpost-mcp-server)

```bash
npx devpost-mcp-server
```

## Quick Start

Run the full flow:
```
/hack:full-run HackIllinois 2026
```

Or run individual commands:
```
/hack:tech-scan              # What tech is hot right now?
/hack:gen-ideas              # Brainstorm 5 scored ideas
/hack:stress-test my idea    # Score it, get build/pivot/scrap
/hack:cut-scope              # What to build, what to fake
/hack:pick-track             # Which prize track to target
```

## All Commands

### Ideation
| Command | What it does |
|---------|-------------|
| `/hack:tech-scan` | Scan trending tech and APIs at the hackathon |
| `/hack:gen-ideas` | Brainstorm 5 ideas scored on 6 hackathon dimensions |
| `/hack:stress-test` | Deep score one idea, build/pivot/scrap verdict |
| `/hack:deep-research` | Research a domain across Devpost, Twitter, GitHub |

### Planning
| Command | What it does |
|---------|-------------|
| `/hack:cut-scope` | Must/Should/Won't Have + build vs fake + timeline |
| `/hack:pick-track` | Analyze prize tracks, pick best submission strategy |
| `/hack:past-winners` | Research what won before, find differentiation angles |
| `/hack:split-work` | Assign parallel workstreams to team members |

### Presentation
| Command | What it does |
|---------|-------------|
| `/hack:script-demo` | Script live demo with wow moment and fallbacks |
| `/hack:prep-pitch` | Structure pitch with judge hook and Q&A prep |
| `/hack:plan-video` | Video production plan with Remotion prompt |

### Submission
| Command | What it does |
|---------|-------------|
| `/hack:write-devpost` | Devpost draft with bold formatting and 5Ws |
| `/hack:write-memo` | Technical memo or LaTeX paper |

### Full Flow
| Command | What it does |
|---------|-------------|
| `/hack:full-run` | Run entire pipeline: scan, ideate, validate, scope, track, demo |

## Scoring System

Ideas are scored on 6 hackathon dimensions (not startup dimensions):

| Dimension | Question |
|-----------|----------|
| Demo-ability | Can you show it live in 3 minutes? |
| Novelty | Have judges seen this before? |
| Theme Fit | Aligned with hackathon theme/tracks? |
| Build Feasibility | Can your team build it in time? |
| Wow Factor | Does it make people lean forward? |
| Pitch Clarity | Can you explain it in one sentence? |

**BUILD** (25-30) | **PIVOT** (18-24) | **SCRAP** (<18)

## Output

All artifacts save to `.hackathon/` in your project:

```
.hackathon/
  hackathon.md          # Event metadata (shared by all commands)
  tech-context.md       # Trending tech scan
  ideas.md              # 5 ranked ideas
  validation/           # Per-idea stress tests
  scope.md              # Build plan + timeline
  tracks.md             # Prize track strategy
  past-winners.md       # Winner research
  demo-script.md        # Demo script
  pitch-outline.md      # Pitch structure
  team-plan.md          # Workstream assignments
  video-plan.md         # Video production plan
  remotion-prompt.md    # Ready-to-use Remotion config
  technical-memo.md     # Technical writeup
  devpost-draft.md      # Devpost submission
  research.md           # Domain research
```

## Philosophy

- **Zero preamble.** No telemetry, no update checks, no philosophy essays.
- **Hackathon scoring, not startup scoring.** Judges care about demos, not TAM.
- **The Judge Test.** "Does a judge watch 2 minutes and think 'coolest thing I've seen'?"
- **3 hours before.** Prototype done 3 hours before presentation. Always.
- **Solution first.** Lead with what you built, then explain the problem.

## Devpost MCP

Separate repo: [devpost-mcp-server](https://github.com/RohanMuppa/devpost-mcp-server)

Gives Claude structured access to Devpost data. Use cases:

- Search for projects that use a specific API (e.g., "show me hackathon projects using LiveKit")
- Find recent winners of a specific hackathon and what tools and frameworks they used
- See what tech stacks are trending across winning projects
- Research how top submissions structured their Devpost pages
- Find projects in a specific domain to check if your idea has been done before

Used by `/hack:past-winners` and `/hack:deep-research` when configured.

## License

MIT
