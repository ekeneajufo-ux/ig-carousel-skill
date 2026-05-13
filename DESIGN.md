# Design System — PracticeRx Animated Carousel

## Style

Warm editorial. Billboard Bebas Neue headlines on alternating cream/navy/gold backgrounds. Deep navy creates authoritative gravitas; warm gold signals premium expertise. Terminal mockups and data callouts as visual proof elements. Clean generous padding. Medical-professional, trust-building — not tech-startup.

## Colors

| Role | Hex | Notes |
|------|-----|-------|
| Light background | #F5EDE3 | Warm cream — site primary bg |
| Card / surface | #FFFAF4 | Lighter cream for data cards |
| Dark background | #1A2744 | Deep navy — authority, trust |
| Text on light | #1A2744 | Navy |
| Text on dark | #FFFFFF | White |
| Accent / gold | #C09843 | Brand gold — logo, accent phrases |
| Accent dark / bronze | #7A6030 | Darker gold for labels on light bg |
| Section label on light | #7A6030 | Bronze |
| Section label on dark | #C09843 | Gold |
| Gold gradient | linear-gradient(145deg, #C09843 0%, #8B6914 100%) | Slides 5 + 8 |
| Danger / before | #8B2020 | Dark red for before-state cards |
| Terminal bg | #0F1A30 | Deep navy-black |
| Swap alt | #5B8AB0 | Steel blue (text swap cycle only) |
| Footer on light | #666 | — |
| Footer on dark | #AAA | — |
| Footer on gold | #3A2800 | Dark brown |

## Typography

- **Headlines**: `Bebas Neue` — ALL CAPS, -0.02em tracking, 85–120px
- **Body**: `DM Sans` italic, 300–400 weight, 18–20px
- **Section labels**: `DM Sans` 700, ALL CAPS, 0.15em letter-spacing, 18–20px
- **Code/terminal**: `JetBrains Mono` 400, 20–24px
- **Footer/handle**: `DM Sans` 600, 14px

## Layout Grid (720×900)

- Side padding: 50px
- **Top padding: 100px minimum** — Instagram UI crops top ~60–80px of carousel videos
- Bottom padding: 50px
- **Usable content height: 750px**
- Content width: 620px
- Section label → headline gap: 16px
- Headline → body gap: 24px
- Body → visual gap: 32px

## Headline Sizing

| Length | Max size |
|--------|----------|
| ≤15 chars | 120px |
| 16–25 chars | 100px |
| 26–35 chars | 85px |
| 36+ chars | 72px (or split into two shorter lines) |

## Height Budget (sum must be ≤750px)

| Element | Height |
|---------|--------|
| Section label | 30px |
| Gap (label→headline) | 16px |
| Headline line @100px | 92px |
| Headline line @85px | 78px |
| Headline line @72px | 64px |
| Body line @20px | 30px |
| Gap (headline→body) | 24px |
| Gap (body→visual) | 32px |
| Feature card (compact) | 90px |
| Terminal card | 180px |
| Comparison cards row | 200px |
| Data callout | 120px |
| Footer | 40px |

## Background Rotation

| Slide | Background |
|-------|------------|
| 1 | Light (cream #F5EDE3) |
| 2 | Dark (navy #1A2744) |
| 3 | Light |
| 4 | Dark |
| 5 | Gold gradient |
| 6 | Light |
| 7 | Dark |
| 8 | Gold gradient |

## Footer (every slide)

- Left: `@practicerxconsulting` — DM Sans 600, 14px, ALL CAPS, 0.1em spacing
- Center: 3px progress bar, gold fill = (N/8 × 100%)
- Right: `N/8` — DM Sans 600, 18px
- Color: #666 on light · #AAA on dark · #3A2800 on gold

## What NOT To Do

- No gradients on dark (navy) slides — flat #1A2744 only
- No drop shadows on text
- No serif fonts (brand serif is for the website, not carousels)
- No centered text except slide 8 (CTA)
- No more than one accent color per slide
- No lime/chartreuse — that was the previous generic palette
