---
description: Plan your demo video with Gemini voiceover, Remotion config, and Screen Studio tips
argument-hint: [idea name]
---

# Plan Demo Video for "$ARGUMENTS"

You are a hackathon demo video producer. Plan a 3-minute Devpost submission video that leads with the SOLUTION, uses pro-grade tooling (Gemini TTS, Remotion MCP, Screen Studio), and is designed to win.

## Step 1: Read Context

Read these files (skip any that don't exist):
- `.hackathon/demo-script.md` — the live demo flow (reuse structure for video)
- `.hackathon/scope.md` — tech stack, problem statement, solution one-liner

Extract:
- **Solution one-liner** (first thing viewers hear)
- **Problem context** (second — NOT first)
- **Core demo steps** (what to screen-record)
- **Tech stack** (for architecture diagram)
- **Impact stats or testimonials** (if available)

## Step 2: Plan Video Structure

Write `.hackathon/video-plan.md` with ALL of the following sections.

### Video Structure (timed for 3 min)

Use this exact timeline template, filling in project-specific details:

```
0:00-0:05  Cinematic hero shot (Gemini Veo, 5 sec) — [describe visual]
0:05-0:15  Solution statement (voiceover + product screenshot)
0:15-0:25  Problem context (voiceover + testimonial or stat)
0:25-1:45  Core demo (Screen Studio recording, auto-zoom on key actions)
1:45-2:15  Technical architecture diagram (Remotion animated build-up)
2:15-2:40  Impact / results (stats, quotes, before/after)
2:40-2:55  What's next / team intro
2:55-3:00  Logo + solution one-liner
```

Customize each segment description to the actual project.

### Voiceover Script

Write a full transcript with timestamps. Rules:
- Written for Gemini TTS — clear, confident, slight bass tone
- Every line tagged with `[ON SCREEN: ...]` describing what viewers see
- Lead with solution, then problem
- Use short sentences (TTS reads them better)
- End with a memorable one-liner
- Target ~400 words (about 3 min at natural pace)

Format each line as:
```
[0:05] "Here's what $ARGUMENTS does." [ON SCREEN: product hero screenshot]
```

### Production Checklist

```markdown
- [ ] Record demo with Screen Studio (enable auto-zoom, cursor highlight, 1920x1080)
- [ ] Generate 5-sec hero shot with Gemini Veo (prompt below)
- [ ] Generate voiceover with Gemini TTS (script above)
- [ ] Create tech stack architecture diagram (Excalidraw or tldraw, then animate in Remotion)
- [ ] Add subtitles (auto-caption or burn in with Remotion)
- [ ] Optional: Record judge interaction clip (ask a judge for a prompt, demo it live)
- [ ] Optional: Add problem testimonial (email screenshot, call quote, stat graphic)
- [ ] Assemble final cut with Remotion MCP or simple editor (CapCut/iMovie as fallback)
```

### Gemini Veo Prompt

Provide a ready-to-paste prompt for generating the cinematic intro:

```
Generate a [5-10] second cinematic video:
[Describe a visually striking scene that metaphorically represents the project's domain.
Be specific — camera movement, lighting, color palette, mood.]
Style: cinematic, shallow depth of field, smooth camera motion.
No text overlays. No people unless relevant. 16:9 aspect ratio.
```

Fill in the bracketed parts based on the project.

### Gemini TTS Instructions

```
Model: Gemini 2.5 Flash (or latest with TTS)
Voice: Use a deep, confident male voice (or specify if project has brand voice)
Settings: Slightly slower pace (0.9x), bass emphasis
Input: Copy the voiceover script section above
Output: Single MP3 file, export at 44.1kHz
Tip: Break script into paragraphs for natural pauses. Regenerate any line that sounds rushed.
```

### Screen Studio Settings

```
Resolution: 1920x1080
Auto-zoom: ON (follows cursor, highlights clicks)
Cursor highlight: ON (subtle glow)
Background: Gradient or solid matching project brand colors
Padding: 16px around window
Export: ProRes or H.264 at 60fps
Tip: Do 2-3 takes. Rehearse the demo-script.md flow first. Hide desktop icons and notifications.
```

## Step 3: Generate Remotion Prompt

Write `.hackathon/remotion-prompt.md` with a ready-to-use prompt for the Remotion MCP.

Structure it as a scene list with exact timings:

```
Create an animated video with these scenes:

1. Hero shot (0:00-0:05) — Fade in from black. Display Gemini Veo clip full-screen.
2. Title card (0:05-0:08) — Project name + one-liner. Slide in from left, white text on dark bg.
3. Solution statement (0:08-0:15) — Voiceover plays. Show product screenshot with subtle ken-burns zoom.
4. Problem context (0:15-0:25) — Stat or testimonial graphic. Fade in text elements one by one.
5. Demo recording (0:25-1:45) — Full-width Screen Studio recording. Subtle 1.02x slow zoom in.
6. Tech stack diagram (1:45-2:15) — Animated build-up. Each layer/service appears with a pop. Labels fade in.
7. Impact stats (2:15-2:35) — Numbers count up from 0. Large font, centered.
8. Team + next steps (2:35-2:55) — Names, roles, GitHub/links. Slide in from bottom.
9. End card (2:55-3:00) — Logo centered, one-liner below, fade to black.

Global config:
- Transitions: 0.5s crossfade between all scenes
- Audio track: Gemini TTS voiceover (import as MP3)
- Subtitles: Burned in, white text, dark shadow, bottom-center
- Resolution: 1920x1080 @ 30fps
- Font: Inter or system sans-serif
- Color palette: [derive from project brand or use neutral dark theme]
```

Fill in all project-specific details from scope.md and demo-script.md.

## Step 4: Final Output

After writing both files, print a summary:
- Confirm `.hackathon/video-plan.md` and `.hackathon/remotion-prompt.md` were created
- List the video segments with timings
- Call out any missing inputs (no demo-script.md? no scope.md? no testimonials?)
- End with: **"Record your demo with Screen Studio first, then assemble with Remotion."**
