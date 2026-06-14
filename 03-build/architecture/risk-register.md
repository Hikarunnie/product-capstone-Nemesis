# Risk Register

**Team:** Nemesis  
**Product:** Musa — Craft Shop Marketplace  
**Date:** 21 May 2026  

---

## Top Technical Risks

| Risk ID | Risk statement | Likelihood, Low Medium High | Impact, Low Medium High | Earliest detection point | Mitigation or spike | Owner | Status |
|--------|----------------|-----------------------------|-------------------------|--------------------------|--------------------|-------|--------|
| R1 | Product image upload may be slow, fail, or display incorrectly across different screen sizes | Medium | High | First seller listing creation test | Test image upload with different file sizes and formats; compress images before saving | Tamar | Open |
| R2 | Seller onboarding may have too many steps, causing creators to abandon before creating their first listing | High | High | First end-to-end seller signup walkthrough | Reduce required fields, allow draft listings, and track drop-off at each step | Tamar | Open |
| R3 | Search and category filtering may return messy or irrelevant results if product data is inconsistent | Medium | Medium | First marketplace browsing test with real listings | Standardize craft categories and required listing fields before launch | Nino | Open |
| R4 | Buyer interest or order request flow may be unclear, causing sellers to miss potential customers | Medium | High | First buyer-to-seller contact test | Add clear request status: new, replied, accepted, declined | Mariam | Open |
| R5 | Marketplace trust may be weak if sellers do not have profiles, photos, or visible product details | Medium | High | First usability test with buyers | Add seller profile, product photos, description, price, and contact visibility rules | Team | Open |
| R6 | Analytics events may not fire correctly for signup, listing creation, and buyer contact actions | Medium | Medium | First end-to-end demo rehearsal | Manually test each event and record expected vs actual event logs | Tamar | Open |

---

## Notes on the Top 3

### R1
- Why this matters to Sprint 1: Musa depends on visual products, so broken or low-quality images would make the marketplace look unprofessional
- What evidence would show the risk is real: uploaded product photos appear stretched, cropped badly, load slowly, or fail completely
- What you will do first: test image upload using jewelry, crochet, art, and accessory photos with different sizes and formats

### R2
- Why this matters to Sprint 1: the main activation moment is a creator successfully creating their first product listing
- What evidence would show the risk is real: creators sign up but do not finish the listing form
- What you will do first: run a seller onboarding walkthrough and remove unnecessary required fields

### R3
- Why this matters to Sprint 1: buyers need to quickly find relevant handmade products, otherwise the marketplace feels empty or hard to use
- What evidence would show the risk is real: searching for “bracelet” or filtering by “jewelry” gives missing, wrong, or duplicated results
- What you will do first: define fixed product categories and test search with a small seeded product list

---

## Spike Plan

| Spike | Question to answer | Timebox | Owner | Output |
|------|--------------------|---------|-------|--------|
| Spike 1 | Can sellers upload product images reliably and display them cleanly in product cards? | 90 minutes | Tamar | Working upload test plus image size rules |
| Spike 2 | What is the minimum seller listing form needed to create a usable product page? | 60 minutes | Tamar | Final required fields list for Sprint 1 |
| Spike 3 | Should Musa use fixed craft categories or free-text tags for the first version? | 45 minutes | Nino | Decision note plus category list |
| Spike 4 | Can a buyer send an interest/order request and can the seller clearly see it? | 90 minutes | Mariam | Tested buyer-to-seller request flow |
| Spike 5 | Which analytics events are required to measure activation? | 45 minutes | Team | Event list for signup, listing created, and buyer contact |

---

## Additional Notes

The biggest risk for Musa is not only technical implementation. The product must make creators feel that listing products is easier and more professional than posting manually on Instagram or answering scattered DMs.

For Sprint 1, the most important technical success signal is:

**A seller can sign up, create a product listing with an image, and see it appear correctly in the marketplace.**

If this flow works, Musa can test real marketplace demand with buyers. If this flow fails, buyer-side features should be delayed until seller onboarding is reliable.

---

*Risk Register | Nemesis | Musa Craft Shop Marketplace | CS-PD-2026 | Spring 2026*