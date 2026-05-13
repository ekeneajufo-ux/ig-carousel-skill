# HyperFrames Carousel Skill — PracticeRx

Build animated 8-slide Instagram carousels with Claude Code + HyperFrames. Paste or describe content — the skill writes all slides, renders MP4s, and prints the caption inline. Zero variable-filling required.

## Quick Start

```
/carousel
```

Paste a blog post, bullet points, or just describe the topic. The skill reads context and builds immediately.

## What It Delivers

- 8 animated MP4 slides (720×900 @ 30fps)
- Phone-mockup HTML previewer at `output/preview.html`
- Caption + hashtags printed inline in the response (copy-paste ready)

## Design System

| Token | Value |
|-------|-------|
| Light bg | #F5EDE3 (warm cream) |
| Dark bg | #1A2744 (deep navy) |
| Accent | #C09843 (warm gold) |
| Headlines | Bebas Neue, ALL CAPS, 85–120px |
| Body | DM Sans italic, 18–20px |
| Dimensions | 720×900, 30fps |

## Slide Arc

| # | Role | Background |
|---|------|------------|
| 1 | Hook + text swap | Cream |
| 2 | Pain | Navy |
| 3 | Solution | Cream |
| 4 | How it works | Navy |
| 5 | Why it matters | Gold gradient |
| 6 | Scale / proof | Cream |
| 7 | Before / after | Navy |
| 8 | CTA | Gold gradient |

## Prerequisites

- `npm install -g hyperframes` (HyperFrames CLI)
- `npm install -g ffmpeg-static` (for video render)

## Files

| File | Purpose |
|------|---------|
| `../../commands/carousel.md` | Skill prompt — loaded when `/carousel` is invoked |
| `DESIGN.md` | Full PracticeRx design token reference |
| `README.md` | This file |
