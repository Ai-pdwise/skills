---
name: design-bible
version: 1.0.0
description: |
  Front-end component library and design system for building HTML documents.
  Use this skill whenever building proposals, reports, briefs, dashboards,
  site architectures, performance summaries, audit documents, or any single-file
  HTML deliverable. This skill tells you WHICH components exist, WHEN to use
  each one, and gives you the exact prompt/pattern to implement them. Trigger
  on any request to build, design, or improve an HTML document, or when the user
  references a specific component by name (e.g. "add a funnel chart", "use
  glassmorphism", "bento grid layout"). Always read this skill before choosing
  components for a document.
allowed-tools:
  - Read
  - Write
  - Edit
  - Grep
  - Glob
  - AskUserQuestion
---

# Front-End Design Bible — Skill Reference

This is the complete component library for building HTML documents. It covers **40+ components** across 5 categories. For every component you will find:

1. **What it is** — a short description
2. **When to use it** — specific document types and scenarios
3. **Brand fit** — which brand tones and industries it suits
4. **Implementation prompt** — the exact pattern to build it
5. **Combination notes** — what it pairs well with

**Read this entire document before selecting components for any HTML build.** Match components to the document's purpose, audience, and brand tone.

---

## How to Use This Skill

When building any HTML document:

1. **Identify the document type** (proposal, report, brief, dashboard, audit, architecture, landing page)
2. **Identify the brand tone** (luxury, corporate, startup/tech, bold/creative, minimal, data-heavy)
3. **Scan the component list below** and select components that match both
4. **Use the implementation prompts** to build each component with the user's specific data
5. **Follow the combination notes** to create cohesive layouts

### Brand Tone Quick Reference

| Tone | Signature Components | Avoid |
|---|---|---|
| **Luxury / Premium** | Glassmorphism, gradient text, animated borders, split sections with large visuals, testimonials | Heatmaps, data tables (too operational), bright callout boxes |
| **Corporate / Enterprise** | Comparison tables, KPI dashboards, data tables, risk matrices, status indicators, step processes | Animated borders, marquee tickers, hover-reveal cards |
| **Startup / Tech** | Bento grids, sparklines, animated counters, tabs, toggle switches, badges | Risk matrices, formal timelines |
| **Bold / Creative** | Hover-reveal cards, funnel charts, gradient text, bento grids, marquee tickers | Plain data tables, corporate comparison tables |
| **Minimal / Clean** | Split sections, feature cards, step processes, progress bars, breadcrumbs | Glassmorphism, animated borders, heatmaps |
| **Data-Heavy / Analytics** | KPI dashboards, sparklines, heatmaps, gauge meters, data tables, funnel charts | Glassmorphism, testimonials, empty states |

---

## Category 1: Data & Metrics

Use these components whenever the document needs to present numbers, performance data, progress, or analytics. These are the backbone of reports, dashboards, and performance summaries.

---

### 1.1 Stat Cards

**What:** A horizontal row of 3-5 cards, each showing a metric label, large value, and directional change indicator.

**When to use:**
- **Monthly/weekly reports** — top of document, summarising key metrics at a glance
- **Proposals** — "Here's where you are now" diagnostic section
- **Executive summaries** — opening dashboard showing headline numbers
- **Case studies** — results section showing before/after metrics
- **Audit documents** — current performance snapshot

**Brand fit:** Universal. Works for every tone. Adjust colors to match brand palette.

**Implementation prompt:**
```
Add a stat cards row showing [NUMBER] key metrics in a horizontal grid. Each
card should have: a colored icon area, an uppercase label, a large bold value,
and a percentage change indicator (green up arrow for positive, red down arrow
for negative). Cards should have subtle gradient backgrounds with decorative
corner accents. Use the metric names: [LIST METRICS]. Values: [LIST VALUES].
Changes: [LIST CHANGES].
```

**Combinations:** Place directly below the document hero/header. Follow with progress bars or sparklines for deeper drill-down. Pair with callout boxes to annotate notable changes.

---

### 1.2 Progress Bars

**What:** Horizontal bars with gradient fills showing completion or performance against a benchmark.

**When to use:**
- **Project status reports** — showing deliverable completion
- **Audit documents** — scoring different areas (SEO, speed, accessibility)
- **Proposals** — "opportunity gap" visualization (current vs potential)
- **Onboarding checklists** — phase completion tracking
- **Campaign reports** — budget pacing, goal attainment

**Brand fit:** Universal. Clean and functional for minimal brands, gradient fills add flair for creative brands.

**Implementation prompt:**
```
Add horizontal progress bars for [NUMBER] metrics. Each bar should have a label
on the left, percentage on the right, and a gradient-filled bar below. Use
different gradient color pairs for each bar to create visual distinction.
Metrics: [LIST ITEMS AND PERCENTAGES].
```

**Combinations:** Stack below stat cards. Pair with circular progress rings for a complementary visual. Use alongside checklist items for project tracking.

---

### 1.3 Circular Progress Rings

**What:** SVG ring charts showing percentage completion with a number centered inside.

**When to use:**
- **Score cards** — page speed, SEO score, accessibility score (like Lighthouse)
- **Goal tracking** — quarterly targets, KPI attainment
- **Audit reports** — grading different performance areas
- **Proposals** — current performance scores to establish baseline
- **Client dashboards** — health check indicators

**Brand fit:** Tech, startup, data-heavy. Slightly less suited to traditional corporate (use gauge meters instead for that tone).

**Implementation prompt:**
```
Add circular progress rings displayed in a horizontal row. Each ring uses an SVG
circle with stroke-dashoffset to show the percentage. Include a large percentage
label centered inside the ring and a descriptive label below. Metrics: [LIST
ITEMS, PERCENTAGES, AND COLORS].
```

**Combinations:** Use in a dedicated "Scores" section. Pair with callout boxes below each ring for interpretation. Works well inside bento grid items.

---

### 1.4 KPI Dashboard Row

**What:** A compact row of 5+ mini metric cards with values and thin performance bars.

**When to use:**
- **PPC/advertising reports** — CTR, CPC, ROAS, Conv. Rate, CPA at a glance
- **Weekly status updates** — compact summary for stakeholders who want density
- **Dashboard-style documents** — when you need more metrics in less vertical space
- **Multi-channel reports** — one KPI row per channel stacked vertically

**Brand fit:** Data-heavy, corporate, startup. Not ideal for luxury (too dense and operational).

**Implementation prompt:**
```
Add a compact KPI dashboard row with [NUMBER] cards side by side. Each card shows
an uppercase metric label, a large colored value, and a thin horizontal bar below
indicating performance vs. benchmark. Use distinct colors per metric. Metrics:
[LIST LABEL, VALUE, BAR WIDTH PERCENT, COLOR].
```

**Combinations:** Stack multiple KPI rows with channel labels for multi-platform reports. Follow with a data table for the detailed breakdown. Precede with stat cards for the headline metrics, then KPI row for the supporting ones.

---

### 1.5 Sparkline Cards

**What:** Metric cards with an inline SVG trend line showing directional movement over time.

**When to use:**
- **Weekly/monthly reports** — showing trend direction alongside the number
- **Executive summaries** — when stakeholders need to see trajectory, not just current value
- **Proposals** — "your current trajectory" section showing declining or flat performance
- **Dashboard headers** — compact trend overview before detailed sections

**Brand fit:** Startup, tech, data-heavy. The inline charts add sophistication that suits modern brands.

**Implementation prompt:**
```
Add sparkline metric cards in a 3-column grid. Each card shows: a metric label,
a directional change indicator (up/down arrow with color), a large bold value,
and an SVG sparkline chart below showing the trend over time. Use a polyline for
the stroke and a filled path area beneath it with low opacity. Metrics: [LIST
LABEL, VALUE, TREND DIRECTION, COLOR].
```

**Combinations:** Use instead of stat cards when trend direction matters more than the absolute number. Follow with data table for granular breakdown.

---

### 1.6 Gauge Meters

**What:** Semi-circular SVG arc gauges showing a score on a scale.

**When to use:**
- **Site audit reports** — Lighthouse-style scoring (Speed, SEO, Accessibility, Best Practices)
- **Health check documents** — account health, campaign health scoring
- **Proposals** — current state diagnosis with visual scoring
- **GTmetrix/performance reports** — page performance metrics

**Brand fit:** Corporate, data-heavy, audit-focused. More traditional than circular progress rings — better for enterprise clients.

**Implementation prompt:**
```
Add semi-circular gauge meters in a horizontal row. Each gauge uses an SVG arc
path with stroke-dasharray/dashoffset to show the fill level. Display a large
percentage value centered below the arc, and a label beneath that. Use different
colors per gauge to indicate severity (green = good, orange = warning, red =
critical). Metrics: [LIST LABEL, VALUE, COLOR].
```

**Combinations:** Place in an "Account Health" or "Performance Scores" section. Follow with callout boxes explaining what each score means and recommended actions. Pair with before/after panels for improvement context.

---

### 1.7 Funnel Chart

**What:** Vertically stacked bars of decreasing width showing conversion flow.

**When to use:**
- **Marketing reports** — impression > click > lead > customer conversion flow
- **Sales proposals** — showing the prospect's current funnel drop-off
- **E-commerce reports** — browse > cart > checkout > purchase flow
- **Campaign analysis** — showing where in the funnel performance breaks down
- **Strategy documents** — illustrating the full-funnel approach

**Brand fit:** Bold/creative, startup, data-heavy. The visual tapering makes it engaging for non-technical stakeholders.

**Implementation prompt:**
```
Add a CSS funnel chart with [NUMBER] stages stacked vertically, each narrower
than the one above to create a visual funnel shape. Each stage has a gradient
background, a label on the left, and a large bold value on the right. Stages:
[LIST STAGE NAME, VALUE, WIDTH PERCENTAGE, GRADIENT COLORS].
```

**Combinations:** Place in a "Conversion Analysis" or "Full-Funnel Strategy" section. Follow with callout boxes for each stage noting optimization opportunities. Precede with stat cards showing overall conversion rate.

---

### 1.8 Heatmap Grid

**What:** A grid of cells with color intensity indicating value, typically time vs. day.

**When to use:**
- **Ad scheduling reports** — showing best-performing hours/days for ad delivery
- **Website analytics** — when users are most active
- **Social media audits** — optimal posting times
- **Email marketing reports** — best send times by day
- **Resource planning documents** — peak demand visualization

**Brand fit:** Data-heavy, analytics-focused. Too technical for luxury or minimal brand tones.

**Implementation prompt:**
```
Add a heatmap grid with [ROWS] time slots as rows and [COLUMNS] days as columns.
Each cell uses background opacity to indicate intensity (low opacity = low value,
high opacity = high value, white text on dark cells). Include row labels on the
left and column headers on top. Cell values should be numeric. Use a single hue
with varying opacity for the heat scale. Data: [PROVIDE GRID DATA].
```

**Combinations:** Place in a "Performance by Time" or "Scheduling Insights" section. Follow with a recommendation callout box suggesting optimal scheduling.

---

### 1.9 Animated Counters

**What:** Large numbers that count up from zero to their target using IntersectionObserver + requestAnimationFrame.

**When to use:**
- **Proposals** — hero section or results section for dramatic impact
- **Case studies** — key results that need to feel impressive
- **About/capabilities sections** — "clients served", "ad spend managed" type stats
- **Annual reviews** — year in numbers
- **Landing page-style documents** — social proof metrics

**Brand fit:** Startup, bold/creative, luxury (when used sparingly for one or two hero numbers). Avoid for formal corporate reports.

**Implementation prompt:**
```
Add animated counter stats that count up from 0 to their target value when they
scroll into view using IntersectionObserver. Display as large bold colored numbers
with a descriptive label below. Support prefixes ($) and suffixes (%, M+, K).
Counters: [LIST LABEL, TARGET VALUE, PREFIX/SUFFIX, COLOR].
```

**Combinations:** Use in a hero section or dedicated "Impact" section. Pair with split section for text context alongside the numbers. Follow with testimonials for social proof reinforcement.

---

### 1.10 Data Table

**What:** A styled table with headers, sortable-looking columns, inline status badges, and hover-highlighted rows.

**When to use:**
- **Campaign reports** — campaign-by-campaign performance breakdown
- **Audit documents** — itemized findings with status/priority
- **Competitor analysis** — side-by-side competitor data
- **Proposals** — deliverables and timeline table
- **SEO reports** — keyword rankings table

**Brand fit:** Corporate, data-heavy, minimal. The structure communicates professionalism and thoroughness.

**Implementation prompt:**
```
Add a styled data table with [NUMBER] columns and [NUMBER] rows. Headers should
be uppercase with muted styling. Include inline colored status badges
(Active=green, Paused=yellow, Ended=red). Key performance values should be
color-coded (green for strong, orange for moderate, red for poor). Rows should
have hover highlighting. Columns: [LIST COLUMNS]. Data: [PROVIDE ROW DATA].
```

**Combinations:** Place after KPI dashboard or stat cards that provide the summary view. Follow with callout boxes highlighting key findings from the data. Use tabs to organize multiple tables by channel/category.

---

## Category 2: Content & Layout

Use these components for structuring information, making comparisons, presenting features, pricing, and creating visual hierarchy.

---

### 2.1 Feature Comparison Table

**What:** A multi-column table comparing features across tiers/options with checkmarks and crosses.

**When to use:**
- **Proposals** — comparing your service tiers
- **Competitor analysis** — feature comparison vs. alternatives
- **Product pages** — plan comparison
- **Strategy documents** — comparing strategic options with trade-offs
- **Migration documents** — current platform vs. recommended platform

**Brand fit:** Corporate, minimal, startup. The highlighted column technique draws attention to the recommended option.

**Implementation prompt:**
```
Add a feature comparison table with [NUMBER] tiers as columns and [NUMBER]
features as rows. Highlight the recommended tier column with a subtle accent
background. Use green checkmarks for included features, red crosses for excluded
ones, and text for partial features. Include a header row with tier names.
Features: [LIST FEATURES]. Tiers: [LIST TIERS AND VALUES].
```

**Combinations:** Follow with a pricing table to anchor the comparison to cost. Precede with a split section introducing the comparison context.

---

### 2.2 Split Content Section

**What:** A two-column layout with text on one side and a visual/image on the other.

**When to use:**
- **Proposals** — introducing your approach, methodology, or unique value prop
- **About sections** — team introduction or agency overview
- **Case studies** — narrative + visual side by side
- **Landing page-style documents** — feature sections alternating left/right
- **Strategy documents** — each strategic pillar with visual illustration

**Brand fit:** Universal. Luxury brands use it with more whitespace and larger visuals. Tech brands use it with screenshots or illustrations.

**Implementation prompt:**
```
Add a split content section with two columns: text on one side and a visual/image
placeholder on the other. The text side includes: a small colored tag/badge at
the top, a large bold heading, a paragraph of body text, and a CTA button. The
visual side should have a rounded container with a gradient background and
centered icon or image. Use a 50/50 grid layout with centered vertical alignment.
```

**Combinations:** Alternate left-right alignment for consecutive split sections. Follow with feature cards for supporting detail. Precede with gradient text hero.

---

### 2.3 Bento Grid Layout

**What:** An asymmetric CSS grid with items spanning different numbers of rows and columns.

**When to use:**
- **Proposals** — services overview showing breadth of capabilities
- **Feature showcases** — when you have 5-8 features of varying importance
- **Capabilities sections** — agency/product capabilities with visual hierarchy
- **Site architecture documents** — showing content categories and their relative weight
- **Dashboard layouts** — mixing different content types in one view

**Brand fit:** Startup, tech, bold/creative. The asymmetry feels modern and premium. Avoid for traditional corporate unless the client is innovation-focused.

**Implementation prompt:**
```
Add a bento grid layout with [NUMBER] items in an asymmetric grid. Some items
span 2 columns, some span 2 rows, creating visual variety. Each item has an
emoji/icon, a bold title, and a short description. Use subtle gradient backgrounds
with distinct hues per item. The grid should use CSS Grid with named column/row
spans. Items: [LIST ICON, TITLE, DESCRIPTION, SPAN TYPE].
```

**Combinations:** Use as a "What We Do" or "Services" section. Follow with individual feature cards or split sections for deeper exploration of key items.

---

### 2.4 Feature Cards

**What:** A grid of cards each with an icon, title, and description. Hover effect reveals a colored top border.

**When to use:**
- **Proposals** — listing included services or deliverables
- **Capabilities sections** — what you offer
- **Strategy documents** — strategic pillars or focus areas
- **Audit reports** — areas of analysis
- **Onboarding documents** — what the client gets

**Brand fit:** Universal. The hover effects add dynamism for tech/startup brands. Remove hover for more corporate tones.

**Implementation prompt:**
```
Add a feature cards grid with [NUMBER] cards in a row. Each card has: an icon in
a rounded square background, a bold title, and a descriptive paragraph. Cards
should have a hover effect that lifts the card slightly and reveals a colored
gradient top border. Use consistent spacing and a bordered card style. Features:
[LIST ICON, TITLE, DESCRIPTION].
```

**Combinations:** Place after a split section introduction. Follow with a pricing table or timeline. Pair with the step process to show how these features are delivered.

---

### 2.5 Testimonial Cards

**What:** Quote cards with testimonial text, author avatar (initials), name, and role.

**When to use:**
- **Proposals** — social proof section, especially before the pricing section
- **Case studies** — client voice validating the results
- **About/capabilities documents** — trust-building section
- **Landing page-style documents** — social proof block

**Brand fit:** Luxury, corporate, minimal. The initials-avatar approach is elegant and doesn't require actual photos. Suits all tones except data-heavy analytics reports.

**Implementation prompt:**
```
Add a testimonial cards section with [NUMBER] cards in a grid. Each card includes:
a large decorative opening quotation mark, italic testimonial text, and an author
section with a colored circular avatar showing initials, the person's name in
bold, and their role/company below. Use bordered card styling. Testimonials:
[LIST QUOTE, NAME, ROLE, INITIALS, AVATAR COLOR].
```

**Combinations:** Place before pricing section in proposals (builds trust before asking for commitment). Follow with animated counters for reinforcement. Pair with a CTA split section.

---

### 2.6 Pricing Table

**What:** Side-by-side pricing cards with tier names, prices, feature lists, and CTAs. One card is visually featured.

**When to use:**
- **Proposals** — investment section (the most critical section)
- **Service pages** — tier comparison
- **Upsell documents** — showing what the next tier unlocks
- **Renewal proposals** — comparing current plan vs. upgraded plan

**Brand fit:** Universal. Luxury uses gold accents and "Investment" language. Corporate uses clean borders. Startup uses vibrant featured card.

**Implementation prompt:**
```
Add a pricing table with [NUMBER] tiers in a horizontal grid. Each card includes:
tier name (uppercase), large price with period suffix, short description, a
feature checklist with green checks and red crosses, and a CTA button. The
recommended tier should have: a "Most Popular" badge above it, an accent border,
a gradient background, and a filled CTA button. Other tiers use outlined buttons.
Tiers: [LIST TIER NAME, PRICE, DESCRIPTION, FEATURES WITH CHECK/CROSS].
```

**Combinations:** Precede with testimonials for trust. Follow with a FAQ accordion to handle objections. Place comparison table above if there are many features to compare.

---

### 2.7 Before / After Comparison

**What:** Two side-by-side panels showing the "before" state (red-tinted) and "after" state (green-tinted).

**When to use:**
- **Case studies** — the transformation story
- **Audit reports** — current state vs. recommended state
- **Proposals** — "where you are vs. where you could be"
- **Optimization reports** — what changed and what improved
- **Campaign restructure reports** — old structure vs. new structure

**Brand fit:** Universal. Especially powerful for proposals and case studies across all brand tones.

**Implementation prompt:**
```
Add a before/after comparison with two side-by-side panels. The "Before" panel
has a red-tinted header with a cross icon. The "After" panel has a green-tinted
header with a check icon. Each panel contains descriptive body text explaining
the state. Use bordered card styling with matching colored headers. Before text:
[TEXT]. After text: [TEXT].
```

**Combinations:** Place in a "Transformation" or "What Changed" section. Follow with stat cards showing the numerical impact. Precede with a timeline showing the journey.

---

### 2.8 Callout / Alert Boxes

**What:** Colored notification boxes with left border, icon, and message text. Four types: info (blue), success (green), warning (orange), error (red).

**When to use:**
- **Reports** — annotating data with context ("Note: this period includes a sale event")
- **Audit documents** — flagging critical issues vs. informational notes
- **Strategy documents** — highlighting risks and opportunities
- **Proposals** — drawing attention to key points or time-sensitive offers
- **Technical documents** — warnings, prerequisites, or success confirmations

**Brand fit:** Universal. Essential for any document that needs to draw attention to specific information.

**Implementation prompt:**
```
Add callout boxes in one or more of these types: info (blue), success (green),
warning (orange), error (red). Each callout has a colored left border, a tinted
background, a circular icon, bold label text, and the message body. Use the
appropriate type for the message severity. Messages: [LIST TYPE AND MESSAGE TEXT].
```

**Combinations:** Insert anywhere context is needed. Place after data tables to highlight key findings. Use within timeline items for milestone-specific notes. Pair with stat cards to annotate significant changes.

---

### 2.9 Gradient Text Hero

**What:** Large heading text with a multi-color gradient applied via background-clip.

**When to use:**
- **Document hero sections** — the opening headline
- **Section dividers** — creating visual impact between major sections
- **Case study headlines** — dramatic result statements
- **Proposal cover pages** — the key value proposition line

**Brand fit:** Luxury, startup, bold/creative. Avoid for conservative corporate (use solid colors instead). The effect is premium and attention-grabbing.

**Implementation prompt:**
```
Add a gradient text heading using background-clip: text with
-webkit-text-fill-color: transparent. The gradient should flow across the text
from [COLOR 1] through [COLOR 2] to [COLOR 3] at 135 degrees. Include a muted
subtitle below. Use a large, heavy font weight (700-800) for maximum impact.
Heading: [TEXT]. Subtitle: [TEXT].
```

**Combinations:** Use as the document opener. Follow with stat cards or animated counters. Place at the start of major sections for dramatic separation.

---

### 2.10 Empty State

**What:** A centered placeholder shown when there is no data, with icon, title, description, and CTA.

**When to use:**
- **Dashboard documents** — placeholder for sections awaiting data
- **Onboarding documents** — "get started" prompts
- **Product documentation** — first-use state illustration
- **Report templates** — showing what will appear once data flows in

**Brand fit:** Startup, tech. Less common in proposals or formal reports.

**Implementation prompt:**
```
Add an empty state placeholder for when there is no data to display. Center a
large faded icon/emoji, a bold title explaining the empty state, a muted
descriptive paragraph, and a primary CTA button. Use generous padding and
center-aligned text. Icon: [EMOJI]. Title: [TEXT]. Description: [TEXT].
Button: [TEXT].
```

**Combinations:** Rarely combined with other components — it replaces them when data is absent.

---

## Category 3: Interactive Components

Use these for documents that benefit from user interaction: expanding content, switching views, toggling options, and revealing information on demand.

---

### 3.1 Accordion / Expandable Sections

**What:** Collapsible content panels triggered by clicking a question/header row.

**When to use:**
- **Proposals** — FAQ section addressing common objections
- **Documentation** — long-form content that should be scannable
- **Audit reports** — detailed findings that can be expanded per issue
- **Onboarding documents** — step-by-step guides with expandable detail
- **Strategy documents** — methodology details that support but don't crowd the narrative

**Brand fit:** Universal. Essential for any document longer than 3 scroll-heights.

**Implementation prompt:**
```
Add an accordion/FAQ section with [NUMBER] expandable items. Each item has a
clickable trigger with the question text and a rotating arrow indicator. When
clicked, the content panel expands with a smooth max-height CSS transition. Only
one item should be open by default. Use onclick to toggle an 'open' class. Items:
[LIST QUESTION AND ANSWER].
```

**Combinations:** Place after pricing table in proposals. Use within split sections for methodology details. Pair with callout boxes inside accordion content for emphasis.

---

### 3.2 Tab Panels

**What:** Horizontal tab navigation that switches between content panels.

**When to use:**
- **Reports** — organizing data by channel, time period, or category
- **Proposals** — showing different service options or phases
- **Case studies** — Overview / Strategy / Results / Next Steps narrative
- **Multi-channel reports** — one tab per platform (Google, Meta, LinkedIn)
- **Strategy documents** — organizing by strategic pillar

**Brand fit:** Startup, tech, corporate. Excellent for managing information density without visual clutter.

**Implementation prompt:**
```
Add a tabbed content panel with [NUMBER] tabs. The tab navigation should be
styled as pill-shaped buttons inside a rounded container bar. The active tab gets
a solid colored background. Tab content panels show/hide when tabs are clicked
using a JavaScript switchTab function that toggles 'active' class. Tabs: [LIST
TAB NAMES AND CONTENT].
```

**Combinations:** Use as a structural container for data tables, stat cards, or KPI rows — each tab showing a different view. Place within split sections for compact information architecture.

---

### 3.3 Hover-Reveal Cards

**What:** Cards with a visible summary that reveal detailed text on hover via a colored overlay.

**When to use:**
- **Proposals** — industry expertise or service verticals
- **Capabilities sections** — teasing depth without overwhelming
- **Case study collections** — hover to see the key result
- **Team pages** — hover to see bio/expertise
- **Service pages** — compact presentation of offerings

**Brand fit:** Bold/creative, startup, luxury. The interaction feels premium and engaging. Avoid for data-heavy documents where hover isn't expected.

**Implementation prompt:**
```
Add hover-reveal cards in a grid. Each card has a gradient image area, a title,
and description visible by default. On hover, a colored overlay slides in
(opacity transition from 0 to 1) showing detailed text. The overlay covers the
entire card with centered text. Cards: [LIST TITLE, DESCRIPTION, HOVER TEXT,
GRADIENT COLORS].
```

**Combinations:** Use in a "Our Expertise" or "Industries We Serve" section. Follow with testimonials from clients in those industries. Precede with a gradient text heading.

---

### 3.4 Modal Dialog

**What:** A centered popup box with title, message, and action buttons, triggered by a button click.

**When to use:**
- **Interactive dashboards** — confirmation dialogs for actions
- **Proposals** — "Book a Call" or "Accept Proposal" CTA that opens a form
- **Tools/calculators** — displaying detailed results
- **Documents with decisions** — presenting options that need confirmation

**Brand fit:** Tech, startup. Less common in static reports or formal proposals unless there's a specific interactive CTA.

**Implementation prompt:**
```
Add a modal dialog component. Include a trigger button that adds a 'visible'
class to the overlay. The overlay uses a dark semi-transparent background with
backdrop-filter blur. The modal box is centered, with a close button (top-right
X), a title, body text, and a row of action buttons (secondary outlined + primary
filled). Clicking the overlay background also closes the modal. Scale transform
for entrance animation. Title: [TEXT]. Body: [TEXT]. Buttons: [LABELS].
```

**Combinations:** Trigger from CTA buttons in pricing sections, hero sections, or callout boxes. Can contain a form, calendar embed, or detailed information.

---

### 3.5 Toggle Switches

**What:** Sliding on/off switches in a settings-style list.

**When to use:**
- **Proposals** — optional add-on services the client can mentally "switch on"
- **Configuration documents** — feature flags or settings explanations
- **Onboarding documents** — preference selection
- **Interactive dashboards** — filter controls

**Brand fit:** Tech, startup. The interaction pattern is familiar from app interfaces.

**Implementation prompt:**
```
Add toggle switch controls in a vertical list. Each row has a label on the left
and a sliding toggle on the right. The toggle is a rounded pill shape with a
circular knob that slides left/right via CSS transform when an 'on' class is
toggled onclick. Active state uses green background. Items: [LIST LABEL AND
DEFAULT STATE].
```

**Combinations:** Use within tab panels for settings-style views. Pair with pricing table where toggles control optional line items.

---

### 3.6 Interactive Checklist

**What:** Clickable checkbox rows that toggle between checked (green, strikethrough) and unchecked states.

**When to use:**
- **Proposals** — scope/deliverables checklist
- **Onboarding documents** — setup tasks
- **Project kickoff documents** — prerequisites checklist
- **Audit reports** — remediation checklist
- **Strategy documents** — action items

**Brand fit:** Universal. The interactivity adds engagement to what would otherwise be a static bullet list.

**Implementation prompt:**
```
Add an interactive checklist with [NUMBER] items. Each item is a clickable row
that toggles a 'checked' class. Checked items show a green checkbox with
checkmark and strike-through text with reduced opacity. Unchecked items show an
empty bordered checkbox. Use onclick to toggle. Items: [LIST ITEMS AND DEFAULT
CHECKED STATE].
```

**Combinations:** Place in a "Deliverables" or "Next Steps" section. Precede with a timeline showing the broader project plan. Follow with a CTA to kick off the work.

---

### 3.7 Tooltips

**What:** Small popup labels that appear on hover, explaining jargon or abbreviations.

**When to use:**
- **Reports** — defining metric abbreviations (CTR, CPA, ROAS)
- **Technical documents** — explaining terms without breaking reading flow
- **Proposals** — clarifying industry terminology for non-technical clients
- **Audit reports** — defining scoring criteria

**Brand fit:** Universal. A UX best practice for any document with specialist terminology.

**Implementation prompt:**
```
Add tooltips that appear on hover. Each trigger element has a relatively-positioned
container with an absolutely-positioned tooltip above it. The tooltip uses opacity
transition, a contrasting background color, and a CSS triangle arrow created with
border tricks pointing downward. Tooltip content: [LIST TRIGGER TEXT AND TOOLTIP
TEXT].
```

**Combinations:** Use inline within data tables, KPI rows, or stat cards. Apply to any metric abbreviation throughout the document.

---

### 3.8 Search Bar

**What:** A styled input field with a search icon and placeholder text.

**When to use:**
- **Documentation** — navigating large reference documents
- **Dashboards** — filtering campaigns, keywords, or data
- **Knowledge bases** — content search interface
- **Site architecture documents** — illustrating the search UX

**Brand fit:** Tech, startup. Functional rather than decorative.

**Implementation prompt:**
```
Add a search bar with a left-aligned search icon (emoji or SVG), a large input
field with placeholder text, and a focus state that highlights the border with an
accent color. Use padding-left on the input to make room for the icon. Style:
rounded corners, dark background, subtle border. Placeholder: [TEXT].
```

**Combinations:** Place at the top of data-heavy sections. Pair with data tables that the search would conceptually filter.

---

## Category 4: Navigation & Flow

Use these components to guide users through processes, timelines, hierarchies, and states.

---

### 4.1 Timeline / Roadmap

**What:** A vertical line with milestone cards branching off, showing project phases.

**When to use:**
- **Proposals** — project plan / engagement timeline
- **Strategy documents** — strategic roadmap with phases
- **Onboarding documents** — what happens when
- **Project reports** — progress tracking against milestones
- **Case studies** — the journey from start to results

**Brand fit:** Universal. One of the most essential components for any document that involves a sequence of work.

**Implementation prompt:**
```
Add a vertical timeline/roadmap with [NUMBER] milestones. Use a gradient vertical
line on the left with circular dot markers at each milestone. Each milestone card
has a date label (accent color), bold title, and description. Use different dot
styles: completed (accent color), active (green with glow shadow), and future
(muted). Cards are bordered with rounded corners. Milestones: [LIST DATE, TITLE,
DESCRIPTION, STATUS].
```

**Combinations:** Precede with a step process for the high-level overview, then timeline for detailed breakdown. Follow with a checklist for immediate next steps. Pair with pricing table to connect timeline to investment.

---

### 4.2 Step Process Flow

**What:** A horizontal numbered sequence showing stages connected by lines.

**When to use:**
- **Proposals** — "How We Work" or "Our Process" section
- **Onboarding documents** — the engagement lifecycle
- **Strategy documents** — the strategic framework overview
- **Sales documents** — the buyer's journey visualization
- **Site architecture documents** — user flow stages

**Brand fit:** Universal. Clean and immediately understandable. Use numbered circles for corporate, colored circles for creative.

**Implementation prompt:**
```
Add a horizontal step process flow with [NUMBER] numbered steps. Each step has a
colored circle with the step number, a bold title, and a short description.
Connect steps with a horizontal line between the circles using a ::after
pseudo-element. Use different colors per step for visual progression. Steps: [LIST
STEP NUMBER, TITLE, DESCRIPTION, COLOR].
```

**Combinations:** Use as a high-level overview before a detailed timeline. Place in the methodology section of proposals. Follow with feature cards that detail what happens at each step.

---

### 4.3 Breadcrumbs

**What:** A horizontal navigation trail showing page hierarchy.

**When to use:**
- **Site architecture documents** — showing URL/page hierarchy examples
- **Multi-page documents** — navigation context
- **Dashboard mockups** — location indicator
- **Documentation** — section context

**Brand fit:** Minimal, corporate, tech. Functional navigation element.

**Implementation prompt:**
```
Add a breadcrumb navigation trail showing the page hierarchy. Links are muted
colored and separated by "/" dividers. The current/last item is bold and uses the
primary text color. The component has a subtle background container with rounded
corners. Path: [LIST BREADCRUMB ITEMS, LAST IS CURRENT].
```

**Combinations:** Place at the top of site architecture diagrams. Use within mockups or wireframe-style sections.

---

### 4.4 Status Indicators

**What:** A vertical list of items with colored status dots and labels.

**When to use:**
- **Campaign reports** — platform/campaign status overview
- **Audit reports** — system health check results
- **Project status documents** — deliverable status tracking
- **Technical documents** — service/integration status
- **Monitoring dashboards** — uptime and health indicators

**Brand fit:** Corporate, data-heavy, tech. Professional and functional.

**Implementation prompt:**
```
Add a status indicator list with [NUMBER] items. Each row has a small colored dot
(green with pulse animation for live, orange for warning, red for error, gray for
offline), a label, and a status text aligned to the right. Rows are stacked in
bordered cards. Items: [LIST LABEL, STATUS TYPE, STATUS TEXT].
```

**Combinations:** Place in a "System Health" or "Platform Status" section. Follow with callout boxes for any items in warning or error state. Pair with data table for detailed breakdown.

---

### 4.5 Badge / Tag System

**What:** Small colored pills used to categorize, label, or indicate status inline.

**When to use:**
- **Everywhere** — used inline within other components to add categorical context
- **Data tables** — status badges in table cells
- **Card layouts** — category tags on cards
- **Reports** — priority or channel labels
- **Task lists** — status and priority indicators

**Brand fit:** Universal. An essential micro-component.

**Implementation prompt:**
```
Add styled badge/tag components using pill-shaped spans. Two variants: (1) with a
small colored dot indicator before the text, (2) text-only. Each badge has a
tinted background matching the text color at low opacity. Use inline-flex for
alignment. Badges: [LIST LABEL, COLOR, AND WHETHER TO INCLUDE DOT].
```

**Combinations:** Insert into data table cells, card headers, timeline items, stat cards, or any component needing categorical context.

---

### 4.6 Avatar Group

**What:** Overlapping circular avatars showing team members with a "+N" overflow indicator.

**When to use:**
- **Proposals** — "Your Team" section showing who will work on the account
- **Project documents** — team assignment visualization
- **Task/project cards** — showing assigned people
- **About sections** — team overview

**Brand fit:** Startup, corporate, minimal. The initials-avatar approach is professional without requiring photos.

**Implementation prompt:**
```
Add an avatar group showing overlapping circular avatars. Each avatar shows
initials on a colored background with a dark border for separation. Avatars
overlap with negative margin-left. Include a "+N" overflow avatar at the end if
there are more people than shown. Optionally add a text label to the right.
People: [LIST INITIALS, COLOR]. Overflow: [NUMBER].
```

**Combinations:** Place in a "Your Team" section in proposals. Use inside project cards or timeline items to show who's responsible for each phase.

---

### 4.7 Marquee / Logo Ticker

**What:** An infinitely scrolling horizontal strip of logos or brand names.

**When to use:**
- **Proposals** — "Platforms We Manage" or "Tools We Use" ticker
- **Case studies** — "Trusted by" client logo strip
- **About sections** — technology stack or partner logos
- **Landing page-style documents** — social proof/credibility strip

**Brand fit:** Startup, bold/creative. The animation adds energy. Avoid for conservative corporate — use a static logo grid instead.

**Implementation prompt:**
```
Add an infinite scrolling marquee/ticker showing logos or brand names. The items
are duplicated inside a flex container with a CSS translateX animation that moves
from 0 to -50%. The wrapper uses overflow:hidden to create the seamless loop
effect. Each item has a small icon box and text label. Items: [LIST ICON LETTER
AND BRAND NAME].
```

**Combinations:** Place between major sections as a visual break. Use after the hero section for immediate credibility. Precede testimonials for a trust-building sequence.

---

## Category 5: Visual Effects

Premium visual treatments that elevate design quality. Use deliberately — a few effects create sophistication; too many create chaos.

---

### 5.1 Glassmorphism Card

**What:** A frosted-glass card floating over colorful blurred background orbs.

**When to use:**
- **Luxury brand proposals** — hero section or feature highlight
- **Premium product showcases** — when the content needs to feel exclusive
- **Startup pitch documents** — creating a modern, polished aesthetic
- **CTA sections** — making the call-to-action feel premium
- **Cover pages** — creating an atmospheric opening

**Brand fit:** Luxury, premium startup. The frosted glass effect signals sophistication. Do NOT use for data-heavy reports, audits, or operational documents.

**Implementation prompt:**
```
Add a glassmorphism card effect. Create a container with a dark gradient
background and 2-3 colored blurred orbs (divs with border-radius:50%,
filter:blur(40px), and low opacity). Place a card on top using
backdrop-filter:blur(20px), rgba background with low alpha, and a subtle white
border. Include a title, description text, and a translucent button. Title:
[TEXT]. Description: [TEXT]. Button: [TEXT].
```

**Combinations:** Use as the document hero or a standalone CTA section. Do NOT combine with data-heavy components in the same section — the aesthetic clash hurts both.

---

### 5.2 Animated Border Card

**What:** A card with a continuously spinning conic-gradient border creating a shimmering edge effect.

**When to use:**
- **Proposals** — featured recommendation or key takeaway
- **Reports** — most important finding or action item
- **Strategy documents** — the primary recommendation
- **Case studies** — the hero result
- **Any document** — when one piece of content needs to visually dominate

**Brand fit:** Luxury, startup, bold/creative. Use exactly once per document for maximum impact. Multiple animated borders dilute the effect.

**Implementation prompt:**
```
Add a card with a spinning animated gradient border. Use a conic-gradient on a
::before pseudo-element with animation: rotate 4s linear infinite. Place a ::after
pseudo-element with the card background on top (z-index:-1) with slightly smaller
inset to reveal the spinning border. The card content sits above both. Title:
[TEXT]. Body: [TEXT].
```

**Combinations:** Use for THE single most important card in the document. Place in the recommendations section of an audit, or the key result of a case study. Follow with supporting evidence (stat cards, data tables).

---

### 5.3 Notification Toasts

**What:** Stacked notification-style cards with colored icons indicating message type.

**When to use:**
- **Reports** — key alerts and notifications about account changes
- **Audit reports** — prioritized findings presented as notifications
- **Monitoring documents** — recent alerts or triggered rules
- **Dashboard mockups** — showing the notification experience
- **Proposals** — "alerts you'll receive" in a monitoring service pitch

**Brand fit:** Tech, startup, data-heavy. The notification metaphor is familiar from apps and dashboards.

**Implementation prompt:**
```
Add notification toast components stacked vertically. Each toast has a colored icon
(success=green check, warning=orange triangle, error=red exclamation), a bold
title, and a description message. Toasts slide in from the right with a CSS
animation using translateX. Use box-shadow for depth and rounded card styling.
Toasts: [LIST TYPE, TITLE, MESSAGE].
```

**Combinations:** Use in a "Recent Alerts" or "Key Findings" section. Follow with a data table or status indicators for the detailed view. Precede with KPI dashboard to provide context.

---

### 5.4 Risk / Priority Matrix

**What:** A 3x3 (or larger) colored grid showing risk/priority by two dimensions (e.g., Impact vs. Likelihood).

**When to use:**
- **Strategy documents** — prioritizing initiatives or opportunities
- **Audit reports** — categorizing findings by severity and effort
- **Project planning** — risk assessment
- **Proposals** — prioritizing recommended actions
- **Security/compliance documents** — threat assessment

**Brand fit:** Corporate, data-heavy. The matrix format communicates analytical rigor. Well-suited to enterprise clients.

**Implementation prompt:**
```
Add a risk/priority matrix as a CSS Grid with [ROWS]x[COLS] cells. The Y-axis
label is rotated vertically. Each cell is color-coded by severity: green for low
risk, yellow for medium, orange for high, red for critical. Include axis labels at
the bottom and left. Cell labels indicate the risk level. Use border-radius on
cells with hover scale effect. Axes: [Y-AXIS LABEL] vs [X-AXIS LABEL]. Cell data:
[PROVIDE GRID DATA].
```

**Combinations:** Place in a "Risk Assessment" or "Priority Matrix" section. Follow with an action-item checklist or data table listing each item and its matrix position. Precede with callout box explaining the methodology.

---

## Document Type Quick-Start Recipes

These recipes suggest a component stack for common document types. Adjust based on brand tone using the Brand Tone Quick Reference at the top.

### Client Proposal
1. Gradient text hero (or glassmorphism hero for luxury)
2. Stat cards — current performance diagnosis
3. Before/after — the opportunity
4. Step process — how we work
5. Feature cards — included services
6. Timeline — the engagement plan
7. Pricing table — investment
8. Testimonials — social proof
9. Accordion — FAQ
10. CTA split section — next steps

### Monthly Performance Report
1. Stat cards — headline metrics
2. KPI dashboard row — supporting metrics
3. Sparkline cards — trends
4. Data table — campaign-level breakdown
5. Funnel chart — conversion flow
6. Heatmap — performance by time
7. Before/after — month-over-month changes
8. Callout boxes — key findings and alerts
9. Checklist — recommended actions

### Audit Document
1. Gauge meters — overall scores
2. Progress bars — category scores
3. Risk matrix — findings by priority
4. Data table — itemized findings
5. Status indicators — system health
6. Callout boxes — critical issues, warnings, info
7. Before/after — current state vs. recommended
8. Timeline — remediation roadmap
9. Checklist — action items

### Case Study
1. Gradient text hero — the headline result
2. Animated counters — the key numbers
3. Split section — the challenge
4. Timeline — the journey
5. Before/after — the transformation
6. Stat cards — the results
7. Testimonial — client voice
8. CTA split section — "want similar results?"

### Site Architecture Document
1. Breadcrumbs — hierarchy examples
2. Bento grid — content categories
3. Step process — user journey flow
4. Feature cards — page types and purposes
5. Data table — URL mapping
6. Comparison table — current vs. proposed structure
7. Checklist — migration tasks

### Strategy / Brief
1. Split section — strategic context
2. Bento grid — strategic pillars
3. Tab panels — detailed pillar breakdowns
4. Funnel chart — full-funnel strategy visualization
5. Timeline — execution roadmap
6. Risk matrix — opportunity prioritization
7. Feature cards — tactical recommendations
8. Checklist — action items

---

## Design Principles

When choosing and combining components:

1. **Hierarchy first.** Lead with the most important information. Stat cards and gradient text heroes go at the top. Detail components (tables, accordions) go deeper.

2. **One effect per section.** Don't combine glassmorphism + animated borders + gradient text in one view. Pick one visual effect and let it breathe.

3. **Data → Context → Action.** Show the number (stat cards/KPIs), explain what it means (callout boxes/split sections), then tell them what to do (checklists/CTAs).

4. **Interaction with purpose.** Don't add tabs just because they exist. Use them when content genuinely benefits from being organized into switchable views. Same for accordions — only when content is too long to display fully.

5. **Color consistency.** Pick 3-4 accent colors and use them consistently: one for primary actions, one for success/positive, one for warnings, one for errors. Every component should inherit from the same palette.

6. **Whitespace is a component.** Leave generous spacing between component blocks. Cramming components together undermines their individual impact.
