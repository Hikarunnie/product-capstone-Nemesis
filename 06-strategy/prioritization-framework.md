# Musa Prioritization Framework

**Team:** Nemesis  
**Product:** Musa  
**Date:** 14 June 2026  
**Purpose:** Updated prioritization framework for the Lab 6 roadmap and post-launch backlog.

## Principle

Musa prioritises evidence-producing work before feature expansion.

The order of importance is:

1. protect users and keep the core flow reliable;
2. help creators publish;
3. measure whether creators return;
4. measure whether buyers take meaningful action;
5. build transaction infrastructure only after intent is proven.

## Step 1 — Non-Negotiable Gates

A backlog item bypasses scoring and becomes **P0** when it addresses:

- security, privacy, data loss, or legal compliance;
- a broken registration, studio, listing, or public-display flow;
- severe accessibility or mobile usability failure;
- missing measurement that prevents the team from evaluating the core product;
- an incident affecting current users.

Items that fail any of the following gates are not scheduled:

| Gate | Question |
|---|---|
| Strategy | Does it support creator activation, retention, buyer intent, trust, or validated revenue? |
| Evidence | Is there interview, analytics, usability, operational, or legal evidence for the need? |
| Metric | Can success be measured with a defined event or outcome? |
| Scope | Is this the smallest version that answers the product question? |
| Capacity | Is there a clear owner and realistic effort estimate? |
| Risk | Have privacy, safety, security, and operational consequences been considered? |

## Step 2 — RICE-E Score

Musa uses an adapted RICE score with an explicit Evidence multiplier.

```text
RICE-E = (Reach × Impact × Confidence × Evidence) / Effort
```

### Scales

#### Reach: 1–5

| Score | Expected users affected in the next 60 days |
|---:|---|
| 1 | Very small subset |
| 2 | One minor segment |
| 3 | Meaningful portion of active users |
| 4 | Most creators or most buyers |
| 5 | Nearly every user or the whole core funnel |

#### Impact: 1–5

| Score | Expected effect |
|---:|---|
| 1 | Cosmetic or convenience improvement |
| 2 | Small usability improvement |
| 3 | Meaningful improvement to a supporting metric |
| 4 | Strong improvement to activation, retention, or buyer intent |
| 5 | Critical to core value or marketplace viability |

#### Confidence: 0.5–1.0

| Value | Basis |
|---:|---|
| 0.50 | Team assumption only |
| 0.65 | Weak qualitative signal |
| 0.80 | Repeated interviews or usability evidence |
| 0.90 | Strong behaviour or analytics evidence |
| 1.00 | Confirmed requirement or directly observed failure |

#### Evidence: 0.5–1.2

| Value | Evidence quality |
|---:|---|
| 0.50 | No supporting evidence |
| 0.75 | One source or indirect evidence |
| 1.00 | Multiple interviews or a clear strategic dependency |
| 1.20 | Live-user data, repeated behaviour, or legal/security requirement |

#### Effort

Estimated person-weeks for design, development, testing, documentation, and operational setup.

## Step 3 — Current Backlog Scoring

Scores are planning estimates and must be recalculated after analytics data and technical discovery.

| Rank | Item | Reach | Impact | Confidence | Evidence | Effort | RICE-E |
|---:|---|---:|---:|---:|---:|---:|---:|
| 1 | Core analytics instrumentation | 5 | 5 | 0.90 | 1.20 | 1.0 | **27.00** |
| 2 | Simplify creator onboarding and first listing | 4 | 5 | 0.85 | 1.20 | 1.5 | **13.60** |
| 3 | Shareable listing card and referral tracking | 4 | 4 | 0.80 | 1.00 | 1.0 | **12.80** |
| 4 | Lightweight buyer inquiry / order request | 5 | 5 | 0.75 | 1.00 | 2.0 | **9.38** |
| 5 | Search and category filters | 4 | 3 | 0.80 | 1.00 | 1.5 | **6.40** |
| 6 | Edit, archive, and availability controls | 3 | 4 | 0.80 | 1.00 | 2.0 | **4.80** |
| 7 | Creator profiles and trust information | 3 | 4 | 0.70 | 1.00 | 2.0 | **4.20** |
| 8 | Verified-interaction reviews | 3 | 4 | 0.65 | 0.75 | 2.5 | **2.34** |
| 9 | Payment integration | 3 | 5 | 0.50 | 0.75 | 5.0 | **1.13** |
| 10 | AI product-description generator | 2 | 2 | 0.50 | 0.50 | 2.0 | **0.50** |
| 11 | Delivery integration | 2 | 4 | 0.40 | 0.50 | 4.0 | **0.40** |
| 12 | Native mobile applications | 2 | 2 | 0.40 | 0.50 | 8.0 | **0.10** |

## Priority Classes

| Class | Meaning | Working rule |
|---|---|---|
| P0 | User protection or broken core journey | Start immediately; may bypass score |
| P1 | Highest evidence-backed product outcome | Commit within the current 30-day horizon |
| P2 | Valuable after P1 or dependent on new evidence | Keep in “Next” |
| P3 | Hypothesis with weak evidence or high effort | Experiment first or defer |
| Rejected | Conflicts with strategy or creates distraction | Document why it is not being built |

### Current classification

- **P0:** core-flow defects, privacy/security issues, data loss, missing critical analytics.
- **P1:** onboarding simplification, share card, buyer inquiry flow, search basics.
- **P2:** creator profiles, listing controls, trust pilot, creator insights.
- **P3:** payments, delivery, advanced reviews, AI assistance.
- **Rejected for current horizon:** native apps, auctions, social feed, complex themes, multiple paid plans.

## Step 4 — Dependency and Sequence Check

A high score does not ignore dependencies.

| Feature | Must happen first |
|---|---|
| Creator retention analysis | Reliable identity and event tracking |
| Share loop | Public listing URLs and referral attribution |
| Reviews | Verified interaction or order evidence |
| Payment integration | Purchase intent, legal model, refund process, creator payout model |
| Delivery integration | Confirmed order flow and provider discovery |
| Commission model | Verified transactions and accepted creator economics |

## Step 5 — Review Cadence

The team holds a biweekly prioritization review.

For each item:

1. update reach from current active-user data;
2. replace assumptions with interviews or event evidence;
3. revise effort after technical discovery;
4. review dependencies and risks;
5. select only the work that fits team capacity;
6. record rejected items and the reason.

## Feature Request Template

```markdown
### Feature / experiment

**User problem:**  
**Evidence:**  
**Target segment:**  
**Expected metric movement:**  
**Smallest test:**  
**Reach:**  
**Impact:**  
**Confidence:**  
**Evidence multiplier:**  
**Effort:**  
**RICE-E score:**  
**Dependencies:**  
**Privacy / security / operational risk:**  
**Decision:** P0 / P1 / P2 / P3 / Rejected
```

## Anti-Feature-Creep Rules

Musa will not prioritise a feature because:

- a competitor has it;
- it looks impressive in a demo;
- it uses fashionable technology;
- one team member personally prefers it;
- it increases scope without testing a strategic assumption.

The framework is successful when the roadmap contains fewer items, clearer evidence, and measurable decision points.
