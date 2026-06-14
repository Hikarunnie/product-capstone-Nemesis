# Unit Economics Analysis

**Product:** Nemesis Craft Market  
**Team:** Nemesis  
**Lab:** Lab 9 -- Growth Modeling  
**Date:** 21 May 2026

---

## Monetisation Model

Nemesis Craft Market is currently free for creators to join and list. Monetisation is via a **platform commission of 8% on each completed sale.**

**Monetisable value substitute (pre-revenue):**  
Since ARPU is currently zero (platform not yet charging), we substitute monetisable value based on the following:

- Average product price on handmade marketplaces: 25 GEL (~9.25 USD). [Benchmark: Etsy median listing price for handmade items, approximately $15-$25 USD; we use the lower end to be conservative given Georgian market purchasing power parity.]
- Average sales per active creator per month: 4 transactions. [Assumption: conservative estimate based on interviews with 3 creators who sell at Tbilisi craft fairs and reported selling 3-6 items per market day; we assume 1 market-equivalent per week digital]
- Commission per transaction: 25 GEL x 8% = 2 GEL = ~0.74 USD
- **ARPU = 4 transactions x 0.74 USD = 2.96 USD per active creator per month**
  We use **3.00 USD/month** as a round conservative figure.

---

## LTV Assumptions (applied across all channels)

ARPU:                   3.00 USD/month
Gross margin:           88%
  (Hosting and infrastructure costs estimated at 12% at scale;
   currently near zero on free tier. Source: Assumption based on
   typical SaaS/marketplace infrastructure ratios.)
Average customer lifetime:  7 months
  (Assumption: creators who successfully publish and make at least
   one sale tend to stay through one academic year or selling season.
   Tbilisi craft fair season runs approximately September–April = 7 months.
   No live churn data yet. Will replace with cohort data at 60 days.)

LTV = ARPU x gross margin x lifetime in months
LTV = 3.00 x 0.88 x 7
LTV = 18.48 USD


**LTV = 18.48 USD** (used consistently across all three channels below)

---

## Channel 1: Instagram / TikTok Organic Content

### CAC Calculation


Total monthly spend:
  Team time: 3 posts/week x 4 weeks = 12 posts/month
  Estimated 1.5 hours per post (filming, editing, posting, community engagement)
  Total hours: 18 hours/month
  Notional rate: 15 GEL/hour (~5.55 USD/hour)
  Time cost: 18 x 5.55 = 99.90 USD/month
  Hard spend (none): 0 USD
  Total: ~100 USD/month

Conversion funnel:
  Post impressions to profile visit: 3%
  [Benchmark: Instagram Reels average engagement-to-profile rate ~2-5%;
   craft/handmade content benchmarks toward the higher end.
   Source: Hootsuite 2024 Instagram Benchmarks Report -- assumption,
   will replace with analytics data]

  Profile visit to app link click: 12%
  [Assumption: Instagram bio link CTR ~10-15% for niche creator accounts.
   Source: Assumption, will replace with UTM data]

  Link click to signup: 20%
  [Assumption: no live landing page data yet. Benchmark: marketplace
   landing page signup conversion 15-25%. Source: First Round Review
   consumer marketplace benchmarks -- assumption]

  Signup to listing_completed (activation): 28%
  [Assumption based on prototype usability testing sessions.
   Will replace with live event schema data once deployed.]

Estimated monthly visitors from organic: 500
  (Based on reaching 3 targeted hashtag communities with 12 posts,
   estimating ~40 profile visits per post average = 480 ≈ 500)

Signups: 500 x 20% = 100 signups/month
Activated (listing_completed): 100 x 28% = 28 creators
Retained at D30: 28 x 55% = 15 retained creators
  [D30 retention 55%. Benchmark: 40-60% for early-stage marketplaces
   with strong activation. Source: Assumption -- no cohort data yet.]

CAC = Total spend / retained users acquired
CAC = 100 USD / 15 = 6.67 USD


**CAC (Channel 1) = 6.67 USD**

### Ratios


LTV:CAC = 18.48 / 6.67 = 2.77:1


This is below the ideal 3:1 floor but above 1:1. It is acceptable at current stage given that:
1. CAC will fall as content compounds (existing posts keep generating views without additional work).
2. LTV will rise once we switch on the 8% commission and creators' sales volume increases.
3. We model LTV:CAC reaching 4:1 by Month 4 as the content library grows and CAC per retained user drops.


Payback period = CAC / (ARPU x gross margin)
Payback = 6.67 / (3.00 x 0.88)
Payback = 6.67 / 2.64
Payback = 2.5 months


**Payback period (Channel 1) = 2.5 months**



## Channel 2: Sales — Craft Fair and University Outreach

### CAC Calculation


Total monthly spend:
  Team time: 2 outreach events/week x 4 weeks = 8 events/month
  Estimated 3 hours per event (travel, time at event, follow-up messages)
  Total hours: 24 hours/month
  Notional rate: 15 GEL/hour (~5.55 USD/hour)
  Time cost: 24 x 5.55 = 133.20 USD/month
  Hard spend (transport, printed materials): ~20 USD/month
  Total: ~153 USD/month

Conversion funnel:
  Creators approached per event: 8
  [Assumption: at a typical Dry Bridge or campus market, estimate
   8 vendor/creator conversations possible per 3-hour slot]

  Total creators approached per month: 8 x 8 = 64

  Approached to signup: 35%
  [Assumption: in-person demo conversion is high given direct value
   demonstration. Benchmark: in-person B2C sales conversion 25-50%
   depending on warm vs cold approach. Source: Assumption]

  Signups: 64 x 35% = 22 signups/month

  Signup to listing_completed (activation): 45%
  [Assumption: higher than organic channel because in-person attendees
   are pre-qualified sellers who already sell handmade goods;
   intent to list is higher. Source: Assumption]

  Activated: 22 x 45% = 10 creators
  Retained at D30: 10 x 60% = 6 retained creators
  [D30 retention 60% for sales-acquired creators: higher than organic
   because in-person onboarding creates personal accountability.
   Source: Assumption]

CAC = Total spend / retained users acquired
CAC = 153 USD / 6 = 25.50 USD


**CAC (Channel 2) = 25.50 USD**

### Ratios


LTV:CAC = 18.48 / 25.50 = 0.72:1


This is below 1:1. We acknowledge this explicitly.

**Why we are still using this channel:**  
The sales channel is loss-making at current monetisation. We are using it because:
1. Supply-side creators are critical to marketplace viability. Without listings, buyers have nothing to browse. The first 50 creators are a prerequisite for any demand-side growth.
2. In-person onboarding produces creators who are more likely to publish multiple listings and stay active, increasing their individual LTV above the 18.48 USD average.
3. The path to profitability for this channel: make sales outreach partially self-serve by Month 3 (QR code at craft fairs linking to a creator signup flow), reducing time cost from 153 USD to ~40 USD/month, which gives LTV:CAC of 18.48/6.93 = 2.67:1.


Payback period = CAC / (ARPU x gross margin)
Payback = 25.50 / (3.00 x 0.88)
Payback = 25.50 / 2.64
Payback = 9.7 months


**Payback period (Channel 2) = 9.7 months**

This is high. It will improve significantly once the channel becomes partially self-serve (see above).



## Channel 3: Viral — Shareable Listing Card

### CAC Calculation


Hard spend: 0 USD (viral channel, no paid distribution)
Time cost: ~10 USD/month (feature maintenance once built)
Total: ~10 USD/month

K-factor: 0.15 (see Loops and Moats document)
  K = 0.35 shares per active creator x 43% conversion rate
  K = 0.35 x 0.43 = 0.15

Users generated per month from viral (M3 onward, base of 30 retained creators):
  30 retained creators x 0.15 = 4.5 ≈ 5 new activated users/month from viral
  Retained at D30: 5 x 55% = 3 retained creators/month

CAC = 10 USD / 3 = 3.33 USD


**CAC (Channel 3) = 3.33 USD** *(from M3 onward only; not active in M1–M2)*

### Ratios

LTV:CAC = 18.48 / 3.33 = 5.55:1


Excellent ratio. This channel validates the investment in building the shareable listing card feature.


Payback period = 3.33 / 2.64 = 1.3 months


**Payback period (Channel 3) = 1.3 months**



## Blended Unit Economics

| Channel | Monthly Spend | Retained Users/Month | CAC | LTV | LTV:CAC | Payback |
|---------|--------------|---------------------|-----|-----|---------|---------|
| Organic (Instagram/TikTok) | $100 | 15 | $6.67 | $18.48 | 2.77:1 | 2.5 mo |
| Sales (craft fair outreach) | $153 | 6 | $25.50 | $18.48 | 0.72:1 | 9.7 mo |
| Viral (listing share, M3+) | $10 | 3 | $3.33 | $18.48 | 5.55:1 | 1.3 mo |
| **Blended (M1–M2)** | **$253** | **21** | **$12.05** | **$18.48** | **1.53:1** | **4.6 mo** |
| **Blended (M3+, viral active)** | **$263** | **24** | **$10.96** | **$18.48** | **1.69:1** | **4.2 mo** |

**Blended LTV:CAC (M1–M2) = 1.53:1**

This is below the 3:1 target. The main drag is the sales channel.

**Plan to reach 3:1 by Month 4:**
1. Sales channel moves to partially self-serve (QR code sign-up at craft fairs), reducing CAC from $25.50 to approximately $7.00.
2. Viral channel activates and contributes at 5.55:1.
3. Organic content library compounds, reducing effective CAC as older posts continue generating traffic with no additional spend.
4. LTV rises as we activate the 8% commission model and creators begin making sales.

At Month 4, revised blended LTV:CAC projection: **3.2:1** [Assumption — modelled in growth projection spreadsheet].
