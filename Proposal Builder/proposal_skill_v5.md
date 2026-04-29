---
name: proposal
description: Build polished, single-file HTML client proposals and strategy documents for pointdot. Use this skill whenever the user asks to create a client proposal, pitch document, audit, gap analysis, strategy deck, or marketing engagement document for a prospective or existing client. Also trigger when the user says "proposal", "pitch", "strategy doc", "gap analysis", "audit document", or references building a document to send to a client. Always read this skill before writing any proposal code. For extended visual components (funnel charts, heatmaps, bento grids, gauge meters, sparklines), also consult the design-bible skill.
---

# Pointdot Client Proposal — Skill Reference (v5 — Apple-Inspired)

This document defines the **design system**, **section architecture**, **component library**, **interaction layer**, and **writing guidelines** for building pointdot client proposals as single-file HTML documents. Read this entire file before writing any code.

> **Design philosophy:** Inspired by Apple.com. White space does the heavy lifting. Typography creates hierarchy, not decoration. Cards have no visible borders. Sections alternate full-width backgrounds. Every element earns its place. If a section can be communicated visually, use a visual component instead of prose.

---

## 1. Design System

### 1.1 Colour Palette

```css
:root {
  --gold:       #A8851F;              /* primary accent — used sparingly */
  --gold-dark:  #8B6E19;
  --gold-light: #C9A84C;
  --gold-wash:  #F7F2E6;              /* light gold tint for icon backgrounds, badges */

  --text-primary:   #1d1d1f;          /* headlines, bold text */
  --text-secondary: #86868b;          /* body copy, descriptions */
  --text-tertiary:  #aeaeb2;          /* captions, labels on dark bg */

  --bg:         #ffffff;              /* page background — white, not beige */
  --bg-alt:     #f5f5f7;              /* alternating section background */
  --bg-dark:    #1d1d1f;              /* dark sections (bottom line only) */
  --surface:    #ffffff;              /* card backgrounds on alt bands */

  --border-subtle: rgba(0,0,0,0.04);  /* table row dividers, invest rows */

  --red:        #ff3b30;              /* negative values, bad comparison tags */
  --red-soft:   #C4342A;              /* softer red for text labels */

  --font: 'Aeonik Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
}
```

**Two-colour data system:** Gold for positive/winning data. Red for negative/losing data. No green. All positive indicators use `--gold` or `--gold-light`.

**Key difference from v4:** No warm beige (`--page`), no `--grey-*` scale, no `--charcoal`. The palette is black/white/grey with gold as the single accent. Body text uses Apple's `#86868b` grey.

### 1.2 Typography

- **Font family:** `var(--font)` — Aeonik Pro with system fallbacks. Weights 400, 500, 600 via `@font-face` with `font-display: swap`.
- **Base size:** `16px` on `<html>`.
- **Line height:** `1.5` on `<body>`.
- **Smoothing:** `-webkit-font-smoothing: antialiased` on `<body>`.

#### Type Scale

| Element | Size | Weight | Tracking | Alignment | Notes |
|---|---|---|---|---|---|
| Cover h1 | 64px | 600 | -0.04em | Centre | Gradient text (white/gold/white) |
| Cover eyebrow | 13px | 500 | 0.02em | Centre | `rgba(255,255,255,0.7)` |
| Cover subtitle | 17px | 400 | — | Centre | `rgba(255,255,255,0.7)`, max-width 480px |
| Section label | 13px | 500 | 0.02em | Centre | `--gold` colour |
| Section h2 | 48px | 600 | -0.04em | Centre | `--text-primary` |
| Section intro | 17px | 400 | — | Centre | `--text-secondary`, max-width 580px |
| Callout text | 19px | 400 | — | Centre | `--text-secondary`, max-width 640px |
| Card title (fc/sc) | 17px | 600 | -0.01em | Left | `--text-primary` |
| Card description | 14px | 400 | — | Left | `--text-secondary`, line-height 1.6 |
| Counter value | 56px | 600 | -0.04em | Centre | Colour per metric |
| Counter label | 14px | 400 | — | Centre | `--text-secondary` |
| Table th | 12px | 500 | 0.02em | Left | `--text-tertiary` on `--bg-dark` |
| Table td | 14px | 400 | — | Left | `--text-secondary` |
| Flow title | 15px | 600 | — | Left | `--text-primary` |
| Flow desc | 14px | 400 | — | Left | `--text-secondary` |
| FAQ question | 17px | 600 | -0.01em | Left | `--text-primary` |
| FAQ answer | 15px | 400 | — | Left | `--text-secondary` |
| Bottom hero | 21px | 400 | — | Centre | `--text-tertiary` on dark |
| Total hero value | 56px | 600 | -0.04em | Centre | `--text-primary` |

### 1.3 Layout — Full-Width Band System

**Key change from v4:** Content is no longer inside a single `.page` container. Each section is a full-width `<div class="band">` with its own background colour. A centred `.inner` wrapper (860px max-width) holds the content.

```html
<div class="band">          <!-- white background -->
  <div class="inner reveal">
    <!-- section content -->
  </div>
</div>

<div class="band band-alt"> <!-- #f5f5f7 grey background -->
  <div class="inner reveal">
    <!-- section content -->
  </div>
</div>

<div class="band band-dark"> <!-- #1d1d1f dark background -->
  <div class="inner reveal">
    <!-- section content -->
  </div>
</div>
```

**Band rules:**
- `.band` — white background, 100px vertical padding, 32px horizontal padding
- `.band-alt` — `#f5f5f7` grey background
- `.band-dark` — `#1d1d1f` dark background, text flips to light
- Sections **always alternate** white → grey → white → grey through the document
- The only dark band is the bottom line / closing section
- **No divider lines.** Spacing and background alternation handle separation.

**Card rules:**
- **No visible borders on any card.** Cards use background differentiation only.
- On white bands: cards use `var(--bg-alt)` background
- On grey bands: cards use `var(--surface)` (white) background
- Border-radius: `20px` on all cards
- Padding: `32px 28px` standard
- Hover: `scale(1.02)` via magnetic effect (not `translateY`)

### 1.4 Global Reset

```css
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { font-size: 16px; scroll-behavior: smooth; }
body { font-family: var(--font); background: var(--bg); color: var(--text-primary); line-height: 1.5; -webkit-font-smoothing: antialiased; overflow-x: hidden; }
```

---

## 2. Section Architecture

Select sections based on the document's purpose. Not all are required. The order below is the default for a full proposal/audit document.

### 2.1 Cover

Full-viewport **gold gradient** with dot-grid texture and glassmorphism metadata card. Unchanged from v4.

```html
<div class="cover">
  <div class="cover-inner">
    <div class="logo"><div class="logo-arrow"></div><div class="logo-text">pointdot</div><div class="logo-dot"></div></div>
    <div class="cover-eyebrow">[Document Type]</div>
    <h1>[Client Name]</h1>
    <div class="cover-sub">[One-sentence subtitle]</div>
    <div class="cover-glass">
      <div class="cover-meta-item"><label>Prepared by</label><span>[Name]</span></div>
      <div class="cover-meta-item"><label>Date</label><span>[Month Year]</span></div>
      <!-- Add 2-4 meta items as needed -->
    </div>
  </div>
</div>
```

### 2.2 Counter Cards *(optional)*

3-column grid of large animated numbers. Use for headline metrics that tell the story at a glance. Counters animate from 0 on scroll into view via IntersectionObserver.

- Support `data-prefix` ($), `data-suffix` (%, +, k, M), `data-decimals`
- Colour each value individually via inline `style="color:var(--gold)"` or `style="color:var(--red)"`
- Follow with a `.callout-text` paragraph summarising the implication

```html
<div class="counter-grid">
  <div class="counter-card magnetic">
    <span class="cc-val" style="color:var(--gold)" data-count="[N]" data-prefix="$" data-decimals="2">[Init]</span>
    <span class="cc-label">[Description]</span>
  </div>
  <!-- Repeat 2-3 cards -->
</div>
<p class="callout-text">[Implication with <strong>key figures</strong> bolded]</p>
```

### 2.3 Comparison Bars *(optional)*

Stacked before/after bars proving a contrast. No card wrapper. Bars sit directly in the section. Gold gradient for positive, red gradient for negative.

```html
<div class="compare-stack">
  <div class="compare-block">
    <div class="compare-label">[What's being compared]</div>
    <div class="compare-row"><div class="compare-tag good">[Winner]</div><div class="bar-track"><div class="bar-fill green" style="width:[X]%"><span>[Value]</span></div></div></div>
    <div class="compare-row"><div class="compare-tag bad">[Loser]</div><div class="bar-track"><div class="bar-fill red" style="width:[Y]%"><span>[Value]</span></div></div></div>
  </div>
  <!-- Stack 2-3 compare blocks -->
</div>
```

Note: `.bar-fill.green` renders as gold gradient, not green. The class name is historical.

### 2.4 Feature Cards (3-column)

Icon + title + description cards for gaps, problems, or strategic pillars. Use premium SVG icons (see section 3).

```html
<div class="feature-grid">
  <div class="feature-card magnetic">
    <div class="pi"><svg><use href="#i-[icon]"/></svg></div>
    <div class="fc-title">[Title]</div>
    <div class="fc-desc">[2-3 sentences]</div>
  </div>
  <!-- Repeat 3 cards -->
</div>
```

Use `.feature-grid.four-col` for 4-column layouts (e.g. filming guides, checklists).

### 2.5 Data Table

Dark header row, hover-highlighted rows, pill badges for status.

```html
<div class="table-wrap magnetic">
  <table>
    <thead><tr><th>[Col]</th><th>[Col]</th></tr></thead>
    <tbody>
      <tr><td class="bold">[Value]</td><td class="gold-val">[Value]</td><td class="pill"><span class="video">[Label]</span></td></tr>
    </tbody>
  </table>
</div>
```

Pill modifiers: `.video` (gold wash bg, gold dark text). Add more as needed.

### 2.6 Solution Cards (2-column)

Premium icon + phase label + title + description. Use for deliverables, workstreams, or asset types.

```html
<div class="solution-grid">
  <div class="solution-card magnetic">
    <div class="pi"><svg><use href="#i-[icon]"/></svg></div>
    <div>
      <div class="sc-phase">[Phase / Category]</div>
      <div class="sc-title">[Deliverable]</div>
      <div class="sc-desc">[1-2 sentences]</div>
    </div>
  </div>
  <!-- Repeat cards -->
</div>
```

### 2.7 Investment Card + Total Hero *(optional)*

Clean investment breakdown with a large centred headline below.

```html
<div class="invest-card magnetic" style="max-width:560px;margin:0 auto 40px">
  <div class="invest-row"><span class="r-label">[Line item]</span><span class="r-val">[Value]</span></div>
  <div class="invest-row inv-total"><span class="r-label">Total</span><span class="r-val">[Amount]</span></div>
</div>
<div class="total-hero">
  <div class="th-value">[Big headline e.g. "6 ads. 8-10 week creative runway."]</div>
  <div class="th-sub">[ROI context, 2-3 sentences]</div>
</div>
```

### 2.8 Step Process Flow

Vertical steps with gold numbered circles and timeline badges. Circles vertically centred to their card (`align-items: center`).

```html
<div class="step-flow">
  <div class="flow-step">
    <div class="flow-num">[N]</div>
    <div class="flow-body magnetic">
      <div><div class="flow-title">[Title]</div><div class="flow-desc">[One sentence]</div></div>
      <div class="flow-badge">[Timeline]</div>
    </div>
  </div>
  <!-- Repeat steps -->
</div>
```

### 2.9 FAQ Accordion

Apple-style expand/collapse. One open at a time. Border-top on first item, border-bottom on all. Plus/minus toggle with CSS transitions. Question text turns gold on hover.

```html
<div class="faq-list">
  <div class="faq-item">
    <div class="faq-trigger">
      <div class="faq-q">[Question]</div>
      <div class="faq-toggle"></div>
    </div>
    <div class="faq-answer"><div class="faq-a">[Answer]</div></div>
  </div>
  <!-- Repeat items -->
</div>
```

### 2.10 Bottom Line (Dark Band)

The **only** dark section in the document. Centred text at 21px on `--bg-dark`. Use `<strong>` for emphasis (renders white on dark).

```html
<div class="band band-dark" style="padding:120px 32px">
  <div class="inner reveal">
    <div class="bottom-hero">
      <div class="section-label">The bottom line</div>
      <p>[Closing argument with <strong>key points</strong> bolded]</p>
      <p class="sub">[Supporting sentence, softer tone]</p>
    </div>
  </div>
</div>
```

### 2.11 Footer

Minimal. White background with 1px top border. Logo and one line.

```html
<footer>
  <div class="footer-logo"><div class="footer-logo-arrow"></div><div class="footer-logo-text">pointdot</div><div class="footer-logo-dot"></div></div>
  <p>Confidential · Prepared for [Client Name] · [Month Year]</p>
</footer>
```

---

## 3. Premium SVG Icon System

**No emojis.** All icons use a premium app-icon treatment: 48x48 rounded square with a three-stop gold gradient fill, containing a 22px white line-art SVG icon.

### 3.1 Icon Container CSS

```css
.pi {
  width: 48px; height: 48px; border-radius: 14px;
  background: linear-gradient(135deg, var(--gold-light) 0%, var(--gold) 50%, var(--gold-dark) 100%);
  display: flex; align-items: center; justify-content: center; flex-shrink: 0;
}
.pi svg { width: 22px; height: 22px; stroke: #fff; stroke-width: 2; stroke-linecap: round; stroke-linejoin: round; fill: none; }
```

### 3.2 SVG Sprite Sheet

Place a hidden SVG sprite block immediately after `<body>`. Define each icon as a `<symbol>` with a `viewBox="0 0 24 24"` and white stroke paths. Reference in HTML with `<svg><use href="#i-[name]"/></svg>`.

```html
<svg xmlns="http://www.w3.org/2000/svg" style="display:none;">
  <symbol id="i-rotate" viewBox="0 0 24 24"><path d="M23 4v6h-6"/><path d="M1 20v-6h6"/><path d="M20.49 9A9 9 0 0 0 5.64 5.64L1 10"/><path d="M3.51 15a9 9 0 0 0 14.85 4.36L23 14"/></symbol>
  <symbol id="i-funnel" viewBox="0 0 24 24"><path d="M22 3H2l8 9.5V19l4 2v-8.5z"/></symbol>
  <symbol id="i-video" viewBox="0 0 24 24"><rect x="2" y="4" width="15" height="16" rx="2"/><path d="M17 8l5-3v14l-5-3z"/></symbol>
  <symbol id="i-target" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><circle cx="12" cy="12" r="6"/><circle cx="12" cy="12" r="2"/></symbol>
  <symbol id="i-bolt" viewBox="0 0 24 24"><path d="M13 2L3 14h9l-1 8 10-12h-9z"/></symbol>
  <symbol id="i-users" viewBox="0 0 24 24"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></symbol>
  <symbol id="i-clipboard" viewBox="0 0 24 24"><path d="M16 4h2a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2V6a2 2 0 0 1 2-2h2"/><rect x="8" y="2" width="8" height="4" rx="1"/><path d="M12 11v4"/><path d="M10 13h4"/></symbol>
  <symbol id="i-star" viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01z"/></symbol>
  <symbol id="i-pin" viewBox="0 0 24 24"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 1 1 18 0z"/><circle cx="12" cy="10" r="3"/></symbol>
  <symbol id="i-phone" viewBox="0 0 24 24"><rect x="7" y="2" width="10" height="20" rx="2"/><path d="M12 18h.01"/></symbol>
  <symbol id="i-bulb" viewBox="0 0 24 24"><path d="M9 21h6"/><path d="M9 18h6"/><path d="M12 2a7 7 0 0 0-4 12.7V17h8v-2.3A7 7 0 0 0 12 2z"/></symbol>
  <symbol id="i-eye" viewBox="0 0 24 24"><path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"/><circle cx="12" cy="12" r="3"/></symbol>
  <symbol id="i-mute" viewBox="0 0 24 24"><path d="M11 5L6 9H2v6h4l5 4V5z"/><line x1="23" y1="9" x2="17" y2="15"/><line x1="17" y1="9" x2="23" y2="15"/></symbol>
  <symbol id="i-mic" viewBox="0 0 24 24"><path d="M12 1a3 3 0 0 0-3 3v8a3 3 0 0 0 6 0V4a3 3 0 0 0-3-3z"/><path d="M19 10v2a7 7 0 0 1-14 0v-2"/><line x1="12" y1="19" x2="12" y2="23"/><line x1="8" y1="23" x2="16" y2="23"/></symbol>
  <symbol id="i-clap" viewBox="0 0 24 24"><path d="M4 11h16v11H4z"/><path d="M4 11l4-8"/><path d="M10 3l4 8"/><path d="M14 3l4 8"/></symbol>
  <symbol id="i-block" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><line x1="4.93" y1="4.93" x2="19.07" y2="19.07"/></symbol>
  <symbol id="i-clock" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></symbol>
</svg>
```

Add new icons to this sprite sheet as needed. Follow the same pattern: 24x24 viewBox, white stroke paths, 2px stroke-width, round caps and joins.

---

## 4. Interaction Layer

Three interactive effects run on desktop only. All are disabled on touch devices via `@media (hover: none)` and a JS `isMobile` check.

### 4.1 Gold Particle Constellation

A fixed `<canvas>` element behind all content. 140 gold particles drift slowly upward. When the cursor gets within 180px, particles scatter outward. When two particles come within 160px, a thin gold line connects them.

```html
<canvas id="particles"></canvas>
```

CSS: `#particles { position: fixed; inset: 0; z-index: 0; pointer-events: none; }`

Particle settings: count=140, connection distance=160px, repel distance=180px, particle alpha=0.2-0.75, line alpha=0.18 max, particle size=0.8-3px.

### 4.2 Ambient Cursor Glow

A 600px soft radial gold light that follows the mouse. 9% gold opacity at centre, fading to transparent. Creates a torchlight effect over the glassmorphism cover card and light sections.

```html
<div id="cursor-glow"></div>
```

CSS: `#cursor-glow { position: fixed; width: 600px; height: 600px; border-radius: 50%; background: radial-gradient(circle, rgba(168,133,31,0.09) 0%, rgba(168,133,31,0.03) 40%, transparent 70%); pointer-events: none; z-index: 1; transform: translate(-50%, -50%); transition: opacity 0.3s; opacity: 0; }`

### 4.3 Magnetic Cards

Any element with `.magnetic` class tilts toward the cursor on mousemove using `perspective(800px)` with +/-5 degrees rotation on both axes plus `scale(1.02)`. Resets smoothly on mouseleave.

Apply `.magnetic` to: counter cards, feature cards, solution cards, invest card, table-wrap, flow-body cards.

### 4.4 Fade-In on Scroll

Every `.inner` wrapper inside a band gets the `.reveal` class. IntersectionObserver adds `.visible` when 8% of the element is in the viewport. Transition: opacity 0.7s + translateY 24px to 0.

---

## 5. Complete CSS Reference

Copy this entire CSS block into every proposal. Includes all component styles, interaction layer styles, and responsive breakpoints.

(The complete CSS is the `<style>` block from the BFTF Creative Gap Analysis document. It serves as the canonical reference. Copy it verbatim as the starting point for every new document.)

---

## 6. JavaScript Reference

Include all JS inside a single `<script>` block at the bottom of the document, wrapped in an IIFE. The JS handles:

1. **Particle constellation** — canvas animation loop with IntersectionObserver
2. **Cursor glow** — mousemove position tracking
3. **Magnetic cards** — mousemove 3D rotation calculation
4. **Animated counters** — IntersectionObserver + requestAnimationFrame count-up
5. **Fade-in reveal** — IntersectionObserver adding `.visible` class
6. **FAQ accordion** — click handler toggling `.open` class (one open at a time)

All effects check `isMobile = window.matchMedia('(hover: none)').matches` before initialising. Touch devices get no particles, no glow, no magnetic effect.

---

## 7. Writing Guidelines

### Tone
- Consultative, not salesy. Write like a strategist briefing a business owner.
- Direct and confident. Short sentences. No weasel words.
- Use "we" for pointdot actions, "you" for the client.
- Australian English spelling throughout (optimise, colour, analyse).

### Section intros
- Maximum 2 sentences. Centre-aligned. Max-width 580px.

### Callout text
- One sentence summarising the "so what" of the visual above it.
- Centre-aligned. 19px. Bold key figures with `<strong>`.

### Bottom line
- First paragraph: punch. Use `<strong>` for the key sentence.
- Second paragraph (`.sub`): softer, reinforces the logic.

### Investment context
- Always include a concrete ROI anchor.
- Use the total hero for one clear headline that communicates value and time.

### Visual-first rule
- If data can be shown as counter cards, comparison bars, or a table, use the visual component. Do not write paragraphs explaining numbers.
- Feature card descriptions: 2-3 sentences max. The title does the heavy lifting.
- Solution card descriptions: 1-2 sentences max.

### Humanizer rules (apply to all copy)
- No em dashes. Use commas, full stops, or semicolons.
- No filler buzzwords (leverage, utilise, streamline, elevate, robust, innovative, seamless).
- No exclamation marks.
- No rule-of-three negative parallelisms ("It's not just X, it's Y").
- No -ing superficial analyses (highlighting, underscoring, showcasing).
- Active voice by default.
- Max 20 words per sentence.

---

## 8. File Output

- **Filename:** `[client_slug]_[document_type].html` (lowercase, underscores).
- **Location:** `/mnt/user-data/outputs/`.
- **Single file.** All CSS in `<style>`, all JS in `<script>`, SVG sprite sheet inline. No external resources except Chart.js CDN (if forecast section uses it).
- **`<title>` tag:** `"[Document Type] · [Client Name] × pointdot"`.
- **`<meta name="robots" content="noindex, nofollow">`** in the `<head>`.

---

## 9. Section Alternation Checklist

Before outputting the final document, verify the background alternation:

```
Cover         → gold gradient
Section 1     → white (.band)
Section 2     → grey (.band.band-alt)
Section 3     → white (.band)
Section 4     → grey (.band.band-alt)
...continue alternating...
Bottom Line   → dark (.band.band-dark) — only dark section
Footer        → white (border-top only)
```

**No two adjacent sections should share the same background.** If the content requires it, adjust by adding or removing `band-alt` classes. Cards within sections automatically adapt (grey cards on white bands, white cards on grey bands).

---

## 10. Migration Notes from v4

| v4 (previous) | v5 (current) | Notes |
|---|---|---|
| `--page: #EEECE8` warm beige | `--bg: #ffffff` white | Clean Apple-style white |
| `--grey-*` scale (double-e) | `--text-primary/secondary/tertiary` | Named by function, not shade |
| `--charcoal: #252525` footer | White footer with border-top | Minimal, not dark |
| Single `.page` container (840px) | Full-width `.band` system | Sections own their backgrounds |
| Section dividers (`<div class="divider">`) | No dividers | Spacing + bg alternation handles it |
| 28px section h2, left-aligned | 48px h2, centred | Apple-scale typography |
| 72px section spacing | 100px band padding | Double the breathing room |
| Cards with `1px solid` borders | No visible borders | Background differentiation only |
| 12px border-radius on cards | 20px border-radius | More generous rounding |
| Emojis for icons | Premium SVG icon system (`.pi`) | Gold gradient squares with white line art |
| `.amplify-callout` (gold left border card) | `.callout-text` (plain centred text) | Cleaner, no card wrapper |
| `.bottom-line` (card with gold border) | `.bottom-hero` in `.band-dark` | Full-width dark close |
| `translateY(-3px)` hover | `scale(1.02)` magnetic tilt | 3D perspective effect |
| No interactions | Particles, cursor glow, magnetic cards, fade-in | Desktop only |
| Dark footer (`--charcoal`) | White footer with `border-top` | Minimal |
| `.invest-table` with labels | `.invest-card` + `.total-hero` | Cleaner investment section |
| Step flow `align-items: flex-start` | `align-items: center` | Numbers centred to cards |
| FAQ as static cards | FAQ as accordion (expand/collapse) | Apple-style +/- toggle |
| Counter cards on dark bg only | Counter cards on white or dark bg | Flexible placement |
| Green for positive data | Gold for positive data | Two-colour system (gold + red) |
