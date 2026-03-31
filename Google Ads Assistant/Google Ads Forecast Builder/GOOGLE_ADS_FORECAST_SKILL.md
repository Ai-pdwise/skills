---
name: google-ads-conversion-forecast
description: Build an interactive Google Ads conversion forecast HTML tool for clients who don't yet have an active account. Use this skill whenever the user wants to project Google Ads performance, build a budget forecast, show a client what their ad spend could return, or visualise conversion estimates from Keyword Planner or Google Trends data. Triggers on phrases like "build a forecast", "Google Ads projection", "conversion forecast", "what could this client get from Google Ads", "budget forecast tool", or any request to turn keyword planner data into a client-facing forecast. Always use this skill when a Keyword Planner screenshot or CSV is provided alongside a client brief.
---

# Google Ads Conversion Forecast — Build Skill

This skill produces a self-contained, single-file interactive HTML forecast for clients who don't yet have live Google Ads data. It is designed to be embedded into a broader client report or shared as a standalone document.

---

## ⛔ MANDATORY INTAKE GATE — READ BEFORE DOING ANYTHING ELSE

**Do not begin building the forecast until every required input below has been confirmed. No exceptions.**

If any required input is missing, incomplete, or ambiguous — stop, ask, and wait for a satisfactory answer before proceeding. Do not make assumptions and fill in gaps silently. Do not begin building a partial forecast. Do not proceed tab by tab. The build starts only when the full picture is confirmed.

This gate exists because the formula inputs (CPC, CVR, market size, budget range) are interdependent. Building with incomplete data produces a forecast that will need to be partially or fully rebuilt — wasting time for both parties.

---

### Required inputs checklist

Before proceeding, confirm ALL of the following are in hand:

| # | Input | What to look for |
|---|---|---|
| 1 | **Client name** | Any name or trading name |
| 2 | **Client website or brand colour** | Used to derive brand aesthetic |
| 3 | **Target location(s)** | City, region, or national |
| 4 | **Primary campaign category** | The Starter tab focus — what are they primarily selling? |
| 5 | **Number of campaign categories** | Determines tab structure — 1 category = Starter only, 2+ categories = Starter + Scale |
| 6 | **Conversion type** | What counts as a conversion — form fill, call, booking, etc. |
| 7 | **Conversion label** | What to call conversions in the UI — "enquiries", "bookings", "leads" |
| 8 | **Keyword Planner data** | Screenshot or CSV — must include keyword, avg monthly searches, high-range bid |
| 9 | **Budget ranges** | Starter min/max and Scale min/max |
| 10 | **Google Trends data** | Screenshot showing interest over time for the category + location |
| 11 | **Aeonik Pro font files** | `AeonikPro-Regular.otf`, `AeonikPro-Medium.otf`, `Aeonik_Pro_Bold.ttf` — must be attached for base64 embedding |

If items 8 or 10 (data attachments) are missing, do not proceed — these are the foundation of the formula. Politely but firmly tell the user what is missing and why it is needed before the build can start.

---

### Category count — tab structure logic

**Item 5 must always be asked via the `ask_user_input` widget.** Use this exact framing:

> "How many campaign categories are we building into this forecast?"
> Options: `1 category` / `2 categories` / `3+ categories`

The answer drives the entire tab structure:

| Answer | Tab structure | What to ask next |
|---|---|---|
| **1 category** | Single tab only — remove the Scale tab entirely | Ask for Keyword Planner + Trends for that one category. Budget range is a single slider (no Starter/Scale split — just min → max). |
| **2 categories** | Two tabs — Starter (primary) + Scale (primary + secondary combined) | Ask for separate Keyword Planner data and Google Trends screenshots for **each** category before proceeding |
| **3+ categories** | Two tabs — Starter (primary) + Scale (all categories combined) | Ask for Keyword Planner data and Google Trends for **each** category individually before proceeding |

**Critical rule for 2+ categories:** Do not begin building until keyword data and Trends screenshots have been provided for every category. If the user provides data for one category but not the others, ask for the remaining data before starting. Each category needs its own:
- Keyword Planner export (keyword, avg monthly searches, high-range bid)
- Google Trends screenshot (interest over time, correct location and time range)

---

### How to ask clarifying questions

Follow these rules precisely when asking for missing information. **Never batch all missing questions into a single wall of text.** Group logically, but keep it readable.

#### Use the `ask_user_input` widget when:
- The answer is bounded and predictable (2–4 likely options cover the realistic range)
- The question is a choice between defined options, not a description
- Forcing the answer into multiple choice does not lose important nuance

**Examples of widget-appropriate questions:**
- "What counts as a conversion?" → options: Form fill / Phone call / Online booking / Multiple
- "Is this Sydney only, or multiple locations?" → options: Sydney only / Multiple cities / National
- "Do you have a Scale keyword set, or should the Scale tab use the same keywords at higher spend?" → Yes, separate keywords / No, same keywords / Not sure yet
- "Is this being embedded into an existing report?" → Yes / No

#### Use a free-type question in chat when:
- The answer requires detail, nuance, or context that a list cannot capture
- The question is open-ended or descriptive
- The realistic range of answers is too broad or unpredictable for options

**Examples of free-type questions:**
- "What's the client's website URL?"
- "What should we call conversions in the UI — e.g. enquiries, bookings, leads?"
- "Are there any nuances about the keyword data I should know before interpreting it?"
- "What's the ceiling alert's recommended next step — e.g. which cities should it suggest for national expansion?"

#### Never do this:
- ❌ Force an open-ended answer into multiple choice (e.g. don't offer "Other" as the only escape hatch for a complex question)
- ❌ Ask more than 3 questions in a single turn — prioritise the most blocking gaps first
- ❌ Proceed after receiving partial answers and silently assume the rest
- ❌ Ask for information that has already been provided earlier in the conversation

---

### Handling the keyword data

When Keyword Planner data is attached, extract and summarise what you've read back to the user **before** applying it — confirming your interpretation:

- How many keywords found
- Total raw search volume
- Estimated deduplicated unique market size (after clustering)
- Weighted average CPC (high-range)
- Any national terms you've adjusted for city population share
- Any anomalies or gaps that need clarification

**Wait for confirmation before proceeding.** If the user says "looks right, go ahead" — proceed. If they correct anything — update and reconfirm.

When Google Trends data is attached, note:
- Whether demand is consistent, seasonal, or growing/declining
- Whether this changes the conservative discount or should be noted in the methodology section
- Flag any notable signals (e.g. rising queries, Sydney-specific decline) worth including in the forecast narrative

---

### Only proceed when:

- [ ] All 11 required inputs are confirmed
- [ ] Keyword data has been extracted, summarised, and confirmed by the user
- [ ] Budget ranges are explicit for both tabs
- [ ] Aeonik Pro font files are attached and readable
- [ ] You have enough to populate the JS `CFG` object for both `starter` and `scale` without guessing

If you are unsure whether you have enough — ask. It is always better to ask one more clarifying question than to build a forecast on an assumption.

---

## What It Builds

A dark-themed, luxury-styled interactive HTML page with:
- A slider the client can drag to adjust monthly budget
- Three live-updating stat cards (clicks, effective CPC, total conversions)
- A conversion breakdown into form fills + phone calls
- A chart showing median projection with upper (optimistic) and lower (pessimistic) error bands
- A market ceiling line on the Scale tab (dashed red) showing Sydney saturation point
- A ceiling alert that fires when impression share approaches ~58%
- A plain-language methodology note at the bottom

---

## Design System

Always apply this aesthetic. Do not deviate.

**Theme: Light — warm off-white base**

- **Background:** `#EEEDEA` — warm off-white, the primary page background
- **Surface cards:** `#FFFFFF` (primary cards) and `#F5F4F1` (secondary/nested surfaces)
- **Gold accent:** `#B8832E` — used for slider, active chart points, stat highlight card, eyebrow text, tab active state. Slightly deeper than the dark-theme gold to read clearly on light backgrounds.
- **Primary text:** `#1A1A1A`
- **Soft text:** `#4A4A4A`
- **Muted text:** `#7A7A7A`
- **Borders:** `rgba(0,0,0,0.08)` — subtle, light
- **Ceiling line:** `rgba(200,60,40,0.6)` — dashed red, slightly stronger opacity than dark theme to maintain visibility
- **Error band fill:** `rgba(184,131,46,0.10)` upper / `rgba(184,131,46,0.07)` lower — two-tone gold shadow above and below median
- **Slider track (empty):** `#D8D6D2`
- **Stat highlight card (gold):** background `#B8832E`, text `#FFFFFF`

**Typography:**
- **Main client name heading only:** Cormorant Garamond (serif) — loaded via Google Fonts. Used sparingly for the large italic display header.
- **All UI, body, labels, numbers, buttons, notes:** Aeonik Pro — custom font, **must be base64-embedded** directly in each HTML file's `<style>` block. Never load from Google Fonts or any CDN.

**Aeonik Pro weights and usage:**

| Weight | File | CSS weight | Use for |
|---|---|---|---|
| Regular | `AeonikPro-Regular.otf` | `400` | Body text, formula notes, hints, slider range labels |
| Medium | `AeonikPro-Medium.otf` | `500` | UI labels, eyebrow text, pill text, model strip labels |
| Bold | `Aeonik_Pro_Bold.ttf` | `700` | Stat values, budget display, tab labels, model strip values |

**@font-face block — insert inside every HTML `<style>` tag:**
```css
@font-face {
  font-family: 'Aeonik';
  src: url('data:font/otf;base64,{{AEONIK_REGULAR_B64}}') format('opentype');
  font-weight: 400; font-style: normal;
}
@font-face {
  font-family: 'Aeonik';
  src: url('data:font/otf;base64,{{AEONIK_MEDIUM_B64}}') format('opentype');
  font-weight: 500; font-style: normal;
}
@font-face {
  font-family: 'Aeonik';
  src: url('data:font/ttf;base64,{{AEONIK_BOLD_B64}}') format('truetype');
  font-weight: 700; font-style: normal;
}
```

Replace `{{AEONIK_REGULAR_B64}}`, `{{AEONIK_MEDIUM_B64}}`, `{{AEONIK_BOLD_B64}}` with base64 strings read from the uploaded `.otf`/`.ttf` files. Font files are always provided by the user at brief time. **If font files are not attached to the brief, ask for them before building.** Do not skip this step or substitute another font.

Remove the Google Fonts `<link>` for Manrope — fully replaced by Aeonik. Keep the Cormorant Garamond Google Fonts link for the display header only.

Apply `font-family: 'Aeonik', sans-serif` to `body`. Apply `font-family: 'Cormorant Garamond', serif` only to the `h1` element.

Apply the client's brand colour only if it does not conflict with the gold system. If the client has a strong brand colour, consider using it for tab highlights or category pills. On a light background, brand colours generally integrate more easily than on dark.

---

## Tab Structure

Tab structure is determined by the number of campaign categories confirmed during intake — not assumed to always be two tabs.

| Categories | Tab structure |
|---|---|
| 1 | Single tab — Starter only. Scale tab is removed entirely. Budget range is a single min → max slider. |
| 2 | Two tabs — Starter (primary category) + Scale (both categories combined) |
| 3+ | Two tabs — Starter (primary category) + Scale (all categories combined) |

Each tab has its **own model strip** (4 cells: CPC, CVR, Market Size, Ceiling or Decay Model).

The Starter tab shows the Decay Model (α value). The Scale tab shows the Market Ceiling number instead.

For single-category builds, the model strip shows all four values on the one tab: CPC, CVR, Market Size, and Decay Model.

---

## Formula Architecture

### Three scenario model

Every chart renders three data series:

1. **Median** (solid gold line) — the primary projection, mid-decay
2. **Optimistic** (upper dashed shadow) — mild decay, lower CPC pressure
3. **Pessimistic** (lower dashed shadow) — steep decay, higher CPC pressure

The shaded band between optimistic and pessimistic widens at higher budgets, reflecting real-world variance.

### Core formula

```
Median conversions = baseConv × (budget / baseMin) ^ α
```

Where:
- `baseConv = (baseMin / baseCPC) × baseCVR`
- `α = 0.65` (median decay exponent)
- Result is capped at `maxConv = mktSearches × maxIS × baseCVR`

### Optimistic variant
- `α = 0.82`
- CPC scale pressure at 40% of median (flatter CPC curve)

### Pessimistic variant
- Steeper CPC growth (cpcScale × 1.8)
- Additional CVR decay: `clicks × baseCVR × (budget/baseMin)^-0.18`
- Floor: never below 30% of base conversion rate

### CPC growth model
```
effectiveCPC = baseCPC × (budget / baseMin) ^ cpcScale
```
- Starter: `cpcScale = 0.12`
- Scale: `cpcScale = 0.14` (chauffeur/wedding market is more competitive)

### Market ceiling
```
maxConv = mktSearches × 0.80 × baseCVR
```
- 0.80 = maximum realistic impression share (80%)
- Ceiling alert fires at ≥58% impression share

---

## Input Derivation Rules

Apply these rules to convert raw Keyword Planner data into model inputs.

### CPC
- Always use the **top-of-page high-range bid** — this is the conservative input
- If multiple keywords, take a weighted average by volume
- For Scale tabs with high-CPC anchor keywords (e.g. "chauffeur hire" at $7.11), weight the blended CPC accordingly

### CVR
- Baseline: 4.5–6% is the luxury automotive industry benchmark for form fills
- Apply a **30% new account discount** → results in ~3.0–4.2% effective form fill CVR
- Phone calls add ~1.0–1.5% on top
- Combined CVR:
  - Starter (self-drive): **4.2%** (65% form / 35% phone)
  - Scale (multi-category): **4.0%** (60% form / 40% phone — chauffeur/wedding skew more toward phone)

### Market size (deduplication rules)
1. Sum all raw keyword volumes
2. Identify intent clusters — keywords covering the same search intent (e.g. "wedding car hire" + "wedding chauffeur hire" = one cluster, count once)
3. For broad national keywords (no location modifier): apply **~20% Sydney population share**
4. Result = deduplicated unique monthly searches

### Conservative discount summary
On average, the model projects approximately **40% below a standard linear forecast** across realistic budget ranges. This results from three compounding factors:
1. CPC sourced from high-range market bids
2. CVR discounted ~30–40% below industry benchmark
3. Power curve decay (α = 0.65) reducing returns at scale

---

## Conversion Breakdown

Always split total projected conversions into:
- **Form fills** — primary conversion path
- **Phone calls** — secondary, requires call tracking to be enabled

Split ratios by tab type:

| Tab type | Form fills | Phone calls |
|---|---|---|
| Self-drive hire | 65% | 35% |
| Chauffeur / wedding / multi-category | 60% | 40% |

Higher phone splits apply to high-consideration, high-ticket categories where customers want to speak before booking.

---

## Methodology Note (bottom of each panel)

Always include three sections at the bottom of each panel:

**Data Pull** — List sources used (Google Keyword Planner, Google Search Trends, date)

**Data Interpretation** — State the ~40% conservative discount, explain the three inputs (CPC sourced from high-range bids, CVR discounted below benchmark, returns modelled to decay at scale).

**The Formula** — Plain English only. No Greek letters, no α values. Explain: budget → clicks → conversion rate → enquiries, with the bend in the curve explained as "clicks get slightly more expensive and harder to convert as spend increases."

**Starter vs Scale** — Always explain the difference between the two tabs on both panels so the client understands regardless of which tab they're reading.

---

## Scale Tab Extras

The Scale tab includes two additional elements the Starter tab does not:

1. **Category pills** — small pill badges showing which campaign categories are included (e.g. 🚗 Self-Drive Hire, 🎩 Chauffeur Hire, 💍 Wedding Car Hire)

2. **Ceiling alert** — fires when `impressionShare >= 58`, reads:
> "Sydney market ceiling approaching. At this budget you're capturing the majority of available searches across all categories. National expansion (Melbourne, Brisbane, Perth) is the logical next step."

Adjust city names to match the client's actual market.

---

## File Output

- Single `.html` file, no external dependencies except Chart.js CDN and Google Fonts
- All JS and CSS inline
- Filename format: `[clientname]-google-ads-forecast.html`

---

## Quality Checks Before Delivering

- [ ] Slider initialises correctly and both tabs show values on load
- [ ] CPC increases as slider moves right (not flat)
- [ ] Optimistic line is always above median, pessimistic always below
- [ ] Chart error band fills correctly between the two shadow lines
- [ ] Ceiling line appears only on Scale tab
- [ ] Ceiling alert fires and dismisses correctly as slider moves
- [ ] Form fill + phone call values sum to total conversions (rounding ±1 is acceptable)
- [ ] Formula note present on both panels with all three sections
- [ ] Model strip values match the JS config constants exactly
