# Weekly META Wrap — Cowork Prompt
*Run every Wednesday morning. Covers the previous 7 days.*

---

## PROMPT

Using Windsor.ai, pull the last 7 days of campaign performance data across all connected META ad accounts.

Before generating the email, identify today's date and calculate the following automatically:
- **Today's date** — used as the run date in the footer
- **7-day reporting period** — 7 days prior to today through yesterday (the last full day of data)
- **30-day benchmark period** — 30 days prior to today through yesterday

Use these calculated dates throughout the email wherever a date or date range is referenced. Do not use placeholders — insert the actual dates.

**Conversion Event Scanning — Important:**
When pulling results data for each account, scan for ALL of the following event types — do not limit to standard META events only:

Standard META events to check: Purchase, Lead, Schedule, Contact, CompleteRegistration, SubmitApplication, Subscribe, StartTrial, AddToCart, InitiateCheckout, ViewContent, PageView, Search, AddPaymentInfo, AddToWishlist, FindLocation, CustomizeProduct, Donate.

Custom conversion events to check: Also scan for any non-standard or custom-named conversion events configured at the account or pixel level — these may include events such as `booking_confirmed`, `lead_form_submit`, `contact_page_view`, `enquiry_submitted`, `thank_you_page`, `form_complete`, or any other custom event name Windsor.ai returns for that account.

For each account, return whichever event type has the highest volume as the primary Result. Label it explicitly with the event name (e.g. "14 booking_confirmed", "8 lead_form_submit", "23 purchases").

If Windsor.ai returns zero events of any type for an account with active spend, flag it in Account Errors as: "Zero conversions returned — account likely uses unmapped custom conversion events. Check META Events Manager for custom event names and map them in Windsor.ai before next run." Do NOT flag it generically as a pixel error unless there is additional evidence of a tracking problem.

Pull both 7-day and 30-day performance data for all connected META ad accounts, at both **account level and campaign/ad set level**. All figures in AUD ($). Kosta Galanis, pointdot.

---

## OUTPUT FORMAT & UX RULES

This report is read by a time-poor META ad trader managing 40+ accounts. Apply these rules to every section without exception:

**Rule 1 — TL;DR first.**
Every flag opens with a single bold line that contains the account name, the problem, and the number. E.g. `Trojan 4x4 — Frequency 5.68 — Pause now` or `Water Tiger — ROAS 0.96x vs 11.87x avg — Check pixel`. No preamble. No context first.

**Rule 2 — Metrics strip, not prose.**
After the TL;DR, show a compact horizontal metrics strip with 3–4 data points only. Format: `Metric: Value` separated by pipes. E.g. `Spend: $457 | CTR: 6.51% | ROAS: 0.96x | Benchmark: 11.87x`

**Rule 3 — Bullets, not paragraphs.**
Why it matters = maximum 2 bullets. Each bullet is one sentence. No "this suggests that" language. State the fact and its implication directly.

**Rule 4 — One action only.**
Every flag ends with a single bolded action line. One sentence. One verb. E.g. `→ Pause "Wangaratta Offroad" campaign now and relaunch only with fresh video creative.` If there are multiple actions, pick the most important one. Do not list secondary actions.

**Rule 5 — Creative briefs are collapsed.**
Any creative direction is placed inside a collapsed "Creative Brief" block AFTER the action line. It does not interrupt the decision flow. Keep it tight: Format / Hook / Draw from / Avoid — one line each, no prose.

**Rule 6 — Top Performer card comes last.**
The Top Performer card sits below the creative brief if present, or below the action if no creative brief. It never interrupts the flag flow.

**Rule 7 — No filler language.**
Remove: "this suggests", "it appears", "it's worth noting", "please be aware", "as mentioned", "confirm whether". Every word must earn its place.

---

## EMAIL STRUCTURE

**SUBJECT LINE:**
Weekly META Wrap — [Date Range] | [X] Active Accounts | [X] Alerts

---

**Hi Kosta,**

Here's your weekly META wrap. Start at the top, work down.

---

### 📊 QUICK SNAPSHOT

Produce a table with one row per client account:
- Client name
- 7-day spend (AUD)
- Results (7d) — scan all standard and custom conversion event types. Return highest-volume primary event, labelled explicitly (e.g. "14 leads", "6 bookings"). Show two events if both meaningful (e.g. "12 leads / 4 calls"). Show — only if genuinely zero events exist — always triggers Account Errors flag.
- Cost Per Result (7d) — spend ÷ primary result count. Dollar figure. Label event type if helpful (e.g. $24.00 lead). Show — if no data.
- Cost Per Result (30d avg) — same metric, 30-day average. Show — if no data.
- Pacing (✅ On Pace / ⚠️ Over / ⚠️ Under)

Sort: ⚠️ accounts first. Include pacing % where available.

---

### ⚠️ ACCOUNT ERRORS — Fix First

Apply Output Format Rules above. Each flag:

**[TL;DR — one line: Account — Issue — Implication]**
`Metrics strip`
- Bullet: what's broken
- Bullet: why it matters before optimising
**→ Single action**

Flag: pixel not firing, conversion flatlined, account restricted, payment failure, disapproved ads, zero events on active spend (flag as likely unmapped custom conversions).

If none: *No errors detected this week ✅*

---

### 🔴 FIX THIS — Action Required This Week

Apply Output Format Rules above. Each flag:

**[TL;DR — one line: Account — Metric vs Benchmark — Verdict]**
`Metrics strip: Spend | Key metric | Benchmark | Campaign name`
- Bullet: the core problem in one sentence
- Bullet: the implication if not actioned
**→ Single action**

[Creative Brief — collapsed, only if creative refresh recommended]
Format: / Hook: / Draw from: / Avoid: — one line each

[Top Performer Card — always include]

Flag if: zero conversions with $50+ AUD spend, Cost Per Result +30% above 30d avg, frequency above 4.0, over-pacing +20%, under-pacing −20%, ROAS drop −30% below 30d avg.

If none: *No critical issues this week ✅*

---

### ✅ CHECK THIS — Needs A Human Eye

Apply Output Format Rules above. Each flag:

**[TL;DR — one line: Account — Metric — Watch signal]**
`Metrics strip: relevant data points`
- Bullet: what's changing
- Bullet: what to watch for
**→ Single action**

[Creative Brief — collapsed, only if creative fatigue flagged]
[Top Performer Card — include if creative fatigue or CTR decline flagged]

Flag if: frequency 3.0–4.0, spend up 35%+ WoW, CTR down 20%+ WoW, CTR 15%+ below 30d avg, Cost Per Result trending up but below 30% threshold.

If none: *Nothing to flag this week ✅*

---

### 💡 CONSIDER THIS — When Time Permits

Apply Output Format Rules above. Maximum 3 items. Each flag:

**[TL;DR — one line: Account — Opportunity — Potential upside]**
`Metrics strip: supporting data`
- Bullet: the opportunity
- Bullet: what action unlocks it
**→ Single action**

Opportunities: audience expansion, budget reallocation (name both campaigns), creative test needed (4+ weeks no refresh), LAL gap, bid strategy upgrade, retargeting gap.

If none: *No proactive opportunities this week ✅*

---

That's it for this week. Reply or flag anything that needs escalating.

**Escalation note:** If any 🔴 Fix This items remain unresolved by the next weekly wrap, please flag them to the Agency Lead so they can be picked up at agency level.

Kosta Galanis
pointdot

---
*Generated by Claude via Windsor.ai — [DATE] — Covers [DATE RANGE] (7-day) | [DATE RANGE] (30-day benchmark)*

---

## NOTES FOR USE

- The only fixed fields are Kosta Galanis and pointdot in the sign-off — everything else is automatic
- If a client account has no data returned by Windsor.ai, note it as "No data available — check connection" in the snapshot table
- Thresholds can be adjusted within each section as benchmarks evolve
- Campaign and ad set names should be pulled exactly as they appear in META Ads Manager
- Custom conversion event names should be pulled exactly as Windsor.ai returns them
