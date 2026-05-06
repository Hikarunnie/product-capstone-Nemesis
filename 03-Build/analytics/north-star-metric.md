# North Star Metric

**Team:** Nemesis  
**Product:** Nemesis Platform (working name)  
**Date:** April 15, 2026  
**Version:** 1.0  

---

## Our North Star Metric

Weekly successfully managed product listings per active creator

**Written out:**

> Weekly successfully managed product listings per active creator

---

## Why This Metric

**Question 1: What is the core action a user takes that proves they got value from our product?**

The core value of our product is helping handmade creators structure and manage the process of selling their products in a simple and low-stress way. The moment a user truly gets value is when they successfully create and complete a product listing with all necessary details (name, price, description). This represents both functional success (they used a structured system instead of chaos) and emotional progress (they moved from hesitation to action).

---

**Question 2: Can we measure it? Is it a discrete, countable event?**

Yes. This is a clear, countable event that occurs every time a user successfully completes and saves a product listing. In our event schema, this is tracked as:

`listing_completed`

Each time this event fires, it represents one successfully managed listing. We can count how many of these events occur per `user_id` over a 7-day period to calculate weekly usage.

---

**Question 3: Does it change when our product gets better or worse?**

Yes. If we release a poor update that makes the listing creation flow confusing or difficult, fewer users will complete listings, and this metric will drop. If we improve onboarding, simplify pricing input, or guide users through the process, more listings will be successfully completed, increasing the metric. This makes it directly sensitive to product quality.

---

## What Our NSM Is Not

| Alternative Metric | Why We Rejected It |
|-------------------|--------------------|
| Total signups | Measures acquisition, not value. Users can sign up and never create anything. |
| Products started | Measures intent, not completion. Users may start but not finish listings. |
| Messages exchanged | Could indicate confusion rather than success. More messages ≠ better experience. |
| Daily active users | Too broad. Users can be active without achieving value. |
| Likes or views | Vanity metrics. Do not represent meaningful progress or outcomes. |

---

## Connection to AARRR

- [ ] Acquisition  
- [x] Activation  
- [ ] Retention  
- [ ] Referral  
- [ ] Revenue  

**Stage:** Activation  

**Why:** The first completed product listing represents the user's "aha moment" — when they successfully use a structured system to prepare a product for selling.

---

## Connection to Prototype

**Screen name:** Listing Completion Screen  

**What the user does on that screen:** Completes and saves a product listing with all required fields  

**Event that fires:** `listing_completed`  

**How that event feeds the NSM:** Each `listing_completed` event increments the weekly completed listing count for the associated `user_id`, contributing directly to the NSM.

---

## Team Sign-Off

All team members reviewed and agreed on this NSM:

| Name | Role | Agreement |
|------|------|-----------|
| Ani Kharabadze | Tech Lead | ☑ Agreed |
| Ketevan Shavadze | Program Lead | ☑ Agreed |
| Gvantsa Nozadze | Discovery Lead | ☑ Agreed |
| Tamar Vatcharadze | Discovery Lead | ☑ Agreed |

**Date agreed:** April 10, 2026  

---

## Change Log

| Date | Change | Reason |
|------|--------|--------|
| April 10, 2026 | Initial definition | Lab 5 |

---

*North Star Metric | Nemesis | CS-PD-2026 | Spring 2026*