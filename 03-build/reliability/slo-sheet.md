# Musa SLO Sheet

**Team:** Nemesis
**Product:** Musa
**Document:** Reliability SLO Sheet
**Date:** 14 June 2026

---

## 1. Purpose

This document defines Musa’s first reliability targets for the MVP. Musa is a handmade marketplace and storefront product where creators publish products and buyers browse, view, favourite, and add products to cart.

Because Musa is an early-stage MVP, the reliability goals focus on the most important user-facing flows:

1. The live product should load successfully.
2. Product browsing and API-backed actions should work without frequent errors.

---

## 2. Reliability Scope

The SLOs apply to the deployed Musa product:

| System area        | Deployment                               |
| ------------------ | ---------------------------------------- |
| Frontend           | Cloudflare Pages                         |
| Backend API        | Render                                   |
| Database           | Render PostgreSQL                        |
| Analytics evidence | Cloudflare dashboard / account analytics |

---

## 3. Key User Journeys Covered

| Journey                                     | Why it matters                              |
| ------------------------------------------- | ------------------------------------------- |
| Visitor opens live product                  | First impression and demo-day critical path |
| Buyer browses products                      | Core marketplace discovery flow             |
| Buyer opens product detail                  | Core product interest flow                  |
| Creator logs in and manages studio/products | Core seller value proposition               |
| User interacts with favourites/cart         | Buyer intent and future order flow          |

---

## 4. Service Level Indicators

## SLI 1 — Product Availability

**Definition:**
Percentage of successful attempts to load the live Musa frontend.

**Measurement method:**
Manual checks and platform availability checks from Cloudflare Pages. A successful check means the live product URL loads without a 404, 5xx error, or deployment failure.

**Formula:**

```txt
Availability = successful product load checks / total product load checks × 100
```

**Example measurement:**

```txt
If Musa loads successfully 98 times out of 100 checks:

Availability = 98 / 100 × 100 = 98%
```

**User impact:**
If this SLI fails, users cannot access Musa at all.

---

## SLI 2 — API Success Rate

**Definition:**
Percentage of successful backend API requests for core product flows.

**Included API areas:**

- Authentication
- Current user profile
- Studio creation/retrieval
- Product listing retrieval
- Product detail retrieval
- Product create/update/delete
- Favourites/cart/order-related endpoints

**Measurement method:**
Manual API testing, browser testing, backend logs, and Render logs. A successful API request is one that returns an expected 2xx or valid handled 4xx response. Unexpected 5xx errors count as failures.

**Formula:**

```txt
API success rate = successful API requests / total API requests × 100
```

**Example measurement:**

```txt
If 190 out of 200 core API requests succeed:

API success rate = 190 / 200 × 100 = 95%
```

**User impact:**
If this SLI fails, users may see broken product lists, failed logins, failed studio actions, or broken cart/favourite actions.

---

## SLI 3 — Product Page Load Performance

**Definition:**
Percentage of product-facing pages that load within an acceptable MVP time window.

**Included pages:**

- Homepage / landing page
- Explore page
- Product detail page
- Studio page
- Create listing page

**Measurement method:**
Manual browser testing and Cloudflare/Chrome DevTools observations. A page is considered successful if the visible page content loads in **3 seconds or less** on a normal connection.

**Formula:**

```txt
Performance success rate = pages loaded within 3 seconds / total measured page loads × 100
```

**Example measurement:**

```txt
If 45 out of 50 page loads finish within 3 seconds:

Performance success rate = 45 / 50 × 100 = 90%
```

**User impact:**
If this SLI fails, users may leave before browsing or creating listings.

---

## 5. Service Level Objectives

| SLO ID | SLO                           |                                              Target | Time window | Reason                                                                 |
| ------ | ----------------------------- | --------------------------------------------------: | ----------- | ---------------------------------------------------------------------- |
| SLO 1  | Product availability          |                   99% successful live product loads | 30 days     | The live product must reliably open for demos, users, and reviewers    |
| SLO 2  | API success rate              |                    95% successful core API requests | 30 days     | Core user flows should work most of the time during MVP                |
| SLO 3  | Product page load performance | 90% of measured product pages load within 3 seconds | 30 days     | Early users should not experience a slow or confusing first impression |

---

## 6. Severity Definitions

## SEV1 — Critical Outage

**Definition:**
Musa is unavailable or a critical user flow is completely broken.

**Examples:**

- Live product URL does not load.
- Frontend deployment returns 404 or 5xx.
- Backend API is down and product/studio pages cannot load.
- Login is completely broken for all users.
- Product listing flow is unavailable for all creators.

**Target response:**
Investigate immediately. Stop feature work until service is restored.

---

## SEV2 — Major Degradation

**Definition:**
Important functionality works only partially or fails for a significant group of users.

**Examples:**

- Some product pages fail to load.
- Product creation fails for some creators.
- Cart/favourites fail repeatedly.
- API returns intermittent 5xx errors.
- Page load times are consistently above 3 seconds.

**Target response:**
Investigate the same day. Prioritize a fix before non-critical product improvements.

---

## SEV3 — Minor Issue

**Definition:**
A non-critical bug or reliability issue exists, but users can still complete the main flows.

**Examples:**

- One product image fails to display.
- A non-critical page has slow loading.
- A minor UI issue causes confusion but not full failure.
- Analytics dashboard has delayed updates.
- A single edge-case API request fails but the main flow works.

**Target response:**
Track and fix in the next planned development cycle.

---

## 7. Monitoring and Review

| Source                       | What it helps monitor                       |
| ---------------------------- | ------------------------------------------- |
| Cloudflare Pages dashboard   | Frontend availability, requests, page views |
| Render dashboard/logs        | Backend availability and API errors         |
| Browser testing              | Product page load and UI behavior           |
| Manual API testing           | Endpoint success and error behavior         |
| GitHub issues/commit history | Reliability fixes and follow-up actions     |

---

## 8. Review Cadence

During the MVP stage, the team reviews reliability signals weekly or after any major deployment.

A review should happen immediately after:

- A failed deployment
- A frontend route returning 404
- Backend API returning repeated 5xx errors
- Database connection errors
- Login or product publishing failures
- Demo-day or public testing issues

---

## 9. Final SLO Summary

| SLO                   |              Target | Time window | Severity if broken                   |
| --------------------- | ------------------: | ----------- | ------------------------------------ |
| Product availability  |                 99% | 30 days     | SEV1 if product does not load        |
| API success rate      |                 95% | 30 days     | SEV1/SEV2 depending on affected flow |
| Page load performance | 90% under 3 seconds | 30 days     | SEV2 if persistent, SEV3 if isolated |

These SLOs are intentionally simple and measurable for an MVP-stage product.
