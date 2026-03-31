---
name: proposal
description: Build polished, single-file HTML client proposals for pointdot. Use this skill whenever the user asks to create a client proposal, pitch document, strategy deck, or marketing engagement document for a prospective or existing client. Also trigger when the user says "proposal", "pitch", "strategy doc", or references building a document to send to a client with pricing, services, and strategy. Always read this skill before writing any proposal code.
---

# Pointdot Client Proposal — Skill Reference

This document defines the **design system**, **section architecture**, and **component patterns** for building pointdot client proposals as single-file HTML documents. Read this entire file before writing any code.

---

## 1. Design System

### 1.1 Colour Palette (CSS Variables)

```css
:root {
  --black: #0c0c0c;
  --white: #FFFFFF;
  --gold: #a78423;            /* primary accent */
  --gold-dark: #8a6c1c;
  --gold-light: #c9a240;
  --warm: #f4f1ec;            /* page background */
  --surface: #FAF9F7;
  --gray-50: #f9fafb;
  --gray-100: #f3f4f6;
  --gray-200: #e5e7eb;
  --gray-300: #d1d5db;
  --gray-400: #9ca3af;
  --gray-500: #6b7280;
  --gray-700: #3f3f46;
}
```

If the user specifies a different accent colour, replace all `--gold*` values and verify contrast on both `--black` and `--warm` backgrounds.

### 1.2 Typography

- **Font family:** `'Aeonik Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif`
- Aeonik Pro is declared via `@font-face` with `local()` references (weights 400 and 500). It will fall back to system fonts gracefully on machines that don't have it installed.
- **Base size:** `16px` on `<html>`.
- **Line height:** `1.55` on `<body>`.

#### Type Scale

| Element | Size | Weight | Tracking | Notes |
|---|---|---|---|---|
| Cover h1 | 52px | 500 | -0.035em | Client name uses `--gold` colour via `.brand` span |
| Section h2 | 30px | 500 | -0.025em | `--black` colour |
| Section label | 10px | 500 | 0.16em | Uppercase, `--gold-dark`, bottom border `--gold-light` |
| Section intro | 15px | 400 | — | `--gray-700`, max-width 680px, line-height 1.7 |
| Card title | 14px | 500 | -0.01em | `--black` |
| Card description | 12px | 400 | — | `--gray-500`, line-height 1.55 |
| Table header (th) | 10px | 500 | 0.1em | Uppercase, `--gold-light` on `--black` background |
| Table body (td) | 13px | 400 | — | Standard colour |
| Stat card value | 26px | 500 | -0.02em | `--black` |
| Stat card label | 10px | 500 | 0.1em | Uppercase, `--gray-500` |
| Cover subtitle | 17px | 400 | — | `rgba(255,255,255,0.55)` |
| Cover meta label | 9px | 400 | 0.15em | Uppercase, `rgba(255,255,255,0.35)` |
| Cover meta value | 14px | 400 | — | White |

### 1.3 Layout

- **Page container:** `max-width: 820px`, centered, `padding: 64px 28px 0`.
- **Section spacing:** `margin-bottom: 56px`.
- **Card border radius:** `14px` for primary cards, `12px` for tables and smaller elements.
- **Card border:** `1px solid var(--gray-200)`.
- **Card background:** `var(--white)`.

### 1.4 Global Reset

```css
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
```

---

## 2. Section Architecture

Every proposal follows this section order. Sections marked *(optional)* are only included when the brief provides sufficient data.

### 2.1 Cover

Full-viewport dark section (`--black` background) with centred content.

**Structure:**
- pointdot logo (arrow + text + dot)
- Section label: `"Integrated Marketing Strategy · Confidential"`
- `<h1>` with client name wrapped in `<span class="brand">` (gold)
- Subtitle paragraph (one sentence describing the strategy)
- Gold divider bar (52px wide, 3px tall, gold, centred)
- Metadata row: Prepared by, Date, Classification, POC Period

**Decorative elements:** 2–3 radial-gradient circles (`rgba` gold at low opacity) positioned absolutely, creating subtle depth on the dark background.

**Below the cover:** a 5px-tall gold gradient bar spanning full width.

```html
<div class="cover">
  <div class="cover-circle-1"></div>
  <div class="cover-circle-2"></div>
  <div class="cover-circle-3"></div>
  <div class="cover-inner">
    <div class="logo">
      <div class="logo-arrow"></div>
      <div class="logo-text">pointdot</div>
      <div class="logo-dot"></div>
    </div>
    <div class="cover-label">Integrated Marketing Strategy · Confidential</div>
    <h1><span class="brand">[CLIENT NAME]</span></h1>
    <div class="cover-sub">[One-sentence strategy subtitle]</div>
    <div class="cover-divider"></div>
    <div class="cover-meta">
      <div class="cover-meta-item"><label>Prepared by</label><span>[Name]</span></div>
      <div class="cover-meta-item"><label>Date</label><span>[Month Year]</span></div>
      <div class="cover-meta-item"><label>Classification</label><span>Confidential</span></div>
      <div class="cover-meta-item"><label>POC Period</label><span>[Period]</span></div>
    </div>
  </div>
</div>
<div class="gold-bar"></div>
```

### 2.2 Business Snapshot *(optional)*

**Pattern:** Section label → h2 → intro paragraph → 4-column card grid.

Each card has: `.s-label` (metric name), `.s-value` (big number), `.s-sub` (context line).

```html
<div class="section">
  <div class="section-label">Business snapshot</div>
  <h2>Where [Client] is today</h2>
  <p class="section-intro">[1–2 sentence summary of current state]</p>
  <div class="snapshot-grid">
    <!-- Repeat 3–4 snap-card blocks -->
    <div class="snap-card">
      <div class="s-label">[Metric Name]</div>
      <div class="s-value">[Value]</div>
      <div class="s-sub">[Context]</div>
    </div>
  </div>
</div>
```

**Grid CSS:** `grid-template-columns: repeat(4, 1fr); gap: 14px;` — collapses to `repeat(2, 1fr)` on mobile.

### 2.3 Approach

Short philosophy section. No cards or visuals — just a section label, a punchy h2, and an optional one-line intro paragraph.

```html
<div class="section">
  <div class="section-label">Approach</div>
  <h2>[Strategic philosophy headline]</h2>
  <p class="section-intro" style="margin-bottom:0;">[Optional one-liner]</p>
</div>
```

### 2.4 Performance Targets *(optional)*

**Pattern:** Section label → h2 → intro paragraph → styled table.

Table has a dark header row (`--black` background, `--gold-light` text) and alternating content rows.

| Class | Use |
|---|---|
| `.bold` | Metric name in first column |
| `.muted` | Short-term target (establishing baselines) |
| `.gold-val` | Medium-term target (the payoff) |

Wrap the table in `.table-wrap` for rounded corners and overflow handling.

```html
<div class="table-wrap">
  <table>
    <thead>
      <tr><th>Metric</th><th>[Short-term] Target</th><th>[Medium-term] Target</th></tr>
    </thead>
    <tbody>
      <tr>
        <td class="bold">[Metric]</td>
        <td class="muted">[Baseline / early target]</td>
        <td class="gold-val">[Growth target]</td>
      </tr>
    </tbody>
  </table>
</div>
```

### 2.5 What We'll Build

**Pattern:** Section label → h2 → intro paragraph → 4-column icon card grid.

Each card: emoji icon (24px), title (14px bold), description (12px muted).

```html
<div class="build-cards">
  <div class="build-card">
    <div class="bc-icon">[Emoji]</div>
    <div class="bc-title">[Pillar Name]</div>
    <div class="bc-desc">[1–2 sentence description of what's delivered]</div>
  </div>
</div>
```

**Grid CSS:** Same as snapshot grid — 4-up desktop, 2-up mobile.

### 2.6 How It Works Together *(optional)*

**Pattern:** Section label → h2 → two short paragraphs explaining integration → visual flow diagram.

The flow diagram is a horizontal strip on an accent-colour (`--gold`) background with 3–4 nodes connected by arrows. Each node has a small icon/shape, a label, and a subtitle. Below the nodes is a dark summary bar.

Adapt the number of nodes to match the number of service pillars in the proposal.

### 2.7 Google Ads Forecast *(optional — built per client using project-level forecast files)*

**This section is built fresh for every proposal using dedicated forecast skill and prompt files that live in the project alongside this file.** Before building the forecast component, Claude must read:

- `GOOGLE_ADS_FORECAST_PROMPT.md` — defines required inputs and build instructions.
- `GOOGLE_ADS_FORECAST_SKILL.md` — defines the design system, JS architecture, Chart.js patterns, and scoped CSS.

Those files are the single source of truth for the forecast section's design, logic, and interactivity. Do not deviate from them.

**Integration rules:**
1. Build the forecast as a self-contained block (`.forecast-outer` wrapper) following the forecast skill/prompt files.
2. The forecast block sits **outside** the `.page` container (it is full-width with its own `.forecast-outer` wrapper and `.forecast-inner` max-width container).
3. Close the preceding `</div><!-- .page -->` before the forecast block, then reopen `<div class="page">` after it.
4. If the forecast uses Chart.js, ensure the CDN is in the `<head>`: `<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js"></script>`.
5. The forecast scopes its styles under `#fc` and `.forecast-outer` to avoid collisions with the proposal's core styles.

### 2.8 Phase 3 *(optional)*

Brief scaling note. Section label → h2 → one-line intro. No cards or visuals.

```html
<div class="section">
  <div class="section-label">Phase three</div>
  <h2>Month [X]+: We scale what's working</h2>
  <p class="section-intro" style="margin-bottom:0;">[One sentence about data-driven scaling]</p>
</div>
```

### 2.9 Investment

**Three sub-tables + a total callout block.**

#### Sub-table pattern (`.invest-table`)

Each table is a stack of `.invest-row` divs (flex, space-between).

| Row type | Class | Style |
|---|---|---|
| Header | `.invest-row.header` | `--black` background, gold uppercase text |
| Item | `.invest-row` | Standard, optional `<br><span>` for description |
| Total | `.invest-row.total` | `--warm` background, bold label, gold value |

```html
<div class="invest-section">
  <h3>[Table Title]</h3>
  <div class="invest-table">
    <div class="invest-row header"><span class="r-label">Service</span><span class="r-val">Investment</span></div>
    <div class="invest-row"><span class="r-label">[Line item]</span><span class="r-val">[Price]</span></div>
    <div class="invest-row total"><span class="r-label">Total</span><span class="r-val">[Sum]</span></div>
  </div>
</div>
```

#### Total Callout (`.total-callout`)

Dark block with gold gradient top border. Shows total monthly commitment as a large number, with a supporting paragraph that contextualises the investment as a percentage of revenue and frames ROI.

```html
<div class="total-callout">
  <div class="tc-label">Total Monthly Commitment</div>
  <div class="tc-value">[Total range] / month</div>
  <div class="tc-sub">[2–3 sentences contextualising the investment]</div>
</div>
```

### 2.10 Next Steps

**Pattern:** Section label → h2 → intro paragraph → vertical stack of numbered step cards.

Each step: gold numbered circle (32px) + title + description paragraph.

```html
<div class="steps">
  <div class="step">
    <div class="step-num">[N]</div>
    <div class="step-text">
      <strong>[Step title]</strong>
      <p>[One sentence description]</p>
    </div>
  </div>
</div>
```

### 2.11 Bottom Line

Dark block with gold gradient top border. A closing argument that ties together the client's current position, the opportunity, and what the strategy will deliver.

```html
<div class="bottom-line">
  <div class="bl-label">The bottom line</div>
  <p>[Main closing argument — 1–2 sentences, punchy]</p>
  <p class="sub">[Supporting context — 2–3 sentences, softer tone]</p>
</div>
```

### 2.12 Footer

Full-width dark bar with pointdot logo (left) and a one-line attribution (right).

```html
<footer>
  <div class="footer-logo">
    <div class="footer-logo-arrow"></div>
    <div class="footer-logo-text">pointdot</div>
    <div class="footer-logo-dot"></div>
  </div>
  <p>Prepared for [Client Name] &nbsp;·&nbsp; Confidential &nbsp;·&nbsp; [Month Year]</p>
</footer>
```

---

## 3. Component CSS Reference

Below is the complete CSS for all components. Copy this block into the `<style>` tag of every proposal. The forecast section carries its own scoped styles (defined in the forecast skill file) — those get added to the proposal's `<style>` block when the forecast is included.

### 3.1 Core Styles

```css
@font-face {
  font-family: 'Aeonik Pro';
  src: local('Aeonik Pro'), local('AeonikPro-Regular');
  font-weight: 400;
}
@font-face {
  font-family: 'Aeonik Pro';
  src: local('Aeonik Pro Medium'), local('AeonikPro-Medium');
  font-weight: 500;
}

:root {
  --black: #0c0c0c;
  --white: #FFFFFF;
  --gold: #a78423;
  --gold-dark: #8a6c1c;
  --gold-light: #c9a240;
  --warm: #f4f1ec;
  --surface: #FAF9F7;
  --gray-50: #f9fafb;
  --gray-100: #f3f4f6;
  --gray-200: #e5e7eb;
  --gray-300: #d1d5db;
  --gray-400: #9ca3af;
  --gray-500: #6b7280;
  --gray-700: #3f3f46;
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { font-size: 16px; }
body { font-family: 'Aeonik Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif; background: var(--warm); color: var(--black); line-height: 1.55; }

/* Cover */
.cover { background: var(--black); min-height: 100vh; display: flex; align-items: center; justify-content: center; position: relative; overflow: hidden; }
.cover-circle-1 { position: absolute; width: 700px; height: 700px; border-radius: 50%; background: radial-gradient(circle, rgba(167,132,35,0.07) 0%, transparent 70%); top: -30%; right: -10%; }
.cover-circle-2 { position: absolute; width: 520px; height: 520px; border-radius: 50%; background: radial-gradient(circle, rgba(167,132,35,0.04) 0%, transparent 70%); bottom: -20%; left: -5%; }
.cover-circle-3 { position: absolute; width: 260px; height: 260px; border-radius: 50%; background: radial-gradient(circle, rgba(167,132,35,0.05) 0%, transparent 70%); top: 25%; left: 28%; }
.cover-inner { position: relative; z-index: 1; text-align: center; padding: 60px 32px 56px; max-width: 780px; }
.logo { display: flex; align-items: center; justify-content: center; gap: 6px; margin-bottom: 48px; }
.logo-arrow { width: 0; height: 0; border-top: 6px solid transparent; border-bottom: 6px solid transparent; border-left: 11px solid var(--gold); }
.logo-text { font-size: 18px; font-weight: 500; color: var(--white); letter-spacing: -0.01em; }
.logo-dot { width: 7px; height: 7px; border-radius: 50%; background: var(--gold); margin-left: 2px; }
.cover-label { font-size: 10px; text-transform: uppercase; letter-spacing: 0.22em; color: var(--gold); margin-bottom: 24px; font-weight: 400; }
.cover h1 { font-size: 52px; font-weight: 500; line-height: 1.08; color: var(--white); letter-spacing: -0.035em; margin-bottom: 18px; }
.cover h1 .brand { color: var(--gold); }
.cover-sub { font-size: 17px; color: rgba(255,255,255,0.55); max-width: 520px; margin: 0 auto 36px; line-height: 1.5; font-weight: 400; }
.cover-divider { width: 52px; height: 3px; background: var(--gold); margin: 0 auto 36px; border-radius: 2px; }
.cover-meta { display: flex; flex-wrap: wrap; justify-content: center; gap: 36px; }
.cover-meta-item { text-align: left; }
.cover-meta-item label { display: block; font-size: 9px; text-transform: uppercase; letter-spacing: 0.15em; color: rgba(255,255,255,0.35); margin-bottom: 4px; font-weight: 400; }
.cover-meta-item span { font-size: 14px; color: var(--white); font-weight: 400; }
.gold-bar { height: 5px; background: linear-gradient(90deg, var(--gold), var(--gold-light), var(--gold)); }

/* Page container */
.page { max-width: 820px; margin: 0 auto; padding: 64px 28px 0; }
.section { margin-bottom: 56px; }
.section-label { font-size: 10px; text-transform: uppercase; letter-spacing: 0.16em; color: var(--gold-dark); margin-bottom: 10px; font-weight: 500; display: inline-block; padding-bottom: 4px; border-bottom: 1px solid var(--gold-light); }
.section h2 { font-size: 30px; font-weight: 500; letter-spacing: -0.025em; margin-bottom: 12px; line-height: 1.2; color: var(--black); }
.section-intro { font-size: 15px; color: var(--gray-700); line-height: 1.7; margin-bottom: 28px; max-width: 680px; }

/* Snapshot grid */
.snapshot-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 14px; }
.snap-card { background: var(--white); border: 1px solid var(--gray-200); border-radius: 14px; padding: 20px 18px; }
.snap-card .s-label { font-size: 10px; text-transform: uppercase; letter-spacing: 0.1em; color: var(--gray-500); margin-bottom: 8px; font-weight: 500; }
.snap-card .s-value { font-size: 26px; font-weight: 500; color: var(--black); letter-spacing: -0.02em; line-height: 1.1; margin-bottom: 5px; }
.snap-card .s-sub { font-size: 12px; color: var(--gray-400); }

/* Build cards */
.build-cards { display: grid; grid-template-columns: repeat(4, 1fr); gap: 14px; }
.build-card { background: var(--white); border: 1px solid var(--gray-200); border-radius: 14px; padding: 22px 18px; }
.build-card .bc-icon { font-size: 24px; margin-bottom: 10px; }
.build-card .bc-title { font-size: 14px; font-weight: 500; color: var(--black); margin-bottom: 6px; letter-spacing: -0.01em; }
.build-card .bc-desc { font-size: 12px; color: var(--gray-500); line-height: 1.55; }

/* Tables */
.table-wrap { overflow-x: auto; margin-top: 24px; border: 1px solid var(--gray-200); border-radius: 12px; }
table { width: 100%; border-collapse: collapse; font-size: 13px; }
thead { background: var(--black); }
th { text-align: left; padding: 14px 18px; font-size: 10px; font-weight: 500; text-transform: uppercase; letter-spacing: 0.1em; color: var(--gold-light); }
td { padding: 16px 18px; border-top: 1px solid var(--gray-100); }
tr:hover td { background: var(--gray-50); }
.bold { font-weight: 500; color: var(--black); }
.muted { color: var(--gray-500); }
.gold-val { color: var(--gold-dark); font-weight: 500; }

/* Investment tables */
.invest-section { margin-bottom: 28px; }
.invest-section h3 { font-size: 12px; font-weight: 500; text-transform: uppercase; letter-spacing: 0.08em; color: var(--gray-700); margin-bottom: 12px; }
.invest-table { background: var(--white); border: 1px solid var(--gray-200); border-radius: 12px; overflow: hidden; }
.invest-row { display: flex; justify-content: space-between; align-items: center; padding: 16px 20px; border-bottom: 1px solid var(--gray-100); font-size: 13px; }
.invest-row:last-child { border-bottom: none; }
.invest-row:not(.header):not(.total):hover { background: var(--gray-50); }
.invest-row.header { background: var(--black); }
.invest-row.header .r-label,
.invest-row.header .r-val { font-size: 10px; font-weight: 500; letter-spacing: 0.11em; text-transform: uppercase; color: var(--gold-light); }
.invest-row.total { background: var(--warm); }
.invest-row.total .r-label { font-weight: 500; color: var(--black); font-size: 14px; }
.invest-row.total .r-val { font-weight: 500; color: var(--gold-dark); font-size: 14px; }
.invest-row .r-label { color: var(--gray-700); }
.invest-row .r-val { color: var(--black); text-align: right; font-weight: 400; white-space: nowrap; padding-left: 32px; }

/* Total callout */
.total-callout { background: var(--black); border-radius: 12px; padding: 36px 40px; margin-top: 28px; position: relative; overflow: hidden; }
.total-callout::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 3px; background: linear-gradient(90deg, var(--gold), var(--gold-light), transparent); }
.total-callout .tc-label { font-size: 10px; text-transform: uppercase; letter-spacing: 0.15em; color: var(--gold); margin-bottom: 12px; font-weight: 500; }
.total-callout .tc-value { font-size: 34px; font-weight: 500; color: var(--white); letter-spacing: -0.03em; margin-bottom: 12px; }
.total-callout .tc-sub { font-size: 13px; color: rgba(255,255,255,0.4); line-height: 1.65; max-width: 600px; }

/* Next steps */
.steps { display: flex; flex-direction: column; gap: 12px; }
.step { display: flex; gap: 18px; align-items: flex-start; background: var(--white); border: 1px solid var(--gray-200); border-radius: 12px; padding: 20px 22px; }
.step-num { width: 32px; height: 32px; border-radius: 50%; background: var(--gold); color: var(--white); display: flex; align-items: center; justify-content: center; font-size: 13px; font-weight: 500; flex-shrink: 0; margin-top: 1px; }
.step-text strong { display: block; font-size: 14px; font-weight: 500; margin-bottom: 5px; letter-spacing: -0.01em; color: var(--black); }
.step-text p { font-size: 13px; color: var(--gray-700); line-height: 1.65; }

/* Bottom line */
.bottom-line { background: var(--black); border-radius: 16px; padding: 44px 48px; position: relative; overflow: hidden; margin-bottom: 64px; }
.bottom-line::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 3px; background: linear-gradient(90deg, var(--gold), var(--gold-light), transparent); }
.bottom-line .bl-label { font-size: 10px; text-transform: uppercase; letter-spacing: 0.16em; color: var(--gold); margin-bottom: 16px; font-weight: 500; }
.bottom-line p { font-size: 17px; font-weight: 400; line-height: 1.6; color: rgba(255,255,255,0.85); margin-bottom: 16px; letter-spacing: -0.01em; }
.bottom-line .sub { font-size: 13px; color: rgba(255,255,255,0.4); line-height: 1.75; margin-bottom: 0; font-weight: 400; }

/* Footer */
footer { background: var(--black); padding: 28px 36px; display: flex; align-items: center; justify-content: space-between; flex-wrap: wrap; gap: 12px; }
.footer-logo { display: flex; align-items: center; gap: 6px; }
.footer-logo-arrow { width: 0; height: 0; border-top: 5px solid transparent; border-bottom: 5px solid transparent; border-left: 9px solid var(--gold); }
.footer-logo-text { font-size: 15px; font-weight: 500; color: var(--white); letter-spacing: -0.01em; }
.footer-logo-dot { width: 6px; height: 6px; border-radius: 50%; background: var(--gold); margin-left: 2px; }
footer p { font-size: 12px; color: rgba(255,255,255,0.28); }

/* Responsive */
@media (max-width: 680px) {
  .cover-inner { padding: 48px 24px 44px; }
  .cover h1 { font-size: 36px; }
  .cover-meta { gap: 22px; }
  .snapshot-grid { grid-template-columns: repeat(2, 1fr); }
  .build-cards { grid-template-columns: repeat(2, 1fr); }
  footer { flex-direction: column; align-items: flex-start; }
}
```

---

## 4. Writing Guidelines

### Tone
- Consultative, not salesy. Write like a strategist briefing a business owner.
- Direct and confident. Short sentences. No weasel words.
- Use "we" for pointdot actions, "you" for the client.

### Section intros
- Maximum 2 sentences. First sentence states what this section covers. Second sentence (if needed) adds strategic context.

### Bottom line
- First paragraph: punch — state the opportunity gap clearly.
- Second paragraph (`.sub`): softer, reinforces the logic and timeline.

### Investment context
- Always frame the total as a percentage of the client's current revenue.
- Always include a concrete ROI anchor ("A single additional [unit] per [period] more than covers the retainer").

---

## 5. File Output

- **Filename:** `[client_slug]_proposal.html` (lowercase, underscores).
- **Location:** `/mnt/user-data/outputs/`.
- **Single file.** All CSS in `<style>`, all JS in `<script>` (forecast JS included inline when forecast section is present), no external resources except Chart.js CDN (if forecast uses it).
- **`<title>` tag:** `"Integrated Marketing Strategy · [Client Name] x pointdot"`.
