# Current Trends, Technologies, Frameworks, and APIs

*Last updated: March 2026*

This file tracks what's hot right now. Used by `/hack:tech-scan` and `/hack:gen-ideas` as baseline context. Update this as the landscape shifts.

## Models and APIs

| Model/API | What's New | Why It Matters for Hackathons |
|-----------|-----------|-------------------------------|
| Claude Opus 4.6 | 1M context window, 128K output | Build complex multi-file agents in one session |
| Gemini 3.1 Pro | $2/$12 pricing, ARC-AGI-2 score 77.1% | Cheap multimodal reasoning |
| Gemini 3 Flash | $0.50/M tokens | Extremely cheap for high-volume inference |
| Gemini Live API | Native audio input/output, real-time | Voice/video agents that see, hear, and speak |
| GPT-5.3 Codex | Fastest agentic coding model | Speed-oriented agentic tasks |
| Gemini Veo | Video generation | 5-10 sec cinematic hero shots for demo videos |

## Protocols

| Protocol | What It Does | Status |
|----------|-------------|--------|
| MCP (Model Context Protocol) | Agent-to-tool communication | 97M monthly SDK downloads. Adopted by every major AI provider. |
| A2A (Agent-to-Agent) | Agent-to-agent discovery and communication | v0.3 with gRPC support. Linux Foundation backed. Google origin. |
| ADK (Agent Development Kit) | Google's agent builder framework | Used in Gemini Live Agent Challenge |

## Frameworks and Tools

| Tool | Stars/Traction | What It Does |
|------|---------------|-------------|
| OpenClaw | 210K+ stars | Agent framework by Peter Steinberger |
| Superpowers | 106K+ stars | TDD-first Claude Code skill pack |
| gstack | 39K+ stars | Role-based Claude Code skills (Garry Tan) |
| everything-claude-code | 50K+ stars | Hackathon-winning Claude Code setup |
| Context7 | #1 MCP server | Real-time library docs for AI |
| Playwright MCP | Top 5 MCP server | Browser automation for agents |
| Remotion | Programmatic video | Create demo videos from code via MCP |
| Screen Studio | Mac recording app | Auto-zoom screen recording for demos |

## Hackathon Winner Patterns (Early 2026)

| Pattern | Example | Why It Wins |
|---------|---------|-------------|
| Multi-agent consensus | Multiple hackathon winners | Multiple agents debating/synthesizing feels like a "real system" |
| Real-time voice/video | ARETE (NexHacks) | Visceral demos that judges can interact with |
| 3D visualization | Multiple hackathon winners | Immediate wow factor, judges haven't seen it before |
| Phone as sensor | Various spatial AI projects | Accessible hardware, no special equipment needed |
| Spatial AI | Recent grand prize winners | 3D spatial reasoning is a consistent winning pattern |
| Deep domain research | CropSync (Aryan Shanker) | Week-long stakeholder research before building |

## Infrastructure Trends

| Trend | What's Happening |
|-------|-----------------|
| Multi-agent orchestration | Every major tool shipped it Feb 2026. Table stakes now. |
| Browser automation MCPs | 3 of top 10 MCP servers are browser tools |
| Post-quantum crypto | Google testing in Chrome |
| ARM AI chips | ARM launched first proprietary AI chip for data centers |
| AI agent payments | Stripe x402 for machine-to-machine payments |

## What Judges Care About (March 2026)

From studying HackIllinois, NexHacks, MCP Hackathon, and Gemini Live Agent Challenge winners:

1. **Technical wow**: "How did you build that in N hours?"
2. **Working demo**: Not slides, not mockups. Running code.
3. **Novelty**: Something they haven't seen 10 times already.
4. **Visceral reaction**: The demo makes them lean forward.
5. **Clear explanation**: One sentence, a non-technical judge gets it.

What they do NOT care about (at stage 1):
- TAM, revenue models, unit economics
- Business plans, go-to-market strategy
- Polish at the expense of innovation

## Common Mistakes Winners Avoid

From studying what separates winners from the other 200+ teams:

- **Building before scoping.** Teams that jump into code without a scope doc waste hours building features they cut at hour 20.
- **No demo script.** They build something cool but fumble the 3-minute demo because they never rehearsed. The demo IS the product.
- **Over-scoping.** "We'll build a full platform with auth, payments, and a dashboard." No you won't. Winners ship one feature that works flawlessly.
- **Skipping sponsor APIs.** The team that integrates the sponsor's API thoughtfully wins the sponsor track. The team that ignores it doesn't.
- **Explaining instead of showing.** Spending 90 seconds of a 3-minute demo on slides. Judges want to see it run, not hear about it.
- **Optimizing for business viability.** Pitching TAM and revenue models at stage 1. Judges stack-rank on gut feeling, not spreadsheets.
- **No fallback plan.** The live demo breaks on stage. No backup video, no pre-recorded path, nothing. Winners always have a plan B.
- **Starting polish too early.** Perfecting the UI at hour 12 when core functionality isn't done. Polish the last 3 hours, not before.
- **Solo heroics instead of parallel work.** One person does everything while teammates wait. Winners split workstreams with clear interfaces from hour 1.
