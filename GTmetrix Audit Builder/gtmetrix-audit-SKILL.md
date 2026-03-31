---
name: gtmetrix-report
version: 1.3.0
description: >
  Build CRO-focused website performance reports from GTmetrix data for Praxio clients.
  Interprets metrics in plain English, filters out misleading data, maps every issue
  to a visible visitor consequence and a fix Praxio can own. Always read this entire
  file before writing or rebuilding any GTmetrix-based client report.
---

# GTmetrix Report — SKILL

This skill governs how Praxio interprets GTmetrix data and structures client-facing performance reports. The goal is always the same: explain what slow metrics cost the business in plain English, present only what is conversion-relevant, and never create scope risk by overstating problems or promising fixes outside Praxio's control.

Read this entire file before writing a single word of a report.

---

## 1. The Purpose of These Reports

These reports are sales and trust tools, not technical audits. They are sent to business owners (not developers) who care about one thing: whether their website is helping or hurting their business.

Every metric must be translated into one of two business outcomes:

- **Visitors leaving before they engage** (bounce and abandonment)
- **Visitors unable to complete an action** (failed bookings, enquiries, purchases)

If a metric cannot be linked to one of those two outcomes, it does not go in the report.

---

## 2. Metric Hierarchy — What to Report and What to Ignore

### TIER 1 — Always include if failing (conversion-critical)

| Metric | What it measures | Good | Needs Work | Critical |
|---|---|---|---|---|
| **LCP** | How fast the main visible content loads | under 2.5s | 2.5s–4s | over 4s |
| **TBT** | How long the page is frozen and unresponsive | under 0.20s | 0.20s–0.60s | over 0.60s |
| **CLS** | Whether page elements jump around on screen | under 0.1 | 0.1–0.25 | over 0.25 |

**TBT display rule — always convert milliseconds to seconds.**
GTmetrix reports TBT in milliseconds. Divide by 1000 and round to 2 decimal places before displaying anywhere in the report.

| Raw GTmetrix value | Display as |
|---|---|
| 435ms | 0.44s |
| 340ms | 0.34s |
| 200ms | 0.20s |
| 150ms | 0.15s |

This keeps all three Core Web Vitals on the same time scale. A client can see that their page appeared at 1.5s but could not be interacted with until 1.94s. That gap is the conversion problem. It is only visible when both numbers speak the same language.

- **Good**: mention briefly as a positive or omit.
- **Needs Work**: include with consequence and fix.
- **Critical**: lead the report around it.

### TIER 2 — Include only if it is the root cause of a Tier 1 failure

| Metric | When to include |
|---|---|
| **FCP** | Only if LCP is also failing and FCP explains why |
| **TTFB** | Only if server response is over 600ms and is the primary cause of LCP failure |
| **Speed Index** | Never. Composite metric, confusing to non-technical readers. |
| **Page Size (MB)** | Only as supporting context for an image issue, not a standalone finding |

### TIER 3 — Never report to clients

| Metric | Why to exclude |
|---|---|
| **Fully Loaded Time** | Includes background scripts completing long after the visitor has left or converted. Always alarmingly high. Never cite. |
| **Total Page Requests** | Does not map to speed or user experience. |
| **Structure Score** | Use internally to find fixes. Never surface to clients. |
| **Onload Time** | A browser event, not a user experience metric. |
| **DOM Interactive / DOM Loaded** | Developer-level. Not relevant to client conversation. |
| **JavaScript execution time** | Supporting data only. Never the headline. |

---

## 3. The One Headline Rule

Every report is built around one primary problem. The single metric that is both failing and most directly responsible for visitors leaving or failing to convert.

**How to choose:**
- TBT Critical: lead with TBT. A frozen page prevents bookings and purchases.
- LCP Critical, TBT acceptable: lead with LCP. Visitors leave before seeing the offer.
- Both Critical: lead LCP (what they see first), support with TBT.
- Only CLS failing: lead with CLS. Tapping the wrong thing destroys trust.

Never spread equal weight across all issues. Pick the villain. The other issues are supporting characters.

---

## 4. The Issue Framework

Every issue must answer all four parts before being written up.

**Part A — Plain-English name.** What the visitor experiences. Not the GTmetrix label.

**Part B — Visitor consequence.** One sentence. What a real visitor experiences when this metric fails.

**Part C — Specific cause.** From the GTmetrix audit panel. If you cannot confirm the cause, do not include the issue.

**Part D — The fix and who owns it.**

| Label | When to use |
|---|---|
| "We fix this" | Fix is fully within Praxio's implementation scope |
| "We can help with this" | Fix requires client action or is platform-constrained |
| "Platform limitation" | Caused by the CMS itself, not fixable without migration |

See Section 10 for how platform mode governs which labels apply.

---

## 5. Scope Safety Rules

**Rule 1.** Never cite Fully Loaded Time as the primary problem.

**Rule 2.** Never promise a specific load time. Write "we aim to significantly improve your LCP and TBT scores" not "we will get your site loading in 2 seconds."

**Rule 3.** Never guarantee a ranking improvement. Write "faster Core Web Vitals can positively influence your Google ranking."

**Rule 4.** Platform determines fix language. WordPress: full confidence. All other platforms: follow MODE B rules in Section 10.

**Rule 5.** Only include issues with confirmed causes. A flag without a confirmed cause is noise.

---

## 6. Report Structure and Section Flow

The report has six sections in a fixed AIDA sequence. Do not reorder. The CTA must be the last element the reader sees before the footer.

### AIDA flow rationale

| Stage | Section | Purpose |
|---|---|---|
| Awareness | Scorecard + Before/After toggle | Current state. The grade. |
| Interest | Speed slider | What this costs you, made personal and quantified. |
| Interest | Google Vitals gauges + current/target toggle | Why Google cares. What the targets look like. |
| Interest | What to fix | Specific problems. Specific ownership. |
| Desire | Homepage observations | Praxio read the actual site. Personalised value that builds want. |
| Action | Broader conversation + CTA | The ask lands at peak desire. Last thing before footer. |

### Scorecard (no number — "Your Results")
GTmetrix grade + LCP + TBT as visual widgets. Before/After toggle beneath. Summary callout box.
Never use Fully Loaded Time as a widget.

### Speed Slider (between Scorecard and Vitals — no section number)
Interactive range slider pre-set to the client's actual TTI. Three output cards (load time, conversion loss %, mobile bounce risk). Consequence text changes at key stops. Conversion bar. Source citation always visible (Portent 2019, Google/Deloitte 2020).

### Section 1 — How Google Scores Your Site
Three arc gauges (LCP, TBT, CLS). Toggle between current scores and Google's target benchmarks. Vitals callout beneath. TBT always in seconds. Good CLS is framed as a win to protect.

### Section 2 — What to Fix First
Maximum four issues ranked by conversion impact. Each: plain-English title, consequence sentence, fix sentence, ownership badge.

### Section 3 — Homepage Observations
Three expandable accordion cards (Above the Fold / Trust Signal / Copywriting). Colour-coded tags. Observations come from reading the live website. See Section 12 for full rules.

### Section 4 — Broader Conversation + CTA
DR-written closing section. Pattern-interrupt headline. Four interactive concern cards. Pointdot backing. 15-minute scoping call CTA. This is the last element before the footer. See Section 13 for full rules.

---

## 7. Copy Rules

1. **Australian English throughout.** Optimise, recognise, colour, behaviour. No -ize spellings.
2. **No em dashes.** Use a full stop, a comma, or rewrite the sentence.
3. **No rule-of-three negatives.** Not "No rebuild. No downtime. No jargon." Write it as a sentence.
4. **No hollow superlatives.** No "industry-leading," "cutting-edge," "seamlessly," "powerful."
5. **No negative parallelism.** Not "it's not just X, it's Y." Just say Y.
6. **No generic conclusions.** End on something specific and actionable.
7. **Grade 6 reading level.** Maximum 20 words per sentence. Split anything longer.
8. **Every sentence must pass the "so what?" test.** If it does not connect to a business outcome, cut it.
9. **Maximum four issues in Section 2.** Never pad with low-priority findings.
10. **Never mention GTmetrix by name** in client-facing copy.
11. **Never name or imply blame toward any agency, ad partner, or third-party provider.** Praxio may itself have implemented the scripts being flagged. All third-party script issues are described purely as technical website configuration issues. Never reference who set it up or how.
12. **Third-party scripts use technical, website-level framing only.** Approved: "analytics and advertising scripts on your site are currently loading before the page is ready for visitors." Forbidden: "your Facebook pixel is causing problems."
13. **Section 4 closes forward, never backward.** The reader has already seen the full picture. Section 4 answers only: what could this business look like when the fixes are done and the broader conversation happens?
14. **Homepage opportunity blocks are under 50 words.** One emoji as a visual anchor. Line breaks between ideas. Written to be scanned in under 3 seconds on mobile.
15. **No location-specific copy in homepage headlines for multi-location businesses.** Suburb names belong in local landing pages and ad copy. The homepage headline must work for all locations equally.

---

## 8. Responsive Design Requirements

Every report must be fully functional on mobile, tablet, and desktop. The majority of recipients open on a phone. Non-negotiable.

### Breakpoints

| Device | Width | Key behaviour |
|---|---|---|
| Mobile small | 320px–380px | Everything single column. All components full width. |
| Mobile standard | 381px–600px | Two-column gauges and metric widgets. Accordion tags hidden. |
| Tablet | 601px–900px | Full layout. Touch targets minimum 44px. |
| Desktop | 900px+ | Constrained to 660px max-width, centred. |

### Mandatory rules

1. **Wrapper: `max-width: 660px; width: 100%`.** No horizontal overflow ever.
2. **CTA button: `width: 100%; box-sizing: border-box` at 600px.** Fixed-width buttons clip at 320px.
3. **Grade widget: `flex: 0 0 100%` at 600px.**
4. **Metric widgets: `flex: 1 1 calc(50% - 5px)` at 600px, `flex: 0 0 100%` at 380px.**
5. **Gauge cards: same two-breakpoint pattern as metric widgets.**
6. **Accordion tags: `display: none` at 600px.** Tag + title text clips at narrow widths.
7. **Gauge toggle labels: 11px at 600px, 10px at 380px.** Both labels are `white-space: nowrap` and will overflow at 320px without this.
8. **Slider output cards: SOC values drop to 16px at 600px, 14px at 380px.**
9. **`section-body` and `vitals-callout` must have explicit base CSS.** These classes have no inherited styles and will render as unstyled body text without explicit definitions. Define them before the media queries.
10. **`concern-card::after` checkmark: use `display: block`, not `display: flex`.** Pseudo-elements do not support flex. Use `line-height` and `text-align: center` to centre the ✓ character.
11. **`praxio-section .section-title` needs its own mobile font-size rule.** It does not inherit from `.section-title` at 600px without an explicit override.
12. **All touch targets minimum 44px tall.**
13. **No font sizes below 11px on any device.**
14. **No fixed-width elements without `min-width: 0`** on flex children.

### Testing checklist (per report)

- [ ] 320px (smallest common mobile)
- [ ] 390px (iPhone standard)
- [ ] 768px (tablet portrait)
- [ ] 1024px (tablet landscape / small desktop)

---

## 9. Visual Components

The report uses only these components. Do not introduce new ones.

| Content | Component |
|---|---|
| Grade + LCP + TBT | Three widgets (grade + 2 metric cards). Before/After toggle beneath. |
| Core Web Vitals | Arc gauges with current/target toggle. Vitals callout box beneath. |
| Speed impact | Interactive slider pre-set to client TTI. Three live output cards. Conversion bar. |
| Issues | Numbered fix cards with ownership badges. Max four. |
| Homepage observations | Three-card expandable accordion. Colour-coded tags. |
| Concern cards | 2x2 interactive grid. Multi-select. Scroll entrance animation. Dynamic CTA. |
| Progress indicator | Sticky 3px cyan bar at top of viewport. |

### Interactive component rules

**Before/After toggle (scorecard):** Flips grade letter, LCP, TBT, badges, and summary callout. "After" state shows projected scores labelled as projected — never guaranteed.

**Gauge toggle (current vs target):** Default shows actual client scores with colour coding. Toggle flips all three to green with target benchmarks. Pills label as "Target." Callout copy updates. Smooth arc animation on transition.

**Concern cards:** Each carries `data-headline` and `data-body` for CTA personalisation. Multi-select: any combination of cards can be selected simultaneously.
- 0 selected: default CTA copy
- 1 selected: card-specific personalised copy
- 2+ selected: "You have got more than one thing worth unpacking" copy

CTA button pulses (cyan ring animation) on each new selection. Mobile auto-scrolls to button at 2+ selections. Scroll entrance uses IntersectionObserver with staggered delays (0s / 0.1s / 0.2s / 0.3s). Falls back to instant-show on older browsers.

---

## 10. Platform Detection and Copy Rules

### Step 1 — Identify the platform

Preferred: call BuiltWith MCP with client URL before processing GTmetrix data. BuiltWith also returns advertising network tags (Meta Pixel, GTM etc.) useful for fix card specificity.

Fallback — waterfall domain patterns:

| Domain pattern | Platform |
|---|---|
| wp-content, wp-includes, wp-json | WordPress |
| assets.squarespace.com | Squarespace |
| cdn.shopify.com | Shopify |
| static.wixstatic.com | Wix |
| webflow.io, uploads.webflow | Webflow |
| weebly.com, editmysite.com | Weebly |
| No recognisable pattern | Custom-built or unknown — treat as MODE B |

### Step 2 — Apply the correct mode

#### MODE A: WordPress
Full codebase access. Write with confidence. Use "We fix this" badges freely where in scope. No platform caveats needed.

#### MODE B: Non-WordPress
Access varies. Do not imply guaranteed delivery of every fix.

**Mandatory MODE B changes:**
1. Replace "We fix this" with "We can help with this" for platform-dependent fixes.
2. Keep "We fix this" for platform-agnostic fixes (image compression, font reduction, resizing delivered as files).
3. Add a two-sentence platform note in Section 4 before the concern cards.

**Platform note tone:** Confident, not apologetic.
- Do not: "Unfortunately your platform limits what we can do."
- Do: "Because your site runs on [Platform], a quick review confirms the fastest path to improvement."

---

## 11. Praxio Brand and Company Context

**Agency:** Praxio (praxio.com.au / hello@praxio.com.au)
**Parent company:** pointdot — a 20-person performance marketing agency covering web, paid media, and conversion strategy.
**Brand colours:** Navy #002237 / Cyan #00BEED / Indigo #1B1B44
**Typography:** DM Sans (body, headings) + DM Mono (numbers, labels, monospace elements)
**Logo path (SVG):** `M58.5312 0H117V29.2578C117 45.3426 103.83 58.5156 87.75 58.5156H117V117H87.75C71.6695 117 58.5 103.827 58.5 87.7422V117H0V87.7422C0 71.6574 13.1695 58.4844 29.25 58.4844H0V0H29.25C45.393 0 58.5312 13.173 58.5312 29.2578V0Z`

The pointdot backing is a meaningful credibility signal. Name it explicitly in Section 4. It tells the client they are not booking a call with a freelancer — they are accessing a 20-person team across web, paid, and conversion.

---

## 12. Homepage Observation Rules (Section 3)

Three accordion cards in a fixed structure. Do not substitute, add, or reorder.

### Card 1 — Above the Fold
**Tag:** Purple. Label: "Above the Fold."
**Assess:** Visible tappable CTA before the scroll line on mobile. Primary value proposition clear. Hero confirms what the business does and who it is for within 3 seconds.
**Common findings:** Rotating carousels pushing CTAs off screen. Headline below mobile fold. No location signal. Hero answering "what is this?" before "what do I do?"
**Note:** CTA absence and location absence are often the same problem (hero is not doing its job). Combine into one card rather than splitting.

### Card 2 — Trust Signal
**Tag:** Amber. Label: "Trust Signal."
**Assess:** Visible social proof without scrolling. Reviews, ratings, testimonials, client counts.
**Principle:** One line of third-party evidence converts better than three paragraphs of self-description.

### Card 3 — Copywriting (with new headline)
**Tag:** Green. Label: "Copywriting."
**Assess:** Does the headline immediately communicate what the business does, who it is for, and why someone should act?
**Always include a new headline** written specifically for this client. Not a template. Read the site. Write it.

**Display the headline in a dark navy block** visually distinct from the explanatory text. It must look like something worth stealing.

**Location specificity rule:**
- Single location: suburb in headline appropriate and adds local SEO value.
- Multiple locations: headline must be location-neutral. No suburb names on the homepage. Suburb-specific headlines belong on local landing pages.

**Headline format:**
1. Name the product specifically
2. Name who it is for or what outcome it delivers
3. Add a low-friction entry point or offer if one exists

Examples:
- Single: "Reformer Pilates in Surry Hills. Every level. First class on us."
- Multi: "Boutique Reformer Pilates. Every level welcome. First class on us."

**Headline rationale block:** Below the headline, explain why each part earns its place, word by word. This is where the client understands the thinking behind the copy.

### Opportunity copy rules (all three cards)
- Maximum 50 words per opportunity block
- One emoji as visual anchor
- Line breaks between distinct ideas
- Written to be scanned in under 3 seconds on mobile
- Every opportunity names one specific action

### What these cards are not
Not a full CRO audit. Not a design critique. Not a comment on brand or aesthetic. Not a promise of outcomes. Close the section with a footnote: surface observations from a first-visit review.

---

## 13. Closing Section Rules (Section 4)

Section 4 is the ask. It lands immediately after the homepage observations at peak desire. The reader has seen the full picture. Now Praxio opens a broader conversation.

### Headline
Pattern interrupt that reframes from "fixing four problems" to "understanding the full opportunity."
Good: "Most websites are not broken. They are just not working hard enough."
Bad: "What we do about it." (Anchors to the fix list only.)

### Opening paragraph
Acknowledge what the report showed. Then widen the frame immediately. The call is not about the four fixes. It is about where the website sits in the bigger picture of the business.

### Four concern cards
The four most common hesitations before engaging an agency. Title = the client's thought. Body = the honest resolution.

| Card | Emoji | Concern |
|---|---|---|
| Access and control | 🔑 | Who actually owns and controls the site |
| Value for money | 💸 | Whether current spend is working |
| Rebuild vs fix | 🏗️ | Whether a rebuild is worth it or just a big expense |
| Ads and landing pages | 📣 | Ads sending traffic to a homepage never built to convert |

Card body: 2–3 sentences. Not a pitch. An honest acknowledgement that Praxio understands the situation and can give a clear answer on the call.

Cards are interactive: multi-select, scroll-triggered entrance, dynamic CTA personalisation. See Section 9 for technical rules.

### Pointdot backing (one sentence)
"Praxio is backed by pointdot, a 20-person performance marketing agency working across web, paid media, and conversion strategy."

### Pre-CTA close
Centred. Bold. Three sentences maximum. Specific about time (15 minutes), outcome (clear picture of what the site needs and what it costs), friction removed (no pitch deck, no jargon, no obligation).

### CTA button
Text: "Book Your Free 15-Minute Scoping Call"
Sub-text: capability statement, not reassurance copy.
Good: "Web · Paid Media · Conversion Strategy · All under one roof."
Bad: "No lock-in. No jargon." (Reassurance. Replace with capability.)

---

## 14. Pre-Report Checklist

**Step 0 — Platform (do first)**
- [ ] BuiltWith MCP called with client URL, or waterfall patterns used as fallback
- [ ] Platform confirmed
- [ ] MODE A or MODE B confirmed
- [ ] If MODE B: platform note drafted, fix badges reviewed

**Metrics**
- [ ] LCP, TBT, CLS extracted and mapped to Good/Needs Work/Critical
- [ ] TBT converted from ms to seconds (divide by 1000, round to 2 decimal places)
- [ ] Fully Loaded Time excluded from all client copy
- [ ] No Tier 3 metrics in any section
- [ ] Primary headline metric chosen (one only)
- [ ] Speed slider pre-set to client's actual TTI

**Section 2 — Fix list**
- [ ] Each issue has a confirmed cause from the audit panel
- [ ] Correct ownership badge for platform mode
- [ ] Maximum four issues
- [ ] All four-part framework checks pass per issue
- [ ] No copy implies blame toward any agency or third-party provider
- [ ] Third-party script issues use technical, website-level framing only

**Gauges**
- [ ] LCP and TBT values display in seconds
- [ ] Gauge toggle wired: current default, target on toggle, callout updates
- [ ] CLS gauge status correct

**Section 3 — Homepage observations**
- [ ] Live website fetched and reviewed
- [ ] Exactly three accordion cards
- [ ] Each opportunity block under 50 words with emoji and line breaks
- [ ] Copywriting card includes a new headline
- [ ] Multi-location: headline is location-neutral
- [ ] Single-location: suburb used appropriately
- [ ] Headline displayed in dark navy block with rationale
- [ ] Footnote included

**Section 4 — Closing**
- [ ] Pattern-interrupt headline (not "How Praxio Helps")
- [ ] Four concern cards with correct data-headline and data-body attributes
- [ ] Pointdot named with team size
- [ ] Pre-CTA close centred, bold, under three sentences
- [ ] CTA: "Book Your Free 15-Minute Scoping Call"
- [ ] CTA sub-text is a capability statement
- [ ] Section 4 is the last element before the footer

**Copy**
- [ ] No em dashes anywhere in the document
- [ ] Australian English throughout
- [ ] GTmetrix not named in client-facing copy
- [ ] No guaranteed load times or ranking outcomes

**Responsive design**
- [ ] Wrapper max-width 660px with width 100%
- [ ] `section-body` and `vitals-callout` have explicit base CSS
- [ ] `concern-card::after` uses `display: block` not `display: flex`
- [ ] CTA button `width: 100%; box-sizing: border-box` at 600px
- [ ] Accordion tags hidden at 600px
- [ ] Gauge toggle labels scale at 600px and 380px
- [ ] Grade widget full width at 600px
- [ ] Gauge and metric widgets two-column at 600px, full width at 380px
- [ ] `praxio-section .section-title` has its own mobile font-size rule
- [ ] No horizontal scrolling at 320px, 390px, 768px, or 1024px
- [ ] All touch targets minimum 44px
- [ ] No font sizes below 11px
