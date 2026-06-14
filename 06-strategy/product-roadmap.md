# Musa Product Roadmap

**Team:** Nemesis  
**Product:** Musa  
**Date:** 14 June 2026  
**Source:** Updated from the Lab 6 roadmap in `03-Build/roadmap/product-roadmap.md`

## Product Goal

Musa helps aspiring and early-stage Georgian handmade creators move from hesitation or scattered social-media selling to a structured public studio.

The roadmap prioritises one outcome:

> A creator publishes a product, returns to maintain the studio, and receives meaningful buyer interest.

## North Star and Supporting Metrics

### North Star Metric

**Completed product listings per activated creator during the creator’s first seven days.**

### Activation Event

`listing_completed`: a creator successfully publishes a product that becomes visible in their studio and the marketplace.

### Supporting Metrics

| Metric | Definition | Decision supported |
|---|---|---|
| Studio activation rate | Percentage of registered creators who create a studio | Whether onboarding reaches the creator journey |
| First-listing completion rate | Percentage of creators who start and publish a listing | Whether the core flow is understandable |
| Time to first listing | Time between registration and first publication | Whether Musa is genuinely low-friction |
| Second-listing rate | Percentage publishing another listing within 30 days | Whether value continues after first activation |
| Creator return rate | Activated creators returning within 7 and 30 days | Retention |
| Product-to-inquiry rate | Percentage of product views producing an inquiry | Buyer intent |
| Share referral rate | Visits and activated creators from shared listing links | Organic loop |
| Completed-sale rate | Inquiries becoming verified sales | Business model evidence, after order flow exists |

## Original Lab 6 Sprint Arc

The original roadmap ran from 24 April to 11 June 2026 and focused on creator activation.

| Sprint | Dates | Original theme | Main outcome |
|---|---|---|---|
| Sprint 1 | 24 Apr–7 May | Foundation | Marketplace navigation, product cards, studio entry, create-listing entry point |
| Sprint 2 | 8–21 May | Activation and instrumentation | Listing form, publishing, persistence, analytics events |
| Sprint 3 | 22 May–4 Jun | Creator management and marketplace improvement | Listing management, search/filter concepts, usability testing |
| Sprint 4 | 5–11 Jun | Demo readiness | Stability, documentation, pitch, live demonstration |

## Confirmed MVP Outcome

By 11 June 2026, the live product had:

- 337 visits;
- 4 registered studios;
- 8 live product listings;
- a public deployment at `https://musa-front.pages.dev/`.

The next roadmap moves from proving that publication is possible to proving repeated creator and buyer value.

## Now / Next / Later

| Horizon | Product objective | Included | Excluded |
|---|---|---|---|
| **Now: 0–30 days** | Reliable activation and measurable buyer intent | Core-flow fixes, analytics, simplified onboarding, share cards, inquiries, search basics | Full payments, delivery integration, advanced customization |
| **Next: 31–60 days** | Creator retention and marketplace trust | Profiles, listing management, trust signals, verified-interaction reviews, creator insights | Complex subscriptions, recommendation AI, international logistics |
| **Later: 3–6 months** | Transaction validation and local network growth | Payment pilot, order states, delivery pilot, commission, category expansion | Native apps and broad international expansion until local fit is proven |

# Phase 1 — Reliability and Measurement

**Dates:** 15–28 June 2026  
**Goal:** Every creator can complete the studio-to-listing journey, and the team can observe each funnel step.

## Deliverables

| Priority | Deliverable | Success criterion |
|---|---|---|
| P0 | Audit authentication, studio creation, image upload, publishing, and public display | No critical break in five complete test journeys |
| P0 | Instrument creator and buyer events | Events visible with user/session identifiers and timestamps |
| P0 | Add privacy notice link and basic account deletion request path | Legal files are reachable from the product |
| P1 | Reduce first-listing form to essential fields | Median completion time under 5 minutes in tests |
| P1 | Add clear empty states and success confirmation | Test users know what to do next without explanation |
| P1 | Add basic search and category filters | Buyers can narrow the Explore feed |
| P2 | Improve mobile accessibility and loading feedback | No blocking usability issue on common phone widths |

## Events

- `creator_signed_up`
- `studio_created`
- `listing_started`
- `listing_form_completed`
- `listing_completed`
- `product_viewed`
- `studio_viewed`
- `listing_shared`
- `inquiry_started`
- `inquiry_completed`

## Exit Criteria

- Five creators complete the full flow without team intervention.
- Event data distinguishes drop-off at each stage.
- Critical security and privacy checklist items are resolved.

# Phase 2 — Buyer Intent and Sharing

**Dates:** 29 June–12 July 2026  
**Goal:** Connect public discovery to measurable customer action.

## Deliverables

| Priority | Deliverable | Success criterion |
|---|---|---|
| P0 | Lightweight inquiry / order-request button | Buyer can contact a creator with product context attached |
| P0 | Inquiry status for creator: New, Responded, Closed | Creator can avoid losing the request in unrelated DMs |
| P1 | Shareable listing card and copied public link | At least 30% of active creators share one listing |
| P1 | Referral-source tracking | Shared-link traffic is measurable |
| P1 | Improved product detail page | Price, creator, availability, description, and CTA are clear |
| P2 | Saved or favourite products | Tested only if buyer interviews show repeated browsing need |

## Exit Criteria

- At least 20 active creators and 40 live listings.
- At least 10 qualified product inquiries.
- Share-source traffic is visible in analytics.

# Phase 3 — Trust and Creator Retention

**Dates:** 13–26 July 2026  
**Goal:** Give creators reasons to return and buyers reasons to trust.

## Deliverables

| Priority | Deliverable | Success criterion |
|---|---|---|
| P0 | Edit, archive, and availability controls for listings | Creators can maintain accurate inventory |
| P0 | Creator profile with location, story, and contact preferences | Buyers understand who made the product |
| P1 | Reporting and moderation workflow | Unsafe or misleading content can be reviewed |
| P1 | Review pilot limited to verified interactions | Reviews cannot be added anonymously without interaction evidence |
| P1 | Simple creator dashboard | Views, inquiries, and top listings are visible |
| P2 | Listing quality prompts | Better photos and descriptions without mandatory complexity |

## Exit Criteria

- At least 40% of activated creators publish a second listing.
- At least 50% return within 30 days.
- Buyer interviews show improved trust compared with DM-only pages.

# Phase 4 — Local Ecosystem Pilot

**Dates:** 27 July–13 August 2026  
**Goal:** Validate whether Musa should become a transaction marketplace.

## Deliverables

| Priority | Deliverable | Success criterion |
|---|---|---|
| P0 | Map payment, refund, tax, and payout requirements | Written decision on feasible payment model |
| P0 | Interview at least two payment and two delivery providers | Integration and operational constraints documented |
| P1 | Run one creator-community or craft-event onboarding pilot | Ten creators start the flow; five publish |
| P1 | Test one manually supported order-and-delivery journey | Operational failure points documented |
| P2 | Commission simulation | Creators understand and react to the proposed 8% fee |

## Exit Criteria

A payment build moves forward only when:

- buyer inquiries regularly become agreed purchases;
- creators accept the fee model;
- support, refunds, and delivery ownership are defined;
- the team has capacity to operate the workflow safely.

# Later Roadmap — 3 to 6 Months

## Candidate Outcomes

1. **Transaction MVP**
   - local payment method;
   - order states;
   - creator payout records;
   - cancellations and refunds;
   - 8% commission tracking.

2. **Delivery pilot**
   - creator-arranged delivery first;
   - optional courier partner;
   - tracking link or status;
   - delivery-cost clarity.

3. **Marketplace trust**
   - verified creators;
   - verified-purchase reviews;
   - policies and reporting;
   - response and fulfilment indicators.

4. **Network growth**
   - creator referral programme;
   - category landing pages;
   - Georgian-language SEO;
   - craft fair and university partnerships.

5. **Creator retention**
   - repeat-listing reminders;
   - listing performance;
   - returning-buyer signals;
   - lightweight inventory management.

## Explicitly Deferred

- native iOS and Android apps;
- AI-generated descriptions as a headline feature;
- complex storefront themes;
- auctions;
- advanced subscriptions;
- international shipping;
- broad categories outside handmade products;
- social feed features unrelated to publishing or buying.

## Roadmap Governance

The team reviews the roadmap every two weeks.

A feature moves into active development only when:

1. it supports activation, retention, buyer intent, trust, or verified revenue;
2. a metric and success threshold are defined;
3. the dependency and owner are clear;
4. privacy, security, and operational consequences are reviewed;
5. a smaller experiment cannot answer the same question faster.

## Roadmap Decision Rule

Musa should continue toward a full marketplace only if the next 60 days show:

- repeat creator publishing;
- growing qualified buyer actions;
- better retention among creators who receive buyer activity;
- credible payment and delivery operations.

If creator workflow value is strong but buyer liquidity remains weak, Musa should narrow toward a creator storefront and inquiry-management product rather than forcing a two-sided marketplace model.
