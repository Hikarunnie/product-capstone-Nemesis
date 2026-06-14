# Musa Error Budget

**Team:** Nemesis
**Product:** Musa
**Document:** Error Budget Policy
**Date:** 14 June 2026

---

## 1. Purpose

This document calculates Musa’s error budgets based on the SLOs defined in `slo-sheet.md`.

An error budget is the amount of unreliability the product can tolerate during a time window before the team must stop normal feature work and focus on reliability.

---

## 2. SLOs Used for Error Budget

| SLO ID | SLO                           |                                      Target | Time window |
| ------ | ----------------------------- | ------------------------------------------: | ----------- |
| SLO 1  | Product availability          |           99% successful live product loads | 30 days     |
| SLO 2  | API success rate              |            95% successful core API requests | 30 days     |
| SLO 3  | Product page load performance | 90% of measured page loads within 3 seconds | 30 days     |

---

## 3. Error Budget Formula

```txt
Error budget percentage = 100% - SLO target percentage
```

For count-based measurements:

```txt
Allowed failures = total measured events × error budget percentage
```

For time-based availability:

```txt
Allowed downtime = total time window × error budget percentage
```

---

## 4. Error Budget for SLO 1 — Product Availability

**SLO target:** 99% successful live product loads
**Time window:** 30 days

### Percentage error budget

```txt
Error budget = 100% - 99%
Error budget = 1%
```

### Time-based calculation

A 30-day window contains:

```txt
30 days × 24 hours/day = 720 hours
720 hours × 60 minutes/hour = 43,200 minutes
```

Allowed downtime:

```txt
Allowed downtime = 43,200 minutes × 1%
Allowed downtime = 43,200 × 0.01
Allowed downtime = 432 minutes
```

Convert to hours:

```txt
432 minutes ÷ 60 = 7.2 hours
```

### SLO 1 error budget

Musa can tolerate at most:

```txt
432 minutes of product unavailability per 30 days
```

or:

```txt
7.2 hours of product unavailability per 30 days
```

If the live product is unavailable for more than 432 minutes in 30 days, the error budget is exhausted.

---

## 5. Error Budget for SLO 2 — API Success Rate

**SLO target:** 95% successful core API requests
**Time window:** 30 days

### Percentage error budget

```txt
Error budget = 100% - 95%
Error budget = 5%
```

### Count-based calculation

If Musa has 1,000 measured core API requests in 30 days:

```txt
Allowed failed API requests = 1,000 × 5%
Allowed failed API requests = 1,000 × 0.05
Allowed failed API requests = 50
```

If Musa has 5,000 measured core API requests in 30 days:

```txt
Allowed failed API requests = 5,000 × 5%
Allowed failed API requests = 5,000 × 0.05
Allowed failed API requests = 250
```

### SLO 2 error budget

Musa can tolerate:

```txt
5 failed core API requests per 100 measured core API requests
```

Examples:

| Total core API requests | Allowed failed requests | Required successful requests |
| ----------------------: | ----------------------: | ---------------------------: |
|                     100 |                       5 |                           95 |
|                   1,000 |                      50 |                          950 |
|                   5,000 |                     250 |                        4,750 |

If failed core API requests exceed 5% of measured core API traffic in 30 days, the error budget is exhausted.

---

## 6. Error Budget for SLO 3 — Product Page Load Performance

**SLO target:** 90% of measured product pages load within 3 seconds
**Time window:** 30 days

### Percentage error budget

```txt
Error budget = 100% - 90%
Error budget = 10%
```

### Count-based calculation

If Musa measures 100 product page loads:

```txt
Allowed slow page loads = 100 × 10%
Allowed slow page loads = 100 × 0.10
Allowed slow page loads = 10
```

If Musa measures 500 product page loads:

```txt
Allowed slow page loads = 500 × 10%
Allowed slow page loads = 500 × 0.10
Allowed slow page loads = 50
```

### SLO 3 error budget

Musa can tolerate:

```txt
10 slow page loads per 100 measured product page loads
```

Examples:

| Total measured page loads | Allowed slow page loads | Required fast page loads |
| ------------------------: | ----------------------: | -----------------------: |
|                       100 |                      10 |                       90 |
|                       500 |                      50 |                      450 |
|                     1,000 |                     100 |                      900 |

If more than 10% of measured product page loads take longer than 3 seconds in 30 days, the error budget is exhausted.

---

## 7. Error Budget Summary

| SLO                   | Target | Error budget | Meaning                                                |
| --------------------- | -----: | -----------: | ------------------------------------------------------ |
| Product availability  |    99% |           1% | Maximum 432 minutes downtime per 30 days               |
| API success rate      |    95% |           5% | Maximum 5 failed core API requests per 100 requests    |
| Page load performance |    90% |          10% | Maximum 10 slow page loads per 100 measured page loads |

---

## 8. Error Budget Burn Examples

## Example A — Product Availability

If Musa is unavailable for 2 hours in a 30-day period:

```txt
2 hours × 60 minutes = 120 minutes
Error budget used = 120 / 432 × 100
Error budget used = 27.78%
```

Musa still has:

```txt
100% - 27.78% = 72.22%
```

of the availability error budget remaining.

---

## Example B — API Success Rate

If Musa records 300 core API requests and 21 unexpected failures:

```txt
Actual failure rate = 21 / 300 × 100
Actual failure rate = 7%
```

Allowed failure rate is:

```txt
5%
```

Because:

```txt
7% > 5%
```

the API success error budget is exhausted.

---

## Example C — Page Load Performance

If Musa records 200 measured page loads and 15 are slower than 3 seconds:

```txt
Slow page load rate = 15 / 200 × 100
Slow page load rate = 7.5%
```

Allowed slow page rate is:

```txt
10%
```

Because:

```txt
7.5% < 10%
```

the page performance error budget is not exhausted.

---

## 9. Error Budget Policy

## If 0%–50% of budget is used

Normal product development may continue.

Allowed work:

- Feature development
- UI improvements
- Product listing improvements
- Growth experiments
- Documentation updates

---

## If 50%–80% of budget is used

Reliability review is required.

Required actions:

- Review recent deployments
- Check Cloudflare and Render logs
- Identify repeated errors
- Fix quick reliability issues before adding risky features
- Avoid large untested deployments

---

## If 80%–100% of budget is used

Reliability becomes the priority.

Required actions:

- Pause risky feature changes
- Fix known reliability bugs
- Add monitoring or logging where missing
- Test core flows manually before deployment
- Review API errors and slow pages

---

## If budget is exhausted

Feature work must pause until reliability is restored.

Required actions:

1. Stop non-critical feature development.
2. Identify the failure source.
3. Fix the reliability issue.
4. Verify the fix using manual testing, logs, or analytics.
5. Document the incident and action taken.
6. Resume feature work only after the affected SLO returns within target.

---

## 10. Severity-Based Policy

| Severity | Action                                            |
| -------- | ------------------------------------------------- |
| SEV1     | Stop feature work immediately and restore service |
| SEV2     | Prioritize fix before new product work            |
| SEV3     | Track and fix in the next development cycle       |

---

## 11. Product-Specific Reliability Priorities

For Musa, the most important reliability priorities are:

1. The live product URL must load without error.
2. Buyers must be able to browse products.
3. Product detail pages must open correctly.
4. Creators must be able to log in and manage studios/products.
5. User-specific data such as cart/favourites must not break or leak across users.

---

## 12. Final Policy

Musa is an MVP, so the team accepts small reliability imperfections. However, the team does not accept repeated failures in the product’s core flows.

If the live site, product browsing, login, studio management, or API-backed product flows exceed their error budgets, reliability work takes priority over new feature development.
