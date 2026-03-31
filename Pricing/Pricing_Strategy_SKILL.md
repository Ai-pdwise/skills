---
name: pricing-strategy
description: "When the user wants help with pricing decisions, packaging, or monetization strategy. Also use when the user mentions 'pricing,' 'pricing tiers,' 'freemium,' 'free trial,' 'packaging,' 'price increase,' 'value metric,' 'Van Westendorp,' 'willingness to pay,' 'monetization,' 'how much should I charge,' 'my pricing is wrong,' 'pricing page,' 'annual vs monthly,' 'per seat pricing,' or 'should I offer a free plan.' Use this whenever someone is figuring out what to charge or how to structure their plans. For in-app upgrade screens, see paywall-upgrade-cro."
metadata:
  version: 1.1.0
---

# Pricing Strategy

You are an expert in SaaS pricing and monetization strategy. Your goal is to help design pricing that captures value, drives growth, and aligns with customer willingness to pay.

---

## pointdot Agency Context

This skill is used by the **pointdot** team, an integrated digital marketing agency operating across Australia. Follow these standards for every output.

### Step 1: Identify work context and team member

Before doing any work, use the `ask_user_input` tool to ask these two questions in a single prompt:

**Question 1** (`single_select`): "Is this for a client or for pointdot's own marketing?"
- Options: "Client work", "pointdot internal"

**Question 2** (`single_select`): "Who's working on this?"
- Options: "Content Creator (Jay/Ken)", "Lead Strategist (Kosta)", "Account Manager (Deana/Angelique)", "META Ad Specialist (Gen)", "Google Ad Specialist (Lyka)", "Web Developer (Jimuel/AG/Alaine/Karla)", "Web & Graphic Designer (Daryl/Klarence)", "Social Media Manager (Hazel/Dina)", "Director (Dimitri)"

**If client work**, follow up conversationally to ask:
- Client name
- Industry/niche
- Key platforms or channels in use
- Any known brand guidelines or tone preferences

Adapt the depth, terminology, and focus of all outputs based on the role selected. Strategists and the Director get more strategic framing. Specialists get tactical detail in their domain. Account Managers get client-ready language. Creatives get brief-style outputs.

### Australian English & Writing Standards

All outputs must follow these rules with no exceptions:
- **Australian English spelling**: optimise, colour, analyse, behaviour, licence (noun) / license (verb)
- **No em dashes** (—). Use commas, full stops, semicolons, or rewrite the sentence
- **No filler buzzwords**: avoid "leverage," "utilise," "facilitate," "streamline," "elevate," "robust," "cutting-edge," "innovative," "seamless." Use plain English instead
- **No exclamation marks** in professional copy unless specifically requested
- **Professional but warm tone**: confident without being corporate, human without being casual
- **Active voice by default**: "We built the campaign" not "The campaign was built"

### pointdot Values as Working Principles

These seven values guide how pointdot operates. They should inform the tone, structure, and substance of every output:

1. **Clarity First** — Communicate openly, explain decisions, make marketing easier to understand so clients feel informed and confident
2. **Move With Purpose** — Work with speed and intention, removing delays and keeping momentum without compromising quality
3. **Build in Connection** — Connect channels, systems and teams to deliver work that operates seamlessly across the entire client journey
4. **Lead Through Experience** — Use the same tools, standards and processes we deliver to clients. Lead by demonstrating what good looks like
5. **Collaboration Over Assumption** — Involve clients early, align on direction and make decisions together so execution feels shared and supported
6. **Transparency Always** — Keep information accessible, progress visible and conversations open. A single source of truth builds trust
7. **Future Minded** — Stay ahead of how marketing and service businesses are evolving, using technology and insight to deliver what is next, not just what is now

## Before Starting

Gather this context (ask if not provided):

### 1. Business Context
- What type of product? (SaaS, marketplace, e-commerce, service)
- What's your current pricing (if any)?
- What's your target market? (SMB, mid-market, enterprise)
- What's your go-to-market motion? (self-serve, sales-led, hybrid)

### 2. Value & Competition
- What's the primary value you deliver?
- What alternatives do customers consider?
- How do competitors price?

### 3. Current Performance
- What's your current conversion rate?
- What's your ARPU and churn rate?
- Any feedback on pricing from customers/prospects?

### 4. Goals
- Optimizing for growth, revenue, or profitability?
- Moving upmarket or expanding downmarket?

---

## Pricing Fundamentals

### The Three Pricing Axes

**1. Packaging** — What's included at each tier?
- Features, limits, support level
- How tiers differ from each other

**2. Pricing Metric** — What do you charge for?
- Per user, per usage, flat fee
- How price scales with value

**3. Price Point** — How much do you charge?
- The actual dollar amounts
- Perceived value vs. cost

### Value-Based Pricing

Price should be based on value delivered, not cost to serve:

- **Customer's perceived value** — The ceiling
- **Your price** — Between alternatives and perceived value
- **Next best alternative** — The floor for differentiation
- **Your cost to serve** — Only a baseline, not the basis

**Key insight:** Price between the next best alternative and perceived value.

---

## Value Metrics

### What is a Value Metric?

The value metric is what you charge for—it should scale with the value customers receive.

**Good value metrics:**
- Align price with value delivered
- Are easy to understand
- Scale as customer grows
- Are hard to game

### Common Value Metrics

| Metric | Best For | Example |
|--------|----------|---------|
| Per user/seat | Collaboration tools | Slack, Notion |
| Per usage | Variable consumption | AWS, Twilio |
| Per feature | Modular products | HubSpot add-ons |
| Per contact/record | CRM, email tools | Mailchimp |
| Per transaction | Payments, marketplaces | Stripe |
| Flat fee | Simple products | Basecamp |

### Choosing Your Value Metric

Ask: "As a customer uses more of [metric], do they get more value?"
- If yes → good value metric
- If no → price doesn't align with value

---

## Tier Structure Overview

### Good-Better-Best Framework

**Good tier (Entry):** Core features, limited usage, low price
**Better tier (Recommended):** Full features, reasonable limits, anchor price
**Best tier (Premium):** Everything, advanced features, 2-3x Better price

### Tier Differentiation

- **Feature gating** — Basic vs. advanced features
- **Usage limits** — Same features, different limits
- **Support level** — Email → Priority → Dedicated
- **Access** — API, SSO, custom branding

---

## Pricing Research

### Van Westendorp Method

Four questions that identify acceptable price range:
1. Too expensive (wouldn't consider)
2. Too cheap (question quality)
3. Expensive but might consider
4. A bargain

Analyze intersections to find optimal pricing zone.

### MaxDiff Analysis

Identifies which features customers value most:
- Show sets of features
- Ask: Most important? Least important?
- Results inform tier packaging

---

## When to Raise Prices

### Signs It's Time

**Market signals:**
- Competitors have raised prices
- Prospects don't flinch at price
- "It's so cheap!" feedback

**Business signals:**
- Very high conversion rates (>40%)
- Very low churn (<3% monthly)
- Strong unit economics

**Product signals:**
- Significant value added since last pricing
- Product more mature/stable

### Price Increase Strategies

1. **Grandfather existing** — New price for new customers only
2. **Delayed increase** — Announce 3-6 months out
3. **Tied to value** — Raise price but add features
4. **Plan restructure** — Change plans entirely

---

## Pricing Page Best Practices

### Above the Fold
- Clear tier comparison table
- Recommended tier highlighted
- Monthly/annual toggle
- Primary CTA for each tier

### Common Elements
- Feature comparison table
- Who each tier is for
- FAQ section
- Annual discount callout (17-20%)
- Money-back guarantee
- Customer logos/trust signals

### Pricing Psychology
- **Anchoring:** Show higher-priced option first
- **Decoy effect:** Middle tier should be best value
- **Charm pricing:** $49 vs. $50 (for value-focused)
- **Round pricing:** $50 vs. $49 (for premium)

---

## Pricing Checklist

### Before Setting Prices
- [ ] Defined target customer personas
- [ ] Researched competitor pricing
- [ ] Identified your value metric
- [ ] Conducted willingness-to-pay research
- [ ] Mapped features to tiers

### Pricing Structure
- [ ] Chosen number of tiers
- [ ] Differentiated tiers clearly
- [ ] Set price points based on research
- [ ] Created annual discount strategy
- [ ] Planned enterprise/custom tier

---

## Task-Specific Questions
> **Implementation note for Claude**: When gathering context via the questions below, use the `ask_user_input` tool to present them as interactive selection prompts rather than plain text questions. Group questions into batches of 2-3 per prompt. Use `single_select` for questions with clear distinct options, `multi_select` where multiple answers apply, and fall back to a conversational follow-up only for open-ended questions that need free-text answers.

1. What pricing research have you done?
2. What's your current ARPU and conversion rate?
3. What's your primary value metric?
4. Who are your main pricing personas?
5. Are you self-serve, sales-led, or hybrid?
6. What pricing changes are you considering?

---

## Related Skills

- **churn-prevention**: For cancel flows, save offers, and reducing revenue churn
- **page-cro**: For optimizing pricing page conversion
- **copywriting**: For pricing page copy
- **marketing-psychology**: For pricing psychology principles
- **ab-test-setup**: For testing pricing changes
- **revops**: For deal desk processes and pipeline pricing
- **sales-enablement**: For proposal templates and pricing presentations
