---
name: video-brief-creation
description: >
  Use this skill whenever someone asks to create, write, generate, or produce video creative briefs for paid social advertising. Triggers include: 'write a video brief', 'create creator briefs', 'brief an influencer', 'UGC brief', 'video script for ads', 'META video brief', 'brief for content creators', 'paid social video brief', or any request to brief creators on filming ads. Also triggers when a user shares a client landing page, Google reviews, or brand assets and asks for video ad direction. Always use this skill before generating any brief — it contains the complete strategic framework, formatting rules, and output specifications.
---
# Video Brief Creation Skill
Generates strategically grounded, creator-ready video briefs for paid social campaigns. Output is always a formatted .docx and .pdf. Briefs are written for non-professional creators (influencers, real customers, friends and family) and structured so the Pointdot team can send them directly without editing.
These briefs are shooting documents. They tell a creator what to communicate and how to deliver it on camera. They do not contain editing instructions, post-production notes, or delivery specs. Every word exists to help the person in front of the camera perform, not to inform anyone behind a desk.
The full strategic framework, discovery process, DR copywriting principles, section structure, tone rules, PASTOR hook system, studio vs. home allocation, and document formatting spec live in `Video_Brief_PROMPT.md`. Read that file before generating any output.
---
## Step-by-Step Execution
### Step 1 — Run discovery (two routes — identify which applies)
Do not write anything until discovery is complete.
**Route A — No intake form submitted:**
Work through all six discovery topics from `Video_Brief_PROMPT.md > Discovery` in order:
1. Purpose and context (including traffic temperature)
2. The business
3. The customer
4. The offer (including delivery method — this feeds the offer footer)
5. Creative history (including brand tone and energy)
6. The shoot (including who is editing and creator type per brief)
Use in-chat widgets for bounded questions. Use open chat for anything requiring real strategic input. There is no limit on the number of questions. The traffic temperature question belongs in Topic 1 and frames every script arc. Do not proceed until it is confirmed.
**Route B — Pointdot intake form submitted by Lead Strategist:**
1. Parse every field in the form and map it to the six discovery topics using the table in `Video_Brief_PROMPT.md > Route B — Step 1`
2. Run the conflict checks from `Video_Brief_PROMPT.md > Route B — Step 2`
3. Identify only the unanswered gaps and ask for those — do not re-ask what the form has already answered
4. Common form gaps: verbatim review language, price point, creative history, studio/home allocation, confirmed B-roll assets, who is editing, creator type per brief
**Creative fatigue note:** A standard 6-brief batch is designed to sustain 4 to 6 weeks of testing. If the client runs over $500/day per ad, flag the need for a second batch at the 10-day mark. Check the Estimated Monthly Ad Spend field if a form has been submitted.
---
### Step 2 — Research the brand
Run the research sequence after discovery is complete:
1. Visit the client landing page — extract offer, headline, USP claims, objection-handling copy
2. **Google Reviews** — two paths:
   - If Claude in Chrome browser extension is active: search Google reviews for the client automatically. Pull the most recent and most detailed reviews. Extract recurring phrases, specific outcomes customers name, and how they describe the before-state. Do this without asking the briefer.
   - If browser access is not available: ask the briefer for a link to the client's Google Business profile or any review source. If no link is available, ask them to paste 5 to 10 real customer reviews directly into the chat. Do not proceed with invented or paraphrased language.
3. Visit FAQ page — map every FAQ to a real objection
4. Check pricing page — understand the entry point and any bundles. If a Route B form was submitted, cross-reference with the price point gap question from Step 1.
5. If a logo is provided, extract brand hex colours using Python PIL pixel sampling
Do not write briefs until research is complete. Never fabricate brand information.
---
### Step 3 — Challenge the brief
Before writing, run these five checks from `Video_Brief_PROMPT.md > Challenge the brief before proceeding`:
1. **Weak offer** — no clear dollar value or no urgency mechanism
2. **Demographic-only audience** — described as a category, not a moment or situation
3. **Unknown objection** — the #1 objection that stops purchase is unclear
4. **No visual proof** — zero briefs include in-context product footage or location shots
5. **Duplicate emotional territory** — two concepts cover the same ground
Raise issues clearly. Propose alternatives. Do not silently proceed with weak inputs.
---
### Step 4 — Plan the batch
Map out the full batch before writing. Present this plan to the user and get confirmation before writing a single brief. Adjust titles, angles, and traffic temperatures based on feedback.
**6-brief batch (default):**
| Brief | Title | PASTOR Angle | Studio / Home | Traffic Temp |
|-------|-------|-------------|---------------|--------------|
| 01 | [working title] | Problem (P) | Studio | Cold |
| 02 | [working title] | Amplify (A) | Studio | Cold |
| 03 | [working title] | Problem (P) | Studio | Cold |
| 04 | [working title] | Solution (S) | Studio | Cold |
| 05 | [working title] | Offer (O) | Home | Warm |
| 06 | [working title] | Testimony (T) | Home | Cold |
**9-brief batch:**
| Brief | Title | PASTOR Angle | Studio / Home | Traffic Temp |
|-------|-------|-------------|---------------|--------------|
| 01 | [working title] | Problem (P) | Studio | Cold |
| 02 | [working title] | Amplify (A) | Studio | Cold |
| 03 | [working title] | Solution (S) | Studio | Cold |
| 04 | [working title] | Testimony (T) | Studio | Cold |
| 05 | [working title] | Offer (O) | Studio | Warm |
| 06 | [working title] | Problem (P) — second angle | Studio | Cold |
| 07 | [working title] | Testimony (T) — second angle | Home | Cold |
| 08 | [working title] | Solution (S) — second angle | Home | Warm |
| 09 | [working title] | Amplify (A) — second angle | Home | Cold |
For any repeated PASTOR angle, the concept, hook, and emotional arc must be meaningfully different from the first use. Flag this in the plan so the user can confirm the angles are distinct before writing begins.
For fewer than 6 briefs, select the PASTOR angles that best serve the campaign objective and confirmed traffic temperature mix. Never use the same angle twice.
---
### Step 5 — Write the briefs
Write all briefs using the six-section structure from `Video_Brief_PROMPT.md > How to structure each brief`:
1. Concept
2. Hook
3. Video Length
4. How to Shoot
5. Script and Talking Points
6. Do's and Don'ts
Apply DR copywriting principles throughout. For every brief, ask:
- Does the hook open a specific loop? (Suby: pattern interrupt)
- Does the problem beat agitate — not just name — the pain? (PAS)
- Does the demo beat show the result, not just the product? (Ogilvy: show don't tell / BAB / Suby: promised land)
- Does the proof beat include a specific number or real claim? (Ogilvy: specificity)
- Does the CTA apply Hormozi's value equation — cut time, cut effort, raise believability, raise the dream?
- Does the offer pass Suby's Godfather test — irresistible, risk-reversed, urgent?
Additional rules:
- All copy in Australian English
- No em-dashes anywhere
- Script section uses talking points and beats — not word-for-word dialogue
- [MUST SAY] used only for offer terms, brand name, and verified claims
- Creator performance reminder at the top of every script
- Every cold traffic brief follows the full DR arc: Hook, Problem, Solution/Demo, Social Proof, CTA
- Social proof beat is mandatory and specific — a real number or honest claim
- Do's and Don'ts are brief-specific and brand-specific — no generic filler
- Creative references (2 to 3 examples or mood board link) in every How to Shoot
- Maximum 25 seconds, minimum 15 seconds per brief unless strategically justified
- PASTOR angles: no repeats in a 6-brief batch. In batches of 7 to 9, repeated angles are permitted if the concept, hook, and arc are meaningfully different — flag repeats in the batch plan
---
### Step 6 — Generate the .docx
Read the docx skill at `/mnt/skills/public/docx/SKILL.md` before generating any file.
Apply all formatting from `Video_Brief_PROMPT.md > Output format`:
**Colours** (extracted from client logo, or fallback if no logo provided):
```
BRAND_ACCENT = [extracted hex]   # logo mark / primary brand colour
BRAND_BG     = [extracted hex]   # logo background / secondary colour
DARK         = "1A1A1A"
WHITE        = "FFFFFF"
MID_GREY     = [warm grey derived from brand palette]
```
**Spacing constants** (tune to achieve single-page fit):
```javascript
const GAP_BEFORE_LABEL  = 360;   // space above each section label
const GAP_AFTER_HEADER  = 200;   // after pastor/traffic tag
const GAP_BODY          = 100;   // between body lines
const GAP_SCRIPT_NOTE   = 180;   // before script timing notes
const GAP_SCRIPT_LINE   = 60;    // between bullet lines in script
```
**Page structure per brief:**
- Cream header band: brief number + title + studio tag + PASTOR angle + traffic temperature
- 6 section labels (brand accent background, white caps text)
- Body text at 11pt, consistent 160 DXA indent
- Studio B-roll sequence strip (studio briefs only)
- Thin rule + offer footer in brand accent colour
---
### Step 7 — Validate layout (mandatory)
After generating the .docx:
```bash
# Convert to PDF
python3 /mnt/skills/public/docx/scripts/office/soffice.py --headless --convert-to pdf output.docx
# Render pages as images
pdftoppm -jpeg -r 120 output.pdf page
# Count pages — should be briefs + 1 cover page
ls page*.jpg | wc -l
```
Visually inspect every brief page:
- Content fills the page without large blank gaps
- No section spills onto a following page
- Footer is visible on every brief page
**If any brief overflows:**
1. Reduce `GAP_BEFORE_LABEL` by 80 DXA
2. Reduce `GAP_SCRIPT_NOTE` by 40 DXA
3. Regenerate and re-inspect
4. Repeat until all briefs are single-page
**If home briefs have excess white space:**
- Increase `GAP_BEFORE_LABEL` for those briefs only
---
### Step 8 — Validate content
```
[ ] Discovery completed across all six topic areas
[ ] Brief challenged on offer, audience, objection, visual proof, and concept duplication
[ ] No em-dashes in any brief
[ ] No duplicate PASTOR angles across the batch
[ ] All copy in Australian English
[ ] Script section uses talking points and beats — no full-sentence dialogue except [MUST SAY] items
[ ] Script arc matches the traffic temperature for each brief
[ ] Social proof beat present, specific, and includes a real number or claim in all cold traffic briefs
[ ] Creator performance reminder at top of every script
[ ] Do's and Don'ts: specific to client and brief, no generic filler
[ ] Creative references included in every How to Shoot section
[ ] Studio briefs: B-roll sequence strip present in How to Shoot
[ ] Home briefs: tagged correctly
[ ] Hook written as actual spoken dialogue, not a description
[ ] Concept is 2 to 4 sentences with a clear emotional through-line
[ ] Offer footer on every page
[ ] Landing page URL verified from actual page visit
[ ] Brand colours extracted from logo, not guessed
[ ] DR principles applied: PAS, BAB, Suby promised land, Hormozi value equation, Ogilvy specificity
```
---
### Step 9 — Deliver
```bash
cp output.docx /mnt/user-data/outputs/[client]_video_briefs_[YYYY-MM-DD].docx
cp output.pdf  /mnt/user-data/outputs/[client]_video_briefs_[YYYY-MM-DD].pdf
```
Call `present_files` with both files. Deliver the PDF first, then the .docx.
---
## Common errors and fixes
| Problem | Fix |
|---------|-----|
| Brief overflows to second page | Reduce `GAP_BEFORE_LABEL` to 280, `GAP_SCRIPT_NOTE` to 140. Regenerate. |
| Home brief has large blank gap | Increase `GAP_BEFORE_LABEL` to 480 for that brief only |
| Brand colours look wrong | Re-run PIL pixel sampling, filter out pure white, take top 2 non-white hex values |
| LibreOffice PDF conversion fails | Run `python3 scripts/office/soffice.py` directly to see error output |
| Em-dash in output | Search for `—` before writing to file. Replace with ` to ` or a comma |
| Talking point reads like a script line | Rewrite as the idea, not the delivery. Test: would a real person say this naturally without notes? |
| Problem beat feels flat | Apply PAS agitation — name the pain then make it worse before moving to solution |
| Demo beat sounds like a product description | Apply BAB and Suby's promised land — sell the result and the feeling, not the feature |
| Proof beat is vague | Replace adjectives with a specific number, a real claim, or a risk reversal |
| CTA feels weak | Apply Hormozi's value equation — cut friction, raise the dream, add real urgency |
| Two hooks feel too similar | Check PASTOR angles. If both are Problem-led, reassign one to Amplify or Testimony |
| Do's and Don'ts are generic | Pull directly from client restrictions (discovery) and the specific concept of that brief |
---
## Output checklist summary
- [ ] Discovery completed (all six topics, no strategic gaps)
- [ ] Brand research completed (landing page, reviews, FAQ, pricing)
- [ ] Brand colours extracted from logo
- [ ] Batch plan confirmed with user (titles, PASTOR angles, traffic temperatures, studio/home split)
- [ ] Challenge checks completed
- [ ] All 6 sections present in every brief
- [ ] PASTOR angles: no duplicates, correct assignments
- [ ] Studio/home split confirmed against batch plan (default: two-thirds studio, one-third home)
- [ ] Studio B-roll sequences in How to Shoot
- [ ] Creative references in How to Shoot for every brief
- [ ] Scripts in Australian English, no em-dashes
- [ ] Script arcs match traffic temperatures
- [ ] Talking points, not dialogue — [MUST SAY] used sparingly
- [ ] Social proof beat specific and mandatory in cold traffic briefs
- [ ] Do's and Don'ts brief-specific and brand-specific
- [ ] DR principles applied across all scripts
- [ ] .docx validated: cover page + one page per brief, no overflow, no blank gaps
- [ ] Both .docx and .pdf delivered via present_files
---
## Reference files
```
video-brief-creation/
├── Video_Brief_SKILL.md    (this file — execution steps and checklist)
└── Video_Brief_PROMPT.md   (strategic framework, DR principles, section rules, formatting spec)
```
Read `Video_Brief_PROMPT.md` first. It is the source of truth for what goes inside each brief. This file is the source of truth for how to execute the process.
