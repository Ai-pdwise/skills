# Weekly META Wrap — Skill Document
**Agency:** pointdot
**Owner:** Kosta Galanis
**Last Updated:** March 2026

---

## What This Skill Does

The Weekly META Wrap is an automated account health audit across all connected META ad accounts. It pulls 7-day performance data via Windsor.ai, benchmarks against a 30-day average, and generates a structured action-first email for the META ad trader.

The report is designed for a time-poor trader managing 40+ accounts. Every flag follows a strict UX framework: TL;DR first, metrics strip, 2 bullets max, one action. The goal is full report review and actioning in under 5 minutes.

---

## When To Run It

- **Every Wednesday morning**
- Covers the previous 7 days (Wednesday to Tuesday)
- Run time: approximately 2–5 minutes depending on account count

---

## Requirements Before Running

### Data Connections
- [ ] Windsor.ai MCP is connected and active in Claude
- [ ] All client META ad accounts are connected via Windsor.ai
- [ ] Custom conversion events mapped in Windsor.ai (see Custom Conversion Events section below)
- [ ] Any new client accounts added since last run have been connected

### Files Required (in this folder)
- [ ] `weekly-meta-wrap-prompt.md` — the main instruction prompt
- [ ] `weekly-meta-wrap-template.html` — the visual email output template

---

## How To Run It

1. Open Claude Desktop and start a new task using **Work in a folder**
2. Select the `pointdot — Cowork > META` folder
3. Reference `weekly-meta-wrap-prompt.md` as the task instruction
4. Claude automatically calculates the date range and pulls data via Windsor.ai
5. Review output before sending — spot check client names, figures, and flags
6. Copy the email output and send to the META trader

---

## Report UX Framework

Every flag in the report follows this strict structure — no exceptions:

```
BOLD TL;DR — Account — Problem — Number — Verdict
Spend: $X | Metric: X | Benchmark: X | Campaign: name
• Core problem in one sentence
• Implication if not actioned
→ Single bolded action

[Creative Brief — collapsed, only when creative refresh needed]
Format: / Hook: / Draw from: / Avoid:

[Top Performer Card — metrics + insight]
```

### The 7 UX Rules
1. **TL;DR first** — account, problem, number, verdict in one line
2. **Metrics strip** — 3–4 data points only, no prose
3. **2 bullets max** — fact + implication, no "this suggests" language
4. **One action only** — one verb, one sentence, most important action
5. **Creative briefs collapsed** — never interrupt the decision flow
6. **Top Performer card last** — never interrupts the flag
7. **No filler language** — every word earns its place

---

## Output Structure

| Section | Purpose | Trader Time |
|---|---|---|
| 📊 Quick Snapshot | One-line per account — Spend, Results, CPR (7d vs 30d), Pacing | 30 seconds |
| ⚠️ Account Errors | Data integrity issues — fix before any optimisation | 1 minute |
| 🔴 Fix This | Urgent issues — action this week | 2 minutes |
| ✅ Check This | Trending issues — monitor and prepare | 1 minute |
| 💡 Consider This | Proactive opportunities — max 3 items | 30 seconds |

---

## Snapshot Table Columns

| Column | Description |
|---|---|
| **Spend (7d)** | Total AUD spend over the reporting period |
| **Results (7d)** | Primary conversion event count. Scans all standard and custom event types. Labelled explicitly (e.g. "14 leads", "6 bookings"). Two events shown if both meaningful. — only if genuinely zero events — always triggers Account Errors. |
| **Cost Per Result (7d)** | Spend ÷ primary result count. Varies by account objective. Labelled with event type where helpful. |
| **Cost Per Result (30d avg)** | 30-day average CPR for benchmark comparison |
| **Pacing** | Budget pacing vs expected monthly spend. % shown where available. |

---

## Key Thresholds

| Metric | Check This | Fix This |
|---|---|---|
| Frequency | 3.0 – 4.0 | Above 4.0 |
| Cost Per Result vs 30d avg | Trending up, below +30% | +30% above 30d avg |
| CTR drop WoW | — | −20% week-over-week |
| CTR vs 30d avg | −15% below 30d avg | — |
| Spend increase WoW | +35% vs prior week | — |
| Budget pacing | — | Over/under by ±20% |
| Zero conversions | — | $50+ AUD spent, zero conversions |
| ROAS drop | — | −30% below 30d avg |

---

## Custom Conversion Events

Many client accounts use non-standard event names (e.g. `booking_confirmed`, `lead_form_submit`) instead of standard META events (Purchase, Lead, Schedule). Windsor.ai may return zero results for these accounts even though conversions are firing correctly in META Ads Manager.

### Two-Part Fix

**Part 1 — Map in Windsor.ai (permanent fix)**
1. META Business Manager → Events Manager → Select each client pixel → Custom Conversions
2. Note every non-standard event name across all accounts
3. Windsor.ai → Connectors → META Ads → map each custom event name
4. Test on one account first (REFORMD PILATES recommended) before mapping all

**Part 2 — Prompt fallback (interim coverage)**
The prompt scans all standard and custom event types Windsor.ai returns. If zero events are found on an account with active spend, it flags it specifically as a likely unmapped custom conversion — not a generic pixel error — directing the trader to the correct fix.

### Identifying Accounts Needing Mapping
Any account showing — in the Results column with "likely uses unmapped custom conversion events" in Account Errors needs Windsor.ai mapping before the next run.

---

## Escalation Protocol

If any 🔴 Fix This items remain unresolved by the following Wednesday's wrap, the trader flags them to the Agency Lead for escalation and reassignment.

---

## Files In This Folder

| File | Description |
|---|---|
| `weekly-meta-wrap-skill.md` | This document |
| `weekly-meta-wrap-prompt.md` | Full Claude prompt — reference when running the task |
| `weekly-meta-wrap-template.html` | Styled HTML email output template |

---

## Future Automations (Planned)

- `weekly-google-wrap-prompt.md` — Google Ads equivalent
- `monthly-client-report-prompt.md` — Client-facing monthly summary
- `daily-anomaly-check-prompt.md` — Lightweight daily spend and conversion check
