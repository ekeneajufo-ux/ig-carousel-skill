# Animated Instagram Carousel Builder

## What This Does

Builds an 8-slide animated Instagram carousel using HyperFrames. Each slide is a separate HyperFrames composition rendered as MP4. Output includes a phone-mockup previewer for reviewing the full carousel before posting.

## Prerequisites

- HyperFrames CLI installed: `npm install -g hyperframes`
- The `/hyperframes` skill must be invoked before writing any composition HTML

## How To Use

Paste this entire prompt into a new Claude Code session in any project directory. Replace the `[VARIABLES]` section with your content. Claude will build all 8 slides, render them, and generate a previewer.

---

## PROMPT — Copy everything below this line

---

Build me an 8-slide animated Instagram carousel using HyperFrames. Follow the design system, slide specs, and build process exactly.

### [VARIABLES] — Replace these

```
HANDLE: @doctablademd
DISPLAY_NAME: Emeka Ajufo, M.D.
AVATAR_PATH: [absolute path to avatar image, ideally 200px+ square]
TOP_RIGHT_LABEL: [product/tool name, e.g. "Viktor AI" or "DoctorLeadFlow"]
KEYWORD: [CTA keyword for comments, e.g. "VIKTOR"]
TOTAL_SLIDES: 8
```

**Slide content (fill in all 8):**

```
SLIDE 1 (HOOK — animated MP4, 10s):
  Type: light background, animated text swap
  Headline: [4-5 word lines filling 40% of slide]
  Swap words: [3 words/phrases that cycle in a colored pill]
  Body: [1-2 sentences, italic]
  CTA: "SWIPE TO LEARN HOW" or similar

SLIDE 2 (PAIN — animated MP4, 10s):
  Type: dark background
  Section label: [e.g. "THE BOTTLENECK"]
  Headline: [pain statement, accent color on key phrase]
  Visual: [what animated element — timeline, dashboard, chat, etc.]

SLIDE 3 (SOLUTION — static-feel MP4, 5s):
  Type: light background
  Section label: [e.g. "THE FIX"]
  Headline: [solution statement]
  Body: [supporting detail]
  Visual: [terminal mockup, Slack mockup, screenshot mockup, etc.]

SLIDE 4 (HOW — static-feel MP4, 5s):
  Type: dark background
  Section label: [e.g. "HOW IT WORKS"]
  Headline: [mechanism statement]
  Visual: [2x2 grid of feature cards with icons, step labels, descriptions]
  Body: [one-liner below cards]

SLIDE 5 (WHY — static-feel MP4, 5s):
  Type: lime gradient background
  Section label: [e.g. "WHY IT WINS"]
  Headline: [paradigm shift statement — big, bold, few words]
  Body: [supporting detail]
  Visual: [code snippet, data card, or proof element]
  Numbered list: [3 benefit statements]

SLIDE 6 (SCALE — animated MP4, 10s):
  Type: light background
  Section label: [e.g. "THE TOOLKIT" or "THE PROOF"]
  Headline: [scale/scope statement with a number]
  Body: [supporting detail]
  Secondary: [additional proof point]

SLIDE 7 (CONTRAST — static-feel MP4, 5s):
  Type: dark background
  Section label: [e.g. "THE CHEAT CODE"]
  Headline: [before/after or cost contrast, accent color on key number]
  Body: [one-liner]
  Visual: [before/after comparison cards — red vs olive]
  Closing: [two-line bold statement, second line in accent color]

SLIDE 8 (CTA — animated MP4, 10s):
  Type: lime gradient background, CENTER-ALIGNED
  Headline: [personal CTA question]
  Body: [what they get when they comment/DM]
  Button: COMMENT "[KEYWORD]"
```

### DESIGN SYSTEM

Colors:
| Role | Hex |
|------|-----|
| Light background | #F5F3EE |
| Dark background | #111111 |
| Text on light | #111111 |
| Text on dark | #FFFFFF |
| Accent | #C5E100 |
| Accent dark / olive | #4A5500 |
| Section label on light | #6B7300 |
| Danger / "before" | #8B2020 |
| Purple (swap only) | #A855F7 |
| Terminal bg | #1A1A1A |

Typography:
- **Headlines**: `Bebas Neue` — ALL CAPS, -0.02em tracking, 85-120px depending on word count
- **Body**: `DM Sans` italic, 300-400 weight, 18-20px
- **Section labels**: `DM Sans` 700, ALL CAPS, letter-spacing 0.15em, 18-20px
- **Terminal/code**: `JetBrains Mono` 400, 20-24px
- **Footer**: `DM Sans` 600, 14-18px

Layout (720x900):
- Padding: 50px sides, 60px top, 50px bottom
- Content width: 620px
- Gaps: label→headline 16px, headline→body 24px, body→visual 32px

Footer (EVERY slide):
- Left: @HANDLE (DM Sans 600, 14px, ALL CAPS, letter-spacing 0.1em)
- Center: progress bar (3px, accent fill width = slideNum/totalSlides * 100%)
- Right: N/totalSlides (DM Sans 600, 18px)
- Text color: #666 on light, #888 on dark, #333 on lime

What NOT to do:
- No gradients on dark slides (flat black only)
- No drop shadows on text
- No serif fonts
- No centered text except slide 8

### NARRATIVE ARC

The 8 slides follow Problem-Agitation-Solution-CTA:

| Slide | Role | Background |
|-------|------|------------|
| 1 | Hook — bold claim + text swap animation | Light |
| 2 | Pain — what's broken | Dark |
| 3 | Solution — what fixes it | Light |
| 4 | How — the mechanism/features | Dark |
| 5 | Why — the paradigm shift | Lime gradient |
| 6 | Scale — proof/scope | Light |
| 7 | Contrast — before/after + closing punch | Dark |
| 8 | CTA — comment keyword | Lime gradient |

Backgrounds MUST alternate light/dark/light/dark/lime/light/dark/lime.

### COPYWRITING RULES

- Headlines are ALL CAPS sentence fragments, never complete sentences
- Every headline uses contrast (big vs small, old vs new, many vs one)
- One phrase per slide gets the accent color treatment
- Body copy is always italic, max 2-3 lines
- Section labels are always present: THE [NOUN] format
- Periods between short phrases = emphasis: "VIDEO. IS. CODE."

### ANIMATION PATTERNS

**Slide 1 (Hook):**
- Avatar + name lockup top-left, product label top-right
- Headline slides from left (expo.out)
- Swap pill scales in (back.out), text cycles every 1.7s with color change
- Decorative stars rotate continuously
- Body + CTA pill fade up

**Slides 2, 6 (Animated, 10s):**
- Section label fades in first (0.15s)
- Headline slides from left
- Visual element has continuous animation (playhead scrub, counter, pulse)

**Slides 3, 4, 5, 7 (Static-feel, 5s):**
- Section label → headline → body → visual element (staggered entrances)
- Visual elements: terminal mockups, card grids, code snippets, comparison cards
- No continuous animation needed — entrance choreography is the engagement

**Slide 8 (CTA):**
- Center-aligned, everything fades/scales in
- CTA button has continuous scale pulse (1→1.03→1, yoyo, 2s cycle)

### VISUAL ELEMENTS TOOLKIT

Pick from these for each slide's visual:

- **Terminal mockup**: Dark card, traffic-light dots, monospace text, lime accents
- **Slack mockup**: Dark card, channel name, message bubbles, timestamps
- **2x2 feature grid**: Olive cards with emoji + step label + description
- **Before/after comparison**: Red-tinted card (before) vs olive card (after), arrow lists
- **Code snippet**: Dark card with syntax-highlighted code
- **Numbered list**: Large Bebas numbers + DM Sans descriptions, thin left border
- **NLE timeline**: Fake video editor timeline with colored tracks + playhead
- **Data callout**: Large stat number + supporting text
- **Chat/message mockup**: Message bubbles showing AI conversation

### BUILD PROCESS

1. **Init project**: `mkdir carousel-project && cd carousel-project && hyperframes init --width 720 --height 900 --fps 30`

2. **Copy avatar** to `assets/avatar.png`

3. **Build each slide** as its own HyperFrames project:
   ```
   mkdir slide-N && cd slide-N && hyperframes init --width 720 --height 900 --fps 30
   ```

4. **For each slide's index.html:**
   - Invoke `/hyperframes` skill before writing
   - Set viewport to `width=720, height=900`
   - Set html/body to 720x900
   - Root div: `data-composition-id="main"`, `data-width="720"`, `data-height="900"`
   - Every visible element: `class="clip"` + `data-start` + `data-duration` + `data-track-index`
   - Timeline: `gsap.timeline({ paused: true })` registered on `window.__timelines["main"]`
   - Import fonts via `@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:ital,wght@0,300;0,400;0,500;0,600;0,700;1,300;1,400&family=JetBrains+Mono:wght@400&display=swap')`

5. **Lint**: `npx hyperframes lint` — fix all errors

6. **Render**: `npx hyperframes render --format mp4 -o ../output/slide-N.mp4`

7. **Build slides in parallel** using 4 agents:
   - Agent 1: Slides 2-3
   - Agent 2: Slides 4-5
   - Agent 3: Slides 6-7
   - Agent 4: Slide 8
   - Build slide 1 yourself (it's the hero, needs direct oversight)

8. **Generate previewer** at `output/preview.html` using the phone mockup template below

### HYPERFRAMES RULES (NON-NEGOTIABLE)

- No `repeat: -1` — calculate exact repeats from duration
- No exit animations except final slide — entrance only
- Offset first animation 0.1-0.3s (not t=0)
- Use at least 3 different eases per slide
- No `Math.random()`, `Date.now()`, or async timeline construction
- `gsap.from()` for entrances, `gsap.to()` only for continuous ambient motion
- Don't animate `visibility` or `display` — only visual properties

### PREVIEWER TEMPLATE

Save this as `output/preview.html`. Copy avatar to `output/avatar.png`. All slide MP4s go in `output/`.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Carousel Preview</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body { background: #1a1a1a; display: flex; align-items: center; justify-content: center; min-height: 100vh; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif; color: #fff; overflow: hidden; }
    .phone-frame { width: 390px; height: 844px; background: #000; border-radius: 48px; border: 4px solid #333; overflow: hidden; position: relative; box-shadow: 0 40px 80px rgba(0,0,0,0.6); }
    .status-bar { height: 54px; background: #000; display: flex; align-items: flex-end; justify-content: space-between; padding: 0 28px 8px; font-size: 14px; font-weight: 600; z-index: 10; position: relative; }
    .ig-header { height: 44px; background: #000; display: flex; align-items: center; padding: 0 14px; gap: 10px; z-index: 10; position: relative; }
    .ig-avatar { width: 32px; height: 32px; border-radius: 50%; background: linear-gradient(135deg, #C5E100, #6B7300); padding: 2px; }
    .ig-avatar-inner { width: 100%; height: 100%; border-radius: 50%; overflow: hidden; }
    .ig-avatar-inner img { width: 100%; height: 100%; object-fit: cover; }
    .ig-username { font-size: 13px; font-weight: 600; }
    .ig-dots { margin-left: auto; font-size: 18px; letter-spacing: 2px; }
    .carousel-viewport { width: 390px; height: 487px; position: relative; overflow: hidden; background: #000; }
    .carousel-track { display: flex; height: 100%; transition: transform 0.35s cubic-bezier(0.25, 0.1, 0.25, 1); }
    .carousel-slide { width: 390px; height: 487px; flex-shrink: 0; }
    .carousel-slide video { width: 100%; height: 100%; object-fit: cover; }
    .nav-arrow { position: absolute; top: 50%; transform: translateY(-50%); width: 28px; height: 28px; border-radius: 50%; background: rgba(0,0,0,0.35); border: none; color: #fff; font-size: 14px; cursor: pointer; z-index: 5; display: flex; align-items: center; justify-content: center; backdrop-filter: blur(8px); }
    .nav-arrow.left { left: 8px; }
    .nav-arrow.right { right: 8px; }
    .nav-arrow.hidden { opacity: 0; pointer-events: none; }
    .ig-carousel-dots { display: flex; justify-content: center; gap: 4px; padding: 10px 0 6px; background: #000; }
    .dot { width: 6px; height: 6px; border-radius: 50%; background: #555; transition: background 0.25s, transform 0.25s; }
    .dot.active { background: #3897f0; transform: scale(1.3); }
    .ig-actions { display: flex; align-items: center; padding: 10px 14px; gap: 16px; background: #000; }
    .ig-action-icon { font-size: 22px; cursor: pointer; opacity: 0.9; }
    .ig-bookmark { margin-left: auto; }
    .ig-engagement { padding: 4px 14px 14px; background: #000; font-size: 13px; line-height: 1.5; }
    .ig-likes { font-weight: 600; margin-bottom: 4px; }
    .ig-caption span { font-weight: 600; }
    .ig-caption { color: #ccc; }
    .ig-more { color: #777; cursor: pointer; }
    .ig-bottom-nav { position: absolute; bottom: 0; left: 0; right: 0; height: 50px; background: #000; border-top: 0.5px solid #222; display: flex; align-items: center; justify-content: space-around; font-size: 22px; }
    .slide-counter { position: fixed; top: 24px; right: 24px; color: #555; font-size: 14px; font-weight: 600; }
    .hint { position: fixed; bottom: 24px; left: 50%; transform: translateX(-50%); color: #666; font-size: 13px; }
    .hint kbd { background: #333; padding: 2px 8px; border-radius: 4px; color: #aaa; }
  </style>
</head>
<body>
<div class="phone-frame">
  <div class="status-bar"><span>9:41</span><span>&#9679;&#9679;&#9679;&#9679; &#128267;</span></div>
  <div class="ig-header">
    <div class="ig-avatar"><div class="ig-avatar-inner"><img src="avatar.png" alt="" /></div></div>
    <span class="ig-username">[HANDLE without @]</span>
    <span class="ig-dots" style="margin-left:auto">&middot;&middot;&middot;</span>
  </div>
  <div class="carousel-viewport" id="viewport">
    <button class="nav-arrow left hidden" id="navLeft" onclick="go(-1)">&#8249;</button>
    <button class="nav-arrow right" id="navRight" onclick="go(1)">&#8250;</button>
    <div class="carousel-track" id="track"></div>
  </div>
  <div class="ig-carousel-dots" id="dots"></div>
  <div class="ig-actions">
    <span class="ig-action-icon">&#9825;</span>
    <span class="ig-action-icon">&#128172;</span>
    <span class="ig-action-icon">&#9993;</span>
    <span class="ig-action-icon ig-bookmark">&#9734;</span>
  </div>
  <div class="ig-engagement">
    <div class="ig-likes">2,847 likes</div>
    <div class="ig-caption"><span>[HANDLE without @]</span> [First line of caption] <span class="ig-more">...more</span></div>
  </div>
  <div class="ig-bottom-nav"><span>&#8962;</span><span>&#128269;</span><span>&#10010;</span><span>&#9654;</span><span>&#128100;</span></div>
</div>
<div class="slide-counter" id="counter">1 / 8</div>
<div class="hint"><kbd>&larr;</kbd> <kbd>&rarr;</kbd> to navigate</div>
<script>
  const slides = [
    { src: 'slide-1.mp4', duration: 10 },
    { src: 'slide-2.mp4', duration: 10 },
    { src: 'slide-3.mp4', duration: 5 },
    { src: 'slide-4.mp4', duration: 5 },
    { src: 'slide-5.mp4', duration: 5 },
    { src: 'slide-6.mp4', duration: 10 },
    { src: 'slide-7.mp4', duration: 5 },
    { src: 'slide-8.mp4', duration: 10 },
  ];
  const track = document.getElementById('track'), dotsC = document.getElementById('dots');
  const navL = document.getElementById('navLeft'), navR = document.getElementById('navRight');
  const counter = document.getElementById('counter');
  let cur = 0; const vids = [];
  slides.forEach((s, i) => {
    const d = document.createElement('div'); d.className = 'carousel-slide';
    const v = document.createElement('video');
    v.src = s.src; v.muted = true; v.playsInline = true; v.loop = true; v.preload = 'auto';
    d.appendChild(v); track.appendChild(d); vids.push(v);
    const dot = document.createElement('div');
    dot.className = 'dot' + (i === 0 ? ' active' : '');
    dot.onclick = () => goTo(i); dotsC.appendChild(dot);
  });
  vids[0].play();
  function goTo(i) {
    if (i < 0 || i >= slides.length) return;
    vids[cur].pause(); cur = i;
    track.style.transform = `translateX(-${cur * 390}px)`;
    document.querySelectorAll('.dot').forEach((d, j) => d.classList.toggle('active', j === cur));
    navL.classList.toggle('hidden', cur === 0);
    navR.classList.toggle('hidden', cur === slides.length - 1);
    counter.textContent = `${cur + 1} / ${slides.length}`;
    vids[cur].currentTime = 0; vids[cur].play();
  }
  function go(dir) { goTo(cur + dir); }
  document.addEventListener('keydown', e => { if (e.key === 'ArrowLeft') go(-1); if (e.key === 'ArrowRight') go(1); });
  let tx = 0; const vp = document.getElementById('viewport');
  vp.addEventListener('touchstart', e => { tx = e.touches[0].clientX; });
  vp.addEventListener('touchend', e => { const d = tx - e.changedTouches[0].clientX; if (Math.abs(d) > 40) go(d > 0 ? 1 : -1); });
</script>
</body>
</html>
```

### REFERENCE SLIDE (Slide 1 — full working example)

Use this as the structural template. Every other slide follows the same HTML skeleton (viewport meta, body dimensions, clip class, data attributes, font imports, timeline registration) with different content and styles.

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=720, height=900" />
    <script src="https://cdn.jsdelivr.net/npm/gsap@3.14.2/dist/gsap.min.js"></script>
    <style>
      @import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:ital,wght@0,300;0,400;0,500;0,600;0,700;1,300;1,400&family=JetBrains+Mono:wght@400&display=swap');
      * { margin: 0; padding: 0; box-sizing: border-box; }
      html, body { margin: 0; width: 720px; height: 900px; overflow: hidden; background: #F5F3EE; }

      .scene-content {
        display: flex; flex-direction: column; width: 100%; height: 100%;
        padding: 50px 50px 45px 50px; position: relative; overflow: hidden;
      }

      /* Section label */
      .section-label {
        font-family: 'DM Sans', sans-serif; font-weight: 700; font-size: 18px;
        letter-spacing: 0.15em; text-transform: uppercase;
        color: #6B7300; /* use #C5E100 on dark backgrounds */
      }

      /* Headline */
      .headline {
        font-family: 'Bebas Neue', sans-serif; font-weight: 400;
        font-size: 100px; line-height: 0.92; letter-spacing: -0.02em;
        color: #111111; /* use #FFFFFF on dark backgrounds */
        text-transform: uppercase; margin-top: 16px;
      }

      /* Body */
      .body-copy {
        font-family: 'DM Sans', sans-serif; font-weight: 400; font-style: italic;
        font-size: 20px; line-height: 1.5; color: #444; margin-top: 24px;
      }

      /* Footer — include on EVERY slide */
      .footer {
        display: flex; align-items: center; width: 100%;
        margin-top: auto; padding-top: 12px;
      }
      .footer-handle {
        font-family: 'DM Sans', sans-serif; font-weight: 600; font-size: 14px;
        letter-spacing: 0.1em; text-transform: uppercase; color: #666;
      }
      .footer-progress { display: flex; align-items: center; gap: 12px; flex: 1; margin-left: 16px; }
      .progress-bar { flex: 1; height: 3px; background: #D0CEC9; border-radius: 2px; overflow: hidden; position: relative; }
      .progress-fill { position: absolute; left: 0; top: 0; height: 100%; width: 12.5%; background: #C5E100; border-radius: 2px; }
      .page-num { font-family: 'DM Sans', sans-serif; font-weight: 600; font-size: 18px; color: #666; }
    </style>
  </head>
  <body>
    <div id="root" data-composition-id="main" data-start="0" data-duration="5" data-width="720" data-height="900">
      <div id="slide" class="clip" data-start="0" data-duration="5" data-track-index="1">
        <div class="scene-content">
          <div class="section-label" id="label">THE FIX</div>
          <div class="headline" id="headline">YOUR HEADLINE HERE.</div>
          <div class="body-copy" id="body">Your supporting copy here.</div>
          <!-- visual element goes here -->
          <div class="footer" id="footer">
            <span class="footer-handle">@DOCTABLADEMD</span>
            <div class="footer-progress">
              <div class="progress-bar"><div class="progress-fill" style="width: 37.5%"></div></div>
              <span class="page-num">3/8</span>
            </div>
          </div>
        </div>
      </div>
    </div>
    <script>
      window.__timelines = window.__timelines || {};
      const tl = gsap.timeline({ paused: true });
      tl.from("#label", { opacity: 0, y: -15, duration: 0.4, ease: "power3.out" }, 0.15);
      tl.from("#headline", { opacity: 0, x: -40, duration: 0.6, ease: "expo.out" }, 0.3);
      tl.from("#body", { opacity: 0, y: 25, duration: 0.45, ease: "power2.out" }, 0.7);
      tl.from("#footer", { opacity: 0, duration: 0.4, ease: "sine.out" }, 1.0);
      window.__timelines["main"] = tl;
    </script>
  </body>
</html>
```
