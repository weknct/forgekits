---
name: ab-variant-generator
description: Use when you need to A/B test marketing copy — generate 3-5 angle-varied variants of any headline, email subject line, ad, CTA, or landing-page section, with tone/industry adaptation and a testing protocol to decide the winner.
---

# Skill: Split Test Lab — A/B Variant Generator

## AI-Native Capability

## Purpose
Generate multiple variants of any marketing asset — headlines, emails, ads, CTAs, landing page sections — so users can test and optimize for maximum conversion. Applies to every content-producing agent and skill in the system.

## When to Use
- After any agent/skill produces a draft, generate test variants
- Want to test different angles, tones, or hooks for the same message
- Need headline alternatives for a landing page or ad
- Want email subject line variants for open rate testing
- Optimizing any element of the Client Attraction Engine pipeline

## Core Principle
The best marketers don't guess — they test. Every piece of marketing content has multiple possible versions, and the difference between a 2% conversion rate and a 5% conversion rate often comes down to a single headline, subject line, or CTA. AI makes it trivial to generate variants; your job is to test them with real traffic and let the data decide.

---

## Variant Generation Framework

### What to Test (In Priority Order)

| Element | Impact Level | Why |
|---------|-------------|-----|
| **Headlines** | Highest | The headline is the first thing people see — it determines whether they read anything else |
| **Email subject lines** | Highest | Determines whether the email gets opened at all |
| **CTAs (buttons, links)** | High | The moment of conversion — small wording changes = big result changes |
| **Opening sentences** | High | Determines whether they keep reading after the headline hooks them |
| **Ad copy** | High | Directly tied to cost per click and cost per lead |
| **Social proof placement** | Medium | Where and how testimonials/numbers appear affects trust |
| **Value proposition framing** | Medium | Different angles resonate with different segments |
| **Visual elements** | Medium | Images, colors, layout (requires design testing, not just copy) |
| **Email body content** | Lower | Usually less impactful than subject line — optimize subject first |
| **Long-form copy** | Lower | Test headlines and CTAs before rewriting entire pages |

### The 5 Variation Angles

When generating variants, rotate through these angles:

| Angle | Approach | Example (Financial Planner) |
|-------|---------|---------------------------|
| **Benefit-Led** | Lead with the positive outcome | "Retire 5 Years Earlier with This Tax Strategy" |
| **Pain-Led** | Lead with the problem/consequence | "The Tax Mistake That Costs Professionals $47K" |
| **Curiosity-Led** | Create an information gap | "Why Smart Professionals Are Changing Their Tax Strategy in 2026" |
| **Social Proof-Led** | Lead with what others have done | "500+ Professionals Use This Tax Strategy — Here's Why" |
| **Direct/Urgency-Led** | Lead with a clear, urgent CTA | "Download Your Free Tax Strategy Guide Before April 15" |

---

## How to Use This Skill

### With Any Agent Output

After any agent produces a draft, say:

```
"Generate A/B variants for [element] using the Split Test Lab skill."
```

The skill will produce 3-5 variants for the specified element, each using a different angle.

### Variant Output Format

For each element being tested, deliver:

```markdown
## A/B Variants: [Element Name]

### Original (Control)
[The original version from the agent output]

### Variant A — [Angle Used]
[Alternative version]
Rationale: [Why this might outperform — what psychological trigger it uses]

### Variant B — [Angle Used]
[Alternative version]
Rationale: [Why this might outperform]

### Variant C — [Angle Used]
[Alternative version]
Rationale: [Why this might outperform]

### Testing Recommendation
- Test [which variants] first
- Minimum sample size: [number] impressions/opens/visitors per variant
- Decision criteria: [metric] improvement of [X]% with [confidence level]
```

---

## Testing Protocols

### Email Subject Line Testing
- **Method**: Most email platforms (ConvertKit, Mailchimp, ActiveCampaign) have built-in A/B testing
- **Sample**: Send variant A to 15% of list, variant B to 15%, winner to remaining 70%
- **Wait time**: 2-4 hours before declaring winner
- **Key metric**: Open rate

### Landing Page Headline Testing
- **Method**: Google Optimize (free), Unbounce, or VWO
- **Sample**: 50/50 split of incoming traffic
- **Minimum duration**: 2 weeks or 100 conversions per variant (whichever comes first)
- **Key metric**: Opt-in conversion rate

### Ad Copy Testing
- **Method**: Run 2-3 ad variants simultaneously in the same ad group
- **Sample**: Let each variant accumulate 50+ clicks
- **Key metric**: CTR + cost per lead (not just clicks — track through to conversion)
- **Budget**: Split evenly until data is significant, then allocate 80% to winner

### CTA Button Testing
- **Method**: Landing page A/B test tool
- **What to test**: Button text, color, size, placement
- **Sample**: 100+ clicks per variant
- **Key metric**: Click-through rate on the button

---

## Tone & Voice Customization

In addition to angle variants, generate tone variants when the target audience may respond differently to communication style:

| Tone | When to Use | Example |
|------|------------|---------|
| **Professional / Authoritative** | B2B, legal, financial, medical | "Strategic tax planning for equity compensation" |
| **Conversational / Friendly** | Coaches, consultants, local businesses | "Let's figure out how to keep more of your money" |
| **Urgent / Direct** | Time-sensitive offers, competitive markets | "Your competitors already know this. Do you?" |
| **Empathetic / Warm** | Health, wellness, personal services | "I know how overwhelming tax season feels. Here's help." |
| **Playful / Bold** | Creative industries, younger demographics | "Taxes are boring. Saving $47K isn't. Let's talk." |

---

## Industry-Specific Variant Packs

When generating variants, adapt language and angles for the industry:

### Professional Services (Law, Accounting, Consulting)
- Emphasize: credibility, precision, risk mitigation, ROI
- Avoid: hype, exaggeration, casual language
- Proof types: case studies with metrics, client logos, credential citations

### Health & Wellness (Chiropractors, Trainers, Therapists)
- Emphasize: transformation stories, pain relief, quality of life
- Avoid: medical claims, guaranteed outcomes
- Proof types: before/after stories, testimonials, practitioner credentials

### Creative & Marketing (Designers, Agencies, Freelancers)
- Emphasize: results, portfolio examples, process efficiency
- Avoid: generic "we're creative" language
- Proof types: visual examples, client results, campaign metrics

### Technology & SaaS
- Emphasize: efficiency, integration, scalability, time savings
- Avoid: jargon without explanation, feature lists without benefits
- Proof types: usage statistics, comparison charts, customer quotes

### Local / Brick-and-Mortar
- Emphasize: community, convenience, personal touch, local knowledge
- Avoid: corporate tone, national-scale language
- Proof types: local testimonials, Google reviews, community involvement

---

## Output Format

When invoked, produce:
1. **3-5 Variants** for each specified element
2. **Angle Label** for each variant (benefit, pain, curiosity, social proof, urgency)
3. **Rationale** for why each variant might outperform
4. **Testing Protocol**: How to run the test (tool, sample size, duration, metric)
5. **Tone Recommendation**: Which tone suits the niche best
6. **Industry Adaptation**: Adjustments for the specific vertical
7. **Winner Evaluation Criteria**: How to decide which variant wins
