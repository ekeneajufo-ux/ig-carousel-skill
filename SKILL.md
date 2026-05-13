# Animated Instagram Carousel — PracticeRx

Build an 8-slide animated Instagram carousel using HyperFrames. Derives all content from context automatically — no variables to fill in.

---

## STEP 0 — Extract context from the conversation

Read the conversation to identify:
- **TOPIC** — what this carousel is about
- **HANDLE** — Instagram handle (default: `@practicerxconsulting`)
- **DISPLAY_NAME** — brand name (default: `Dr. Ekene Ajufo, MD · PracticeRx`)
- **KEYWORD** — CTA comment trigger (derive from topic, e.g. `VACCINES`, `DPC`, `GUIDE`)
- **KEY_POINTS** — 5–7 core claims from any pasted content to distribute across slides

If the topic cannot be inferred at all, ask one question. Otherwise proceed immediately.

---

## DESIGN SYSTEM

**Colors — PracticeRx brand:**
| Role | Hex |
|------|-----|
| Light background | #F5EDE3 |
| Dark background | #1A2744 |
| Text on light | #1A2744 |
| Text on dark | #FFFFFF |
| Accent / gold | #C09843 |
| Accent dark / bronze | #7A6030 |
| Section label on light | #7A6030 |
| Section label on dark | #C09843 |
| Gold gradient | `linear-gradient(145deg, #C09843 0%, #8B6914 100%)` |
| Danger / "before" | #8B2020 |
| Terminal bg | #0F1A30 |
| Swap alt | #5B8AB0 |
| Footer text on light | #666 |
| Footer text on dark | #AAA |
| Footer text on gold | #3A2800 |

**Typography:**
- Headlines: `Bebas Neue` ALL CAPS, -0.02em tracking, 85–120px
- Body: `DM Sans` italic, 300–400 weight, 18–20px
- Labels: `DM Sans` 700, ALL CAPS, 0.15em letter-spacing, 18–20px
- Code/terminal: `JetBrains Mono` 400, 20–24px
- Font `@import`: `https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:ital,wght@0,300;0,400;0,500;0,600;0,700;1,300;1,400&family=JetBrains+Mono:wght@400&display=swap`

**Layout — 720×900:**
- Padding: **100px top** (Instagram crops top 60–80px), 50px sides, 50px bottom
- Usable height: **750px**. Sum element heights before writing every slide.
- Footer on every slide: left `@handle` · center 3px progress bar (gold fill) · right `N/8`

**Headline sizing by character count:** ≤15→120px · 16–25→100px · 26–35→85px · 36+→72px

**Height budget per element:**
label 30 · gap(label→hl) 16 · hl-line@100px 92 · hl-line@85px 78 · hl-line@72px 64 · body-line 30 · gap(hl→body) 24 · gap(body→visual) 32 · feature-card 90 · terminal 180 · comparison-cards 200 · footer 40

---

## NARRATIVE ARC

| # | Role | Background | Duration |
|---|------|------------|----------|
| 1 | Hook — bold claim + text swap animation | Light (cream) | 10s |
| 2 | Pain — what's broken | Dark (navy) | 10s |
| 3 | Solution — what fixes it | Light | 5s |
| 4 | How it works — mechanism | Dark | 5s |
| 5 | Why it matters — paradigm shift | Gold gradient | 5s |
| 6 | Scale / proof — numbers | Light | 10s |
| 7 | Before / after contrast | Dark | 5s |
| 8 | CTA — comment keyword | Gold gradient | 10s |

---

## HYPERFRAMES RULES (non-negotiable)

- Canvas 720×900 · `data-composition-id="main"` · all elements `class="clip"` + `data-start` + `data-duration` + `data-track-index`
- `gsap.timeline({ paused: true })` registered as `window.__timelines["main"]`
- GSAP: `<script src="https://cdn.jsdelivr.net/npm/gsap@3.14.2/dist/gsap.min.js"></script>`
- No `repeat: -1` — calculate exact repeat count from slide duration
- Entrance only (`gsap.from()`). Ambient motion only via `gsap.to()`. No exit tweens.
- First tween at 0.1–0.3s. Use ≥3 different eases per slide.
- Ambient tweens must start **≥0.05s after the entrance on the same element ends**. Add `overwrite: "auto"` to every ambient tween.
- Never animate `visibility` or `display`. No `Math.random()`, `Date.now()`, async timelines.

---

## BUILD PROCESS

**1 — Setup** (run once, creates project dir and 8 slide dirs):
```bash
PROJECT="carousel-$(date +%s)" && mkdir "$PROJECT" && cd "$PROJECT"
npx hyperframes@0.5.7 init --width 720 --height 900 --fps 30
for N in 1 2 3 4 5 6 7 8; do
  mkdir "slide-$N" && cp 720/hyperframes.json "slide-$N/"
  printf '{"name":"slide-%s","private":true,"type":"module","scripts":{"render":"npx hyperframes@0.5.7 render","check":"npx hyperframes@0.5.7 lint"}}' $N > "slide-$N/package.json"
  printf '{"id":"slide-%s","name":"slide-%s"}' $N $N > "slide-$N/meta.json"
done && mkdir output
```

**2 — FFmpeg** (Windows, run once per session):
```bash
export FFMPEG_PATH="$(npm root -g)/ffmpeg-static/ffmpeg.exe"
export PATH="$PATH:$(dirname $FFMPEG_PATH)"
```

**3 — Write slides in pairs:** Write slide N and N+1, then immediately lint both before moving on.
```bash
cd slide-N && npx hyperframes@0.5.7 lint 2>&1 && cd ..
```
Fix **all errors**. Fix all `overlapping_gsap_tweens` warnings (ambient start = entrance_end + 0.05s min). Do not advance to the next pair until both slides are clean.

Pairs: 1+2 → lint → fix · 3+4 → lint → fix · 5+6 → lint → fix · 7+8 → lint → fix

**4 — Render:**
```bash
for N in 1 2 3 4 5 6 7 8; do
  cd "slide-$N" && npx hyperframes@0.5.7 render --format mp4 -o "../output/slide-$N.mp4" 2>&1 | tail -2 && cd ..
done
ls -lh output/*.mp4
```
All 8 files must exist and be >50KB. Re-lint and re-render any that are missing or small.

**5 — Previewer:** Write `output/preview.html` — standard Instagram phone mockup (390×844 black rounded frame, status bar, IG header with gold Rx avatar circle + handle, 487px carousel viewport with left/right nav arrows, dot indicators, IG actions row, caption row with first line of copy, bottom nav). Videos autoplay and loop; slide change pauses current and plays next from t=0. Arrow keys and touch swipe navigate.

**6 — Caption:** After renders succeed, print the caption and hashtags **directly in your response** in a single fenced code block. Do not write to a file.

Format:
```
[Hook — bold restatement of the core claim as a question or declaration]

[1–2 sentences of context for the target audience]

✦ [key insight 1]
✦ [key insight 2]
✦ [key insight 3]
✦ [key insight 4]
✦ [key insight 5]

Comment [KEYWORD] below and I'll send you [what they get] 👇

— — —

#[niche-1] #[niche-2] #[midtier-1] #[midtier-2] #[broad-1]
```
5 hashtags only: 2 niche (<50K posts) · 2 mid-tier (50K–500K) · 1 broad.

**7 — Preview server:**
```bash
cd output && npx serve . --listen 4242 &
```
Then open `http://localhost:4242/preview.html`. Navigate all 8 slides. Confirm no cropping, no cut-off text, all videos play.

---

## ANIMATION PATTERNS

**Slide 1 (Hook, 10s):** Brand lockup (gold Rx circle + name) top-left, topic pill top-right. Headline slides from left (expo.out). Swap pill scales in (back.out), text cycles every 1.7s with color toggle between gold and #5B8AB0. Decorative ✦ stars rotate continuously (start ≥0.05s after entrance, overwrite:auto). Body + CTA pill fade up.

**Slides 2, 6 (Animated, 10s):** Label fades in → headline slides from left → visual with continuous motion (counter, pulse, scrub). Footer fades in with label.

**Slides 3, 4, 5, 7 (Static-feel, 5s):** Label → headline → body → visual, staggered 0.15–0.2s apart. Entrance choreography is the engagement — no continuous motion needed.

**Slide 8 (CTA, 10s, center-aligned):** Everything center-aligned. Brand lockup → headline → body → accent line → CTA button. Button pulses continuously after entrance (scale 1→1.04→1, yoyo, overwrite:auto).

---

## VISUAL ELEMENTS

- **Terminal mockup:** `#0F1A30` card, traffic-light dots, JetBrains Mono, gold (`#C09843`) for values/accents
- **2×2 feature grid:** `rgba(192,152,67,0.15)` cards with `1px solid #7A6030` border, emoji + label + desc
- **Before/after:** `rgba(139,32,32,0.2)` + `#8B2020` border (before) · `rgba(192,152,67,0.2)` + `#7A6030` border (after)
- **Numbered list:** Bebas Neue 64px gold numbers, 3px gold left border, DM Sans italic desc
- **Data callout:** Bebas Neue 80px gold stat + DM Sans supporting label, on `#FFFAF4` card

---

## COPYWRITING RULES

- Headlines: ALL CAPS fragments, never full sentences. Use contrast (many vs one, before vs after, big vs small).
- One phrase per slide in accent gold. Body italic max 2–3 lines. Labels = `THE [NOUN]` format.
- Emphasis via periods: `ONE DECISION. $10K BACK.`
- All text left-aligned except slide 8 (center).

---

## KNOWN FIXES

| Problem | Fix |
|---------|-----|
| Instagram crops top 60–80px | Always 100px top padding minimum |
| `hyperframes init` creates `720/` subfolder | Copy configs manually into each `slide-N/` |
| FFmpeg not found | Set `FFMPEG_PATH` to ffmpeg-static `.exe` path |
| `overlapping_gsap_tweens` warning | Ambient start = entrance end + 0.05s; add `overwrite:"auto"` |
| `preview.html` blank on open | Must serve via `npx serve` — never open as `file://` |
| Slide content overflows 750px | Reduce headline font size or cut one visual element |
