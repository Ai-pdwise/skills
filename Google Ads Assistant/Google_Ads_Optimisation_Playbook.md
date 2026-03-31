---
name: google-ads-optimisation-playbook
description: Google Ads optimisation framework and reference document for media buyers. Use this skill whenever auditing, diagnosing, optimising, or reporting on a Google Ads account. Triggers on phrases like "audit this account", "optimise Google Ads", "weekly optimisation", "monthly deep-dive", "diagnose CPA", "account health score", "ad copy test", "n-gram analysis", "bidding strategy review", "campaign structure review", "search term analysis", or any request to evaluate, troubleshoot, or improve Google Ads performance. Contains KPI benchmarks by client type (eCommerce, lead gen, local/service), weekly and monthly checklists, decision trees for common problems (high CPA, low ROAS, low CTR, dropping conversion rate), ad copy frameworks, bidding strategy guides, account health scoring, campaign structure principles, conversion tracking configuration, audience and remarketing setup, ad copy testing methodology, and n-gram analysis process.
---

# Google Ads Optimization Playbook
**Media Buyer Reference Document**
Client Types: eCommerce/DTC · Lead Generation · Local/Service Businesses
Tools: Google Ads Editor · Looker Studio · Notion/Google Sheets

---

## How to Use This Playbook
Upload this file to Claude when working on any Google Ads account. Claude will use it as your optimization framework to audit accounts, diagnose problems, suggest actions, and generate reports aligned to your process.

---

## Part 1 — KPI Benchmarks by Client Type

### eCommerce / DTC
| Metric | Weak | Acceptable | Strong |
|---|---|---|---|
| ROAS (Search) | < 3x | 3–5x | > 5x |
| ROAS (PMAX) | < 4x | 4–7x | > 7x |
| CTR (Search) | < 3% | 3–6% | > 6% |
| Conversion Rate | < 1% | 1–3% | > 3% |
| CPC | > $2.50 | $1–$2.50 | < $1 |
| Impression Share | < 40% | 40–70% | > 70% |

### Lead Generation
| Metric | Weak | Acceptable | Strong |
|---|---|---|---|
| CPL | > $80 | $30–$80 | < $30 |
| CTR (Search) | < 4% | 4–8% | > 8% |
| Conversion Rate | < 3% | 3–8% | > 8% |
| Quality Score (avg) | < 5 | 5–7 | > 7 |
| Impression Share | < 40% | 40–75% | > 75% |

### Local / Service Businesses
| Metric | Weak | Acceptable | Strong |
|---|---|---|---|
| CPL / Cost per Call | > $60 | $20–$60 | < $20 |
| CTR (Search) | < 5% | 5–10% | > 10% |
| Conversion Rate | < 5% | 5–12% | > 12% |
| Quality Score (avg) | < 5 | 5–8 | > 8 |
| Impression Share | < 50% | 50–80% | > 80% |

---

## Part 2 — Weekly Optimization Checklist

Run this for every active client, every week. Target: 20–30 minutes per client.

### Performance Review
- [ ] Compare this week vs. last week: Spend, Conversions, CPA/ROAS/CPL
- [ ] Compare vs. monthly KPI target — on track, ahead, or behind?
- [ ] Check for sudden drops or spikes (flag if >20% change week-over-week)

### Search Terms
- [ ] Open Search Terms report (last 7 days)
- [ ] Add irrelevant terms as negatives (campaign or account level)
- [ ] Identify high-intent new terms → consider adding as exact match keywords
- [ ] Check for brand terms appearing in non-brand campaigns → add as negatives if needed

### Budget & Pacing
- [ ] Is daily budget being fully spent by top campaigns?
- [ ] Are any campaigns limited by budget? → Reallocate from underperformers
- [ ] Is spend tracking toward monthly budget target?

### Ads & Assets
- [ ] Are there disapproved ads? → Fix immediately
- [ ] Any ad groups with only one active ad? → Add a second variant
- [ ] Check for low Ad Strength RSAs → improve headlines/descriptions

### Anomaly Check
- [ ] Review Recommendations tab → Accept, dismiss, or note for review
- [ ] Check Auction Insights for new competitors
- [ ] Review Quality Scores for top keywords — any drops?

---

## Part 3 — Monthly Deep-Dive Checklist

Run this at the start of each month reviewing the prior month. Target: 60–90 minutes per client.

### Performance Analysis
- [ ] Month-over-month comparison (all KPIs)
- [ ] Compare to same month last year if data available
- [ ] Segment performance by campaign type (Search / Shopping / PMAX / Display)
- [ ] Segment by device — adjust bids if mobile/desktop gap is significant
- [ ] Segment by location — are any regions wasting spend?
- [ ] Segment by time of day / day of week — adjust ad schedule if needed

### Keywords
- [ ] Identify top 20% keywords driving 80% of conversions → protect budget for these
- [ ] Identify keywords with high spend and zero conversions (30-day window) → pause or reduce bids
- [ ] Review match type distribution — too broad? Too restrictive?
- [ ] Add new keywords from Search Terms report wins
- [ ] Refresh negative keyword lists

### Bidding Strategy Review
- [ ] Is the current bidding strategy aligned to the client's goal?
- [ ] For Smart Bidding: Is there sufficient conversion data? (Min. 30–50 conversions/month recommended)
- [ ] Review Target CPA / Target ROAS — adjust if performance has stabilised up or down
- [ ] Check Learning Period status — avoid making big changes during learning

### Ad Copy
- [ ] Identify bottom 20% performing ads by conversion rate → pause and replace
- [ ] Review RSA asset performance report → remove low-rated assets, add new ones
- [ ] Ensure every ad group has at least 2 active RSAs
- [ ] Check seasonal relevance of ad copy — update for upcoming events/promotions

### Extensions / Assets
- [ ] Sitelinks present and relevant?
- [ ] Callout extensions updated?
- [ ] Structured snippets present?
- [ ] Call extension active (Lead Gen + Local)?
- [ ] Price extensions relevant (eComm)?
- [ ] Promotion extension active if there's an active offer?

### Audiences
- [ ] Remarketing lists building and attached to campaigns?
- [ ] Customer match list uploaded and active?
- [ ] In-market and affinity audiences in observation mode?
- [ ] Review audience performance — adjust bids for high-converting segments

### PMAX (if running)
- [ ] Review asset group performance
- [ ] Check search themes are relevant
- [ ] Review audience signals — are they aligned to actual converters?
- [ ] Check PMAX vs. Search cannibalization in Auction Insights
- [ ] Assess whether brand terms are being consumed by PMAX

### eCommerce Specific
- [ ] Shopping feed health check (disapprovals, missing attributes)
- [ ] Review top products by revenue vs. spend
- [ ] Segment high/low ROAS products — adjust bidding or pause poor performers
- [ ] Check for out-of-stock products still being advertised

### Local / Service Specific
- [ ] Review call recording/quality (if call tracking active)
- [ ] Check Google Business Profile integration and Local campaigns
- [ ] Review location targeting radius — too wide or too narrow?
- [ ] Check competitor offers in area

---

## Part 4 — Optimization Decision Trees

### 🔴 CPA / CPL Too High
1. Is conversion tracking accurate? → If no: fix before anything else
2. Are there keywords with very high CPA dragging the average up? → Pause or reduce bids
3. Is the search term report full of irrelevant queries? → Add negatives aggressively
4. Is the landing page converting? → Check landing page conversion rate in GA4
5. Is the bidding strategy in learning mode? → Wait before making changes
6. Is Target CPA set too low, causing under-delivery? → Raise target slightly (10–15%)
7. Is ad copy relevant to search intent? → Review and rewrite low-CTR ads
8. Are broad match keywords out of control? → Shift to phrase/exact and add negatives

### 🔴 ROAS Too Low (eCommerce)
1. Check product-level ROAS → Are low-margin products eating budget?
2. Check PMAX vs. Search attribution — is PMAX claiming credit for brand/repeat customers?
3. Review shopping feed — are prices competitive? Are titles optimised?
4. Is Target ROAS set too low, resulting in cheap but low-value clicks?
5. Check for high cart abandonment → Improve remarketing or landing page
6. Are promotions/discounts reflected in ad copy?

### 🔴 CTR Too Low
1. Is ad copy relevant to the keyword intent?
2. Are all asset types filled in? (Especially sitelinks, callouts, structured snippets)
3. Is the keyword match type too broad, causing irrelevant impressions?
4. Are competitors outbidding for top position? → Check Impression Share (top)
5. Is Quality Score low? → Review Expected CTR component
6. Test new headline angles: price, urgency, USP, social proof

### 🔴 Conversion Rate Dropping
1. Has landing page changed recently? → Compare before/after
2. Has page speed worsened? → Run Core Web Vitals test
3. Is traffic quality lower? → Review search terms for intent shift
4. Seasonal factor? → Compare same period last year
5. Is the offer/CTA still competitive vs. market?
6. Check mobile vs. desktop conversion rate split — mobile issue?

### 🟠 Impression Share Lost
- If **lost to Budget**: Increase budget OR pause lower-priority campaigns to consolidate
- If **lost to Rank**: Improve Quality Score (ad relevance, CTR, landing page) OR increase bids/Target CPA

### 🟠 Quality Score Below 5
1. Check which component is low: Expected CTR, Ad Relevance, or Landing Page Experience
2. **Expected CTR low** → Rewrite ad copy with stronger hooks and keyword inclusion
3. **Ad Relevance low** → Tighten ad group themes, ensure keyword appears in headline
4. **Landing Page Experience low** → Improve page speed, relevance, and ease of navigation

### 🟠 PMAX Underperforming
1. Review asset group quality — are all asset types present and high quality?
2. Check audience signals — are they too broad or misaligned?
3. Add search themes to guide targeting
4. Check if PMAX is cannibalising Search → Temporarily pause and compare
5. Review if brand terms are being consumed → Create brand campaign and exclude from PMAX

---

## Part 5 — Ad Copy Frameworks

### Universal Formula
**Headline structure:** [Keyword/Problem] | [USP/Differentiator] | [CTA/Offer]
**Description structure:** Expand the benefit → Address an objection → Include a CTA with urgency or proof

### eCommerce / DTC
**High-performing headline angles:**
- Price/Value: "From $X — Free Shipping Over $X"
- Social Proof: "Trusted by X,000+ Customers"
- Urgency: "Sale Ends Sunday — Shop Now"
- Product Benefit: "Lasts 3x Longer Than Competitors"
- USP: "Made in Australia — 30-Day Returns"

**Description angles:**
- "Shop [category] with free next-day delivery. Over X,000 5-star reviews. Easy returns."
- "Compare [product type] from top brands. Best price guarantee. Order by 3pm for same-day dispatch."

### Lead Generation
**High-performing headline angles:**
- Outcome-focused: "Get X Leads in 30 Days"
- Free offer: "Free Consultation — No Obligation"
- Problem-led: "Struggling With [Problem]? We Can Help"
- Credibility: "Rated 5 Stars on Google"
- Speed/Ease: "Response Within 2 Hours"

**Description angles:**
- "Speak to a specialist today. No long-term contracts. X clients helped since [year]."
- "Tell us your requirements and get a free, no-obligation quote within 24 hours."

### Local / Service Businesses
**High-performing headline angles:**
- Location-specific: "[Service] in [City] — Available Today"
- Speed: "Same-Day [Service] Available"
- Trust: "Family Run Since [Year] — Fully Insured"
- Offer: "First Visit Free — Book Online in 60 Seconds"
- Urgency: "Limited Availability This Week"

**Description angles:**
- "Serving [City] and surrounding areas. Call now for a free quote. Fully accredited."
- "Fast, reliable [service] with 5-star reviews. X years local experience."

### RSA Best Practices
- Write 15 unique headlines — no repeats or near-duplicates
- Write 4 unique descriptions
- Include primary keyword in at least 2 headlines
- Represent: USP, offer/price, CTA, social proof, and urgency across assets
- Pin sparingly — only pin headline 1 if brand/legal requires it
- Avoid pinning descriptions unless critical

---

## Part 6 — Bidding Strategy Guide

| Goal | Recommended Strategy | When to Use |
|---|---|---|
| Maximise conversions within budget | Maximise Conversions | New campaigns, <30 conv/month |
| Hit a target cost per conversion | Target CPA | 30+ conv/month, stable performance |
| Maximise revenue/value | Maximise Conv. Value | eComm with value tracking |
| Hit a target return on ad spend | Target ROAS | 50+ conv/month, eComm |
| Drive traffic, awareness | Maximise Clicks / tCPM | Top of funnel, Display |
| Manual control | Manual CPC + Enhanced | Low data, testing phase |

**Bidding Transition Rules:**
- Never switch bidding strategy during a promotion or peak period
- Always allow 2–4 week learning period after a change before evaluating
- When raising Target ROAS, increase in 10–15% increments max
- When lowering Target CPA, decrease in 10–15% increments max
- If performance tanks after a strategy switch, revert and investigate before trying again

---

## Part 7 — Account Health Scoring

Use this to score any account out of 100 during an audit or monthly review.

| Category | Max Score | Score Criteria |
|---|---|---|
| Conversion Tracking | 20 | 20 = accurate + GA4 linked. 10 = tracking present but issues. 0 = broken/missing |
| Campaign Structure | 15 | 15 = clean, logical, segmented. 8 = some issues. 0 = chaotic |
| Keywords & Negatives | 15 | 15 = tightly themed + active negative lists. 8 = partial. 0 = none |
| Ad Copy & Assets | 15 | 15 = strong RSAs + all extensions. 8 = basic. 0 = minimal/disapproved |
| Bidding Strategy | 10 | 10 = aligned to goal + sufficient data. 5 = suboptimal. 0 = wrong strategy |
| Audience & Remarketing | 10 | 10 = lists built + audience signals active. 5 = partial. 0 = none |
| Landing Pages | 10 | 10 = fast + relevant + clear CTA. 5 = issues present. 0 = poor |
| Reporting & Tracking | 5 | 5 = Looker Studio live + goals tracked. 0 = manual/none |

**Score Interpretation:**
- 85–100: Healthy — focus on testing and scaling
- 65–84: Moderate — fix flagged issues within 30 days
- 40–64: Needs Work — prioritise P1 fixes immediately
- Below 40: Critical — full account rebuild likely needed

---

## Part 8 — Campaign Structure Principles

A well-structured account makes every other optimisation easier. Poor structure inflates CPAs, obscures performance data, and limits Smart Bidding effectiveness. Review structure during onboarding and as part of the monthly deep-dive.

---

### Campaign Segmentation
Segment campaigns by the following where volume and budget allow:

**By intent temperature**
- Branded search (highest intent — protect this budget always)
- Non-brand search (core acquisition)
- Competitor keywords (separate — different expectations and benchmarks)
- Remarketing / RLSA (separate bid logic applies)

**By funnel stage**
- Top of funnel: awareness and education queries
- Bottom of funnel: purchase or enquiry-ready queries
- Keep these separate so bidding strategies and budgets can be managed independently

**By product or service line**
- Segment where products or services have meaningfully different margins, CPAs, or conversion paths
- Avoids high-volume low-margin activity consuming budget earmarked for priority offerings

**By match type (where applicable)**
- Exact match campaigns for proven high-performers
- Phrase/broad campaigns for discovery and search term mining
- Prevents exact match terms from competing against their own broad equivalents

---

### Brand vs. Non-Brand Separation
Always run brand and non-brand keywords in separate campaigns. Blending them produces misleading performance data — brand terms convert at a lower CPA and higher CTR, which inflates the apparent health of non-brand activity.

- Brand campaign: contains all variations of the business name, common misspellings, and branded product terms
- Non-brand campaign: excludes all brand terms via negative keywords
- Report on brand and non-brand separately — never blend the two in client-facing performance summaries
- Brand Impression Share is a separate KPI — track it independently to monitor brand defence

---

### Competitor Campaign Strategy
Competitor campaigns target users searching for a named competitor. They typically deliver lower CTR and conversion rates than brand or non-brand campaigns and require a clear strategic rationale before running.

**When to run a competitor campaign**
- Client is in a mature, competitive market with identifiable direct competitors
- Client has a clear and demonstrable USP relative to those competitors
- Budget allows for it without cannibalising higher-priority campaigns

**How to structure it**
- Separate campaign with its own budget — never blend with non-brand
- Ad copy must lead with the client's differentiator, not attack the competitor directly (Google policy)
- Set realistic benchmarks — expect lower CTR and higher CPA than non-brand
- Review monthly and pause if cost per acquisition is not commercially viable

**What to avoid**
- Bidding on competitors when the client cannot articulate why a customer should switch
- Letting competitor campaigns consume budget that should be protecting the client's own brand terms

---

## Part 9 — Conversion Tracking & GA4 Configuration

Conversion tracking is the single most important foundation in any Google Ads account. Smart Bidding is only as good as the data it is trained on. If tracking is broken, misconfigured, or measuring the wrong actions, every optimisation decision downstream is compromised.

---

### What to Track and How to Prioritise

**Primary conversion actions** — used by Smart Bidding to optimise. Set only one or two per campaign. Should represent the actual business outcome:
- eCommerce: purchase (with revenue value)
- Lead Gen: form submission, phone call (60 seconds+ duration), booked appointment
- Local/Service: phone call, contact form, direction request

**Secondary conversion actions** — tracked for insight but excluded from Smart Bidding. Use for micro-conversions:
- Page engagement events (scroll depth, time on site)
- Soft enquiries (brochure downloads, live chat initiated)
- Add to cart (eComm — useful for funnel analysis but not primary optimisation signal)

**Common configuration mistakes to check**
- [ ] Duplicate conversion actions inflating reported conversions
- [ ] All actions set to primary when only one should be
- [ ] Conversion window too short for the actual sales cycle
- [ ] GA4 goals not imported — relying solely on Google Ads tag
- [ ] Value not assigned to conversions for eComm or high-value lead gen clients

---

### GA4 Integration Checklist
- [ ] GA4 property linked to Google Ads account
- [ ] Key GA4 events imported as Google Ads conversion actions
- [ ] Auto-tagging enabled in Google Ads
- [ ] GA4 confirming sessions from Google Ads (check Acquisition report)
- [ ] Conversion events marked correctly in GA4 as conversions (not just events)
- [ ] Enhanced measurement enabled in GA4 for form submissions and outbound clicks

---

### Offline Conversion Imports
Relevant for lead gen clients where the Google Ads conversion (a form fill or call) is not the final business outcome. A lead that does not close is not equal to a lead that does — but without offline conversion imports, Smart Bidding treats them identically.

**How it works**
- Google Ads passes a GCLID (click identifier) with each conversion
- The CRM or booking system captures and stores the GCLID alongside the lead
- When a lead progresses (qualified, booked, closed), the outcome is uploaded back to Google Ads with the original GCLID
- Smart Bidding recalibrates toward the traffic patterns that produce actual business outcomes, not just form fills

**When to implement it**
- Lead gen clients with a CRM in place (HubSpot, Salesforce, or similar)
- Client can confirm close rate varies meaningfully by lead source or keyword
- Monthly lead volume is sufficient to generate usable signal (30+ closed outcomes per month recommended)

**Implementation checklist**
- [ ] GCLID capture confirmed in CRM or lead system
- [ ] Offline conversion action created in Google Ads
- [ ] Upload schedule agreed — weekly minimum, daily preferred
- [ ] Smart Bidding strategy updated to optimise toward offline conversion action once sufficient data is present (allow 4–6 weeks of import history first)

---

## Part 10 — Audience & Remarketing Structure

Remarketing lists should be built and active from day one of any campaign. Audiences in observation mode cost nothing and provide valuable performance data. Audiences used for remarketing campaigns or bid adjustments require minimum list sizes — build them early.

---

### Core Remarketing Lists to Build

| Audience | Definition | Primary Use |
|---|---|---|
| All website visitors (30 days) | Anyone who visited the site | Broad remarketing, observation |
| All website visitors (90 days) | Wider pool for lower-volume sites | Observation, Display remarketing |
| Product/service page visitors | Visited a specific category or service page | Mid-funnel remarketing |
| Cart abandoners (eComm) | Added to cart but did not purchase | High-priority remarketing |
| Past converters (90 days) | Completed a purchase or enquiry | Exclusion from prospecting, upsell campaigns |
| Past converters (180–365 days) | Lapsed customers | Reactivation campaigns |

---

### How to Use Lists Strategically

**Exclusions**
- Exclude recent converters from prospecting campaigns to avoid wasting spend on people who have already acted
- Exclude past converters from competitor campaigns — no need to defend against competitors with customers already won

**Bid adjustments (Search)**
- Apply remarketing lists to Search campaigns in observation mode
- Review performance after 30 days — adjust bids up for high-converting segments, down or exclude for poor performers

**Dedicated remarketing campaigns**
- Where list sizes allow (minimum 1,000 users for Search, 100 for Display/YouTube), create dedicated remarketing campaigns with tailored messaging
- Messaging should reflect where the user is in the funnel — do not show a first-visit awareness ad to a cart abandoner

**Audience signals (PMAX)**
- Upload remarketing lists as audience signals in PMAX asset groups
- Include customer match lists where available
- Review whether PMAX is over-relying on remarketing audiences rather than acquiring new customers — check new vs. returning customer split if available

---

### Audience Observation Checklist (Monthly)
- [ ] All core lists building correctly — check user counts
- [ ] In-market and affinity audiences attached to campaigns in observation mode
- [ ] Audience performance reviewed — any segments with significantly better or worse CPA/ROAS?
- [ ] Bid adjustments applied or updated based on observed performance
- [ ] Converter exclusions in place on all prospecting campaigns

---

## Part 11 — Ad Copy Testing Framework

Testing ad copy without a structured process produces noise, not insight. The goal is to isolate variables, accumulate enough data to make a reliable decision, and build a compounding record of what works for each client.

---

### Testing Principles
- Test one variable at a time where possible — changing headline angle, offer, or CTA in isolation makes it clear what drove the performance difference
- Never run more than 2–3 active RSA variants per ad group — too many splits data and slows learning
- Allow a minimum of 2–4 weeks and 50+ conversions per variant before drawing conclusions
- Use Google Ads asset performance labels (Learning, Low, Good, Best) as a directional signal — not the sole decision criteria
- Document every test and outcome — patterns across clients build into a reusable knowledge base

---

### What to Test and in What Order

**Priority 1 — Offer and value proposition**
The biggest lever. Test fundamentally different angles before testing execution details.
- Price/value vs. outcome vs. trust vs. urgency
- Example: "Free Consultation" vs. "Results in 30 Days" vs. "Rated #1 in [City]"

**Priority 2 — Headline 1 angle**
The first headline carries the most weight. Once an offer angle is confirmed, test how it is expressed.
- Question format vs. statement vs. keyword inclusion
- Example: "Struggling to Generate Leads?" vs. "More Leads, Less Wasted Budget" vs. "Google Ads That Actually Convert"

**Priority 3 — CTA and urgency**
- Soft CTA vs. direct CTA vs. urgency-led
- Example: "Learn More" vs. "Get a Free Quote" vs. "Limited Spots — Book Today"

**Priority 4 — Description copy**
- Benefit-led vs. objection-handling vs. social proof
- Once headline direction is locked, descriptions fine-tune the message

---

### RSA Testing Process
1. Launch ad group with 2 RSA variants — each representing a distinct angle, not minor wording tweaks
2. Set ad rotation to "Do not optimise" during the test period if you want equal exposure (use with caution — Google's optimisation often accelerates valid results)
3. Review after minimum 2 weeks and 50+ conversions per variant
4. Pause the lower performer, replace with a new challenger variant
5. Log the result: what was tested, what won, and the likely reason why
6. Apply winning patterns to other ad groups or campaigns where the audience and intent are similar

---

### Ad Copy Testing Checklist (Monthly)
- [ ] Are there ad groups with only one active RSA? → Add a challenger variant
- [ ] Have any variants been running for 60+ days without a review? → Assess and refresh
- [ ] Are asset performance labels showing predominantly Low ratings? → Remove and replace
- [ ] Has a winning angle been identified? → Roll it out across relevant ad groups
- [ ] Have test results been documented for future reference?

---

## Part 12 — N-Gram Analysis

N-gram analysis breaks search terms down into individual words (1-gram), two-word phrases (2-gram), and three-word phrases (3-gram) to identify patterns across the entire search term pool — not just individual queries. It surfaces recurring words and phrases that are either driving strong performance or quietly wasting budget at scale.

Run this as part of the monthly deep-dive, or any time CPA/CPL is drifting and the cause is not obvious from top-level keyword data.

---

### Why It Matters
A single search term with high CPA is easy to spot and pause. But if the word "free", "cheap", or "DIY" is appearing across 40 different search terms — each individually below the pause threshold — the cumulative damage is significant and invisible without n-gram analysis.

The same logic applies in reverse. A high-converting word or phrase appearing across multiple queries is a signal to build around it — tighter ad groups, dedicated landing pages, or exact match keywords.

---

### How to Run It in Google Sheets

**Step 1 — Export your search terms**
- In Google Ads, go to Keywords → Search Terms
- Set the date range to the last 30 days (or the period under review)
- Export as CSV, including: Search Term, Impressions, Clicks, Cost, Conversions, Conv. Value (if eComm)

**Step 2 — Split terms into n-grams**
Use this formula approach in Google Sheets to extract individual words from each search term, then use COUNTIF and SUMIF to aggregate metrics by word or phrase. Alternatively, paste your raw search term data into Claude and request an n-gram breakdown directly (see Part 9).

**Step 3 — Build your frequency and performance table**
For each n-gram, capture:

| N-Gram | Impressions | Clicks | Cost | Conversions | CPA / ROAS | Frequency |
|---|---|---|---|---|---|---|
| "free" | | | | | | |
| "near me" | | | | | | |
| "how to" | | | | | | |

Sort by Cost descending first to find where budget is going. Then sort by CPA/ROAS to identify what is and is not converting.

---

### What to Look For

**Negative keyword candidates**
Flag any n-gram that appears in 3 or more search terms and has zero or near-zero conversions relative to spend. Common patterns include:
- Informational intent: "how to", "what is", "can I", "guide", "tutorial"
- Price-sensitive intent: "free", "cheap", "discount", "DIY"
- Irrelevant modifiers: job-seeking terms, competitor brand fragments, unrelated locations

**Exact match or ad group opportunities**
Flag any n-gram with strong conversion volume and a CPA/ROAS better than the campaign average appearing across multiple queries. These are candidates for:
- Dedicated exact match keywords
- Tighter single-theme ad groups with tailored copy
- Dedicated landing pages if volume justifies it

**Bid adjustment signals**
N-grams that consistently outperform average can support a case for higher bids or budget reallocation toward campaigns or ad groups capturing those terms.

---

### Monthly N-Gram Checklist
- [ ] Export search terms for the prior month
- [ ] Run 1-gram, 2-gram, and 3-gram frequency and performance tables
- [ ] Identify top 10 n-grams by cost — are they earning their spend?
- [ ] Add confirmed negative n-grams to account-level or campaign-level negative lists
- [ ] Flag high-performing n-grams as exact match keyword candidates
- [ ] Document findings and actions taken in client monthly notes

---

### Using Claude for N-Gram Analysis
Paste your raw search term export (CSV or plain text) into a Claude conversation alongside this playbook and use a prompt like:

- *"Analyse these search terms using n-gram analysis. Break them into 1, 2, and 3-word patterns. Show me frequency, total cost, total conversions, and CPA for each. Flag the top negative keyword candidates and the top exact match opportunities."*
- *"Here are last month's search terms for a lead gen client. Run an n-gram breakdown and tell me what to add to the negative keyword list and what to consider promoting to exact match."*

---

## Part 13 — How to Use This Playbook With Claude

When uploading this file to a Claude conversation, use prompts like:

- *"Here is my optimisation playbook. I'm going to paste in data from a client account. Please audit it against my playbook and tell me what to fix first."*
- *"Using my playbook, generate a weekly optimisation report for this client based on the data below."*
- *"Based on my playbook decision trees, my client's CPA has increased 40% this month. Walk me through the diagnosis."*
- *"Write 15 RSA headlines for a lead gen client in the home renovation niche, following my ad copy framework."*
- *"Score this account using my Account Health Scoring system and give me a priority action list."*

---

*Playbook Version 1.0 — Created March 2026*
*Update this document as your process evolves.*
