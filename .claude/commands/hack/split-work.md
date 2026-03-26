---
description: Assign parallel workstreams to team members based on skills and time remaining
argument-hint: [hours remaining]
---

Read `.hackathon/hackathon.md` for team info (names, skills) and `.hackathon/scope.md` for the feature list and architecture.

If team members and skills are not listed in hackathon.md, ask: "List team members and their primary skills (e.g., 'Alice - backend/Python, Bob - frontend/React, Carol - ML/infra')."

The user has provided hours remaining: $ARGUMENTS. If blank or unclear, ask: "How many hours until presentations?"

Using the team roster, feature scope, and time remaining, generate a workstream plan and write it to `.hackathon/team-plan.md`.

Follow this structure exactly:

---

# Team Plan

## Team Roster

| Name | Primary Skill | Secondary Skill | Role |
|------|--------------|----------------|------|
| (fill from metadata or user input) | | | |

Assign roles like: backend lead, frontend lead, infra/deploy, ML/AI, integration lead, demo prep.

## Workstreams

For each person or pair, create a block:

**[Name]: [Workstream Title]**
- Build order: what to do first, second, third
- Deliverables: specific files, endpoints, components, or scripts they own
- Dependencies: "Needs [X] from [other person] by hour [N]"

Make workstreams as independent as possible. The goal is people working in parallel without stepping on each other. Think like real hackathon splits:
- One person owns the backend API and data layer
- One person owns the frontend/UI
- One person owns the AI/ML pipeline or core logic
- One person owns infra, deploy, demo video, or a secondary feature (bot, CLI, etc.)

If the team is 2 people, split by frontend vs backend. If 3+, consider giving someone a vertical slice (e.g., a standalone bot or CLI that talks to the same API).

## Interfaces

Define exactly where workstreams connect. Be specific — vague interfaces cause integration disasters at hour 20.

- **API contracts**: "[Backend person] exposes `POST /api/endpoint` returning `{ field: type }` by hour N"
- **Shared state**: "Both use `[file/table/store]` with `[format/schema]`"
- **UI components**: "[Frontend person] builds `<Component>` that consumes `[endpoint or prop shape]`"
- **Environment**: shared env vars, config files, or secrets that everyone needs

If an interface isn't decided yet, flag it: "DECIDE NOW: what format does [X] return?"

## Sync Points

Specific hours where the team MUST stop and sync:

- **Hour [N]**: Interfaces locked. Backend stubs exist, frontend can call them.
- **Hour [M]**: First end-to-end test. Frontend calls real backend, data flows through.
- **Hour [P]**: Feature freeze. No new features, only bug fixes and polish.
- **Hour [Q]**: Integration + demo rehearsal. Run through the full demo once.
- **Final 30 min**: Demo prep — slides, talking points, screen recording backup.

Work backwards from presentation time. The last 3 hours are sacred: feature freeze, integration, demo prep. Plan workstreams to deliver core features BEFORE that window.

## If Someone Gets Blocked

For each person, define a fallback:
- [Person A] blocked on [X] → drops it, switches to help [Person B] with [specific task]
- [Feature Y] taking too long → cut it, [Person] switches to [fallback task that still makes demo work]
- Integration failing → everyone stops their workstream, fix the shared interface first
- Someone finishes early → pick up [stretch goal] or help with demo polish

## Parallel vs Sequential

**Can be built independently (parallel):**
- (list tasks that have no dependency on each other)

**Must be sequential:**
- (list tasks with their order and why)

---

Keep the plan under 1500 words. Be specific about deliverables and interfaces — name the files, endpoints, schemas, and components. Every workstream should know exactly what they produce and what they consume from others.

End the plan with:

> Sync with your team on these assignments, then start building.
