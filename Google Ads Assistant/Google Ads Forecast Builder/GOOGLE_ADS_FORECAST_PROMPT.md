---
name: google-ads-forecast-brief
description: Brief template for building a Google Ads conversion forecast. Use this skill whenever the user wants to start a new forecast brief, fill in forecast inputs, or provide client details for a Google Ads projection. Triggers on phrases like "new forecast brief", "brief a forecast", "fill in the forecast template", "forecast inputs for [client]", or any request to collect and structure the required data before building a forecast. This is the intake document — it captures client name, location, campaign categories, conversion type, budget ranges, keyword data, and Google Trends before handing off to the build skill. Always use this skill first when initiating a new forecast, then hand off to the google-ads-conversion-forecast build skill once all inputs are confirmed.
---

# Google Ads Conversion Forecast — Client Brief Template

Use this prompt to brief Claude when building a new forecast for a client.
Fill in every field marked **[REQUIRED]**. Fields marked [OPTIONAL] improve accuracy but are not blocking.

Attach Keyword Planner screenshots or CSV exports directly to this message.

> **⚠️ Important:** Claude will not begin building the forecast until all required inputs are confirmed. If anything is missing, Claude will ask for it before proceeding — using clickable multiple choice questions for bounded answers, and free-type questions for anything that needs detail or nuance. This is intentional. Incomplete briefs produce forecasts that need to be rebuilt. Fill in as much as possible before sending.

> **🔤 Fonts:** Always attach the three Aeonik Pro font files to every brief: `AeonikPro-Regular.otf`, `AeonikPro-Medium.otf`, `Aeonik_Pro_Bold.ttf`. These are embedded directly into the HTML. Without them, Claude will ask before building.

---

## Client

**Client name:** [REQUIRED]
**Website:** [OPTIONAL — Claude will scrape for brand colours if provided]
**Brand hex colour:** [OPTIONAL — provide if known, otherwise Claude will derive from website]
**Location(s):** [REQUIRED — e.g. Sydney only / Sydney + Melbourne / National]

---

## Campaign Categories

List all categories this client operates in. These determine how many tabs and keyword sets are needed.

**Primary category (Starter tab):**
[REQUIRED — e.g. "Self-drive luxury car hire", "Emergency plumbing", "Childcare enrolments"]

**Number of campaign categories:**
[REQUIRED — Claude will ask this via widget: 1 / 2 / 3+]
- **1 category** → Single tab forecast, no Scale tab
- **2 categories** → Starter tab (primary) + Scale tab (both combined)
- **3+ categories** → Starter tab (primary) + Scale tab (all combined)

If 2+ categories, list them here and attach separate Keyword Planner + Google Trends data for each:
- Primary category (Starter): ___________
- Additional category/ies (Scale): ___________

---

## Conversion Type

**What counts as a conversion for this client?**
[REQUIRED — choose one or more]
- [ ] Form fill / enquiry
- [ ] Phone call
- [ ] Online booking / purchase
- [ ] Other: ___________

**What should we call conversions in the UI?**
[REQUIRED — e.g. "enquiries", "bookings", "leads", "appointments"]

---

## Budget Scenarios

**Starter tab:**
- Min budget: $[REQUIRED] /mo
- Max budget: $[REQUIRED] /mo
- Step size: $[OPTIONAL — default $50 for <$5K, $250 for <$20K, $500 for $50K+]

**Scale tab:**
- Min budget: $[REQUIRED] /mo
- Max budget: $[REQUIRED] /mo
- Step size: $[OPTIONAL]

---

## Keyword Data

**Attach Keyword Planner export(s) to this message.**

Provide separate exports for Starter and Scale categories if they differ.
At minimum include: keyword, avg. monthly searches, top-of-page bid (high range), top-of-page bid (low range).

**Notes on the keyword data:**
[OPTIONAL — flag anything unusual, e.g. "the high volume term is national, client is Sydney only"]

---

## Google Trends

**Attach Google Trends screenshot(s) if available.**
[OPTIONAL but recommended — helps Claude flag seasonal demand patterns]

Settings used when capturing: [location / time range / search term]

---

## Existing Report

**Is this forecast being embedded into an existing HTML report?**
- [ ] Yes — attach the existing report HTML
- [ ] No — build as a standalone page

If yes, which tab should the forecast live under?
[e.g. "Add as a new tab called 📈 Conversion Forecast"]

---

## Additional Context

[OPTIONAL — anything else Claude should know: competitor landscape, niche audience notes, specific upsell narrative you want the ceiling alert to reference, etc.]

---

## How Claude Will Use This Brief

**Step 1 — Intake gate check**
Claude will verify all 10 required inputs are present before doing anything else. If anything is missing, it will ask — using clickable options for bounded questions (e.g. conversion type, location, tab structure) and free-type questions for anything open-ended (e.g. website URL, conversion label, keyword nuances). Claude will ask no more than 3 questions per turn, prioritising the most blocking gaps first.

**Step 2 — Data extraction and confirmation**
Once keyword data is attached, Claude will extract and summarise its interpretation — keyword count, deduplicated market size, weighted CPC, any population share adjustments for national terms — and ask for your confirmation before proceeding.

**Step 3 — Build**
Only after all inputs are confirmed will Claude derive the model constants and build the HTML. Steps in order:
1. Extract CPC from high-range bids (weighted by volume)
2. Deduplicate keyword volumes into realistic unique market size
3. Apply city population share to national-only terms
4. Set CVR using industry benchmarks, discounted for new account maturity
5. Build the two-tab interactive HTML with median + error band chart
6. Apply the ~40% conservative discount across CPC, CVR, and decay model
7. Populate methodology note with actual data sources and calculated figures

