# Product Roadmap — Nemesis Craft Market

**Team:** Nemesis  
**Product:** Nemesis Craft Martket  
**Date:** [5/6/2025]  
**Version:** 1.0  
**Sprint Arc:** April 24 to June 11 2026

---

## MVP Scope

### What We Are Building

Nemesis Platform is a mobile-first handmade marketplace app for creators and buyers. Buyers can browse and purchase handmade products such as crochet clothing, jewelry, accessories, bowls, and press-on nails. Creators can manage their studio, create product listings, and publish items to the marketplace.

The main MVP focus is creator activation. The most important user behavior is when a creator successfully completes and publishes a new product listing. This matters because the marketplace only becomes valuable if creators add real products for buyers to discover.

### North Star Metric

> Weekly completed product listings per active creator

### Activation Event

> `listing_completed`

This event fires when a creator taps **Publish Listing** and successfully creates a new marketplace listing.

---

## In Scope: Sprints 1 to 4

| Feature | Sprint | Interview Evidence / Product Reasoning |
|---------|--------|-----------------------------------------|
| Mobile-first marketplace feed | Sprint 1 | Buyers need to browse handmade items easily before purchasing. This also gives creators a clear place where their products will appear. |
| Product cards with image, title, price, and Add button | Sprint 1 | Handmade products are visual, so image-first cards help users quickly understand product value. |
| Bottom navigation: Explore, Cart, My Studio, Profile | Sprint 1 | The prototype needs a simple structure that supports both buyer and creator behavior without clutter. |
| Cart screen with selected items and order summary | Sprint 1 | Buyer flow is secondary, but the app should still feel like a real marketplace. |
| Creator workspace / My Studio dashboard | Sprint 1 | Creators need a clear place to manage listings and start the listing process. |
| Create New Listing CTA | Sprint 1 | This is the key bridge into the activation flow. |
| Create Listing form | Sprint 1 | Core MVP feature. Creators must be able to enter product title, category, price, description, and image. |
| Publish Listing button | Sprint 1 | This is the activation moment that triggers `listing_completed`. |
| Basic user profile screen | Sprint 2 | Users need a place to access My Studio, My Listings, Settings, and Become a Seller. |
| Product listing storage | Sprint 2 | Listings must persist after publishing so the MVP works with real data. |
| Creator listing management | Sprint 2 | Creators should be able to view their active listings after publishing. |
| Analytics instrumentation | Sprint 2 | Required to track activation and evaluate whether creators are completing listings. |
| Analytics dashboard for activation funnel | Sprint 2 | Needed for Checkpoint 3 to show events such as listing started and listing completed. |
| Usability testing with real creators | Sprint 2 | Needed to confirm whether the listing flow is understandable and not too difficult. |
| Edit listing feature | Sprint 3 | Creators may need to correct price, title, description, or image after publishing. |
| Listing status tags such as Active or Draft | Sprint 3 | Helps creators understand what is already published and what still needs work. |
| Search and category filtering | Sprint 3 | Helps buyers find relevant handmade products and improves marketplace usability. |
| Improved seller onboarding | Sprint 3 | Helps buyers transition into creators by making the selling path clearer. |
| Final polish, bug fixes, and demo preparation | Sprint 4 | Needed for Demo Day and final product presentation. |
| Repository documentation and AI log | Sprint 4 | Required for submission and technical clarity. |
| Pitch deck / venture packet updates | Sprint 4 | Needed for final demo and product explanation. |

---

## Out of Scope: MVP Phase

| Feature | Reason Out of Scope |
|---------|---------------------|
| Full payment processing | Checkout is not the core activation flow. Payment can be simulated during MVP because the main evaluated behavior is listing creation. |
| Real shipping integration | Too technically complex for the sprint arc and not required to prove creator activation. |
| Chat between buyers and sellers | Could be useful later, but it distracts from the core listing creation funnel. |
| Reviews and ratings | Helpful for trust, but not necessary for the first activation-focused MVP. |
| Advanced analytics for sellers | The prototype includes basic studio stats, but full analytics can come after the MVP. |
| Native iOS / Android apps | Mobile web is enough for the course MVP and faster to build. |
| AI product description generator | Interesting future feature, but not necessary for validating whether creators can publish listings manually. |

---

## Explicitly Rejected

| Feature | Why Rejected |
|---------|-------------|
| Social media feed | The product is a marketplace, not a social network. A feed would distract from buying and listing creation. |
| Complex creator dashboard with too many statistics | Beginner creators may feel overwhelmed. The MVP should stay simple and focused on creating listings. |
| Auction or bidding system | Handmade sellers need a simple listing flow first. Auctions would add unnecessary complexity. |
| Multiple seller subscription plans | No strong evidence yet that creators are ready to pay before the platform proves value. |
| Advanced customization for storefronts | Useful later, but the first MVP should focus on getting products listed. |

---

## Sprint Overview

| Sprint | Dates | Theme | Key Deliverable | Checkpoint |
|--------|-------|-------|-----------------|------------|
| Sprint 1 | Apr 24 to May 7 | Foundation | A user can browse the marketplace, open the cart, access My Studio, and start creating a listing. | Sprint Review May 7 |
| Sprint 2 | May 8 to May 21 | Activation + Instrumentation | A creator can publish a listing, listing data persists, and analytics events are firing. | Checkpoint 3 May 21 |
| Sprint 3 | May 22 to Jun 4 | Creator Management + Marketplace Improvement | Creators can manage listings and buyers can search/filter products more easily. | Peer Assessment Jun 4 |
| Sprint 4 | Jun 5 to Jun 11 | Demo Day | Product is polished, repo is complete, and the pitch/demo are ready. | Demo Day Jun 11 |

---

# Sprint 1: Foundation

**Dates:** April 24 to May 7 2026  
**Sprint Goal:** A user can browse the marketplace, view product cards, use the cart screen, access My Studio, and begin the create listing flow from a publicly accessible URL.  
**Demo:** Show the mobile app flow: Explore → Cart → My Studio → Create New Listing.

---

## Capacity

| Team Member | Available Hours | Story Points Max |
|-------------|-----------------|-----------------|
| Team Member 1 | 14 hrs | ~10 pts |
| Team Member 2 | 12 hrs | ~8 pts |
| Team Member 3 | 14 hrs | ~10 pts |
| **Total** | **40 hrs** | **~28 pts max** |

**Sprint 1 commitment:** 17 story points

**Rationale:** Sprint 1 focuses on building the foundation from the Stitch prototype. The team should avoid overbuilding and focus only on the core mobile screens and navigation.

---

## Stories Allocated to Sprint 1

| Story ID | Story Summary | Points | Assignee | AI Tool |
|----------|---------------|--------|----------|---------|
| S1-01 | Set up project repository and basic app structure | 2 | Team Member 1 | GitHub Copilot |
| S1-02 | Build mobile marketplace feed with product cards | 4 | Team Member 2 | Google Stitch + Claude Code |
| S1-03 | Add bottom navigation: Explore, Cart, My Studio, Profile | 3 | Team Member 1 | GitHub Copilot |
| S1-04 | Build cart screen with selected items and order summary | 3 | Team Member 2 | Google Stitch |
| S1-05 | Build My Studio dashboard with Create New Listing CTA | 3 | Team Member 3 | Google Stitch + Claude Code |
| S1-06 | Connect navigation between Explore, Cart, My Studio, and Profile | 2 | Team Member 1 | GitHub Copilot |
| **Sprint 1 Total** | | **17** | | |

---

## Sprint 1 Risks

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| Stitch-generated UI may need manual cleanup | Medium | Medium | Review each screen against the prototype before merging. |
| Team may spend too much time polishing visuals | High | Medium | Prioritize functional navigation first, visual polish second. |
| Product images may not load correctly | Medium | Low | Use local placeholder images or seeded image URLs for demo. |
| Scope creep into payments or chat | Medium | High | Keep buyer flow simple and avoid non-MVP features. |

---

# Sprint 2: Activation + Instrumentation

**Dates:** May 8 to May 21 2026  
**Sprint Goal:** A creator can complete and publish a product listing, the listing saves, and analytics events are firing correctly.  
**Demo:** Create a product listing live and show the `listing_completed` event in the analytics dashboard.  
**Checkpoint 3 due:** May 21 at 23:59

---

## Capacity

**Sprint 2 commitment:** 20 story points  
This can be adjusted after Sprint 1 velocity is measured.

---

## Stories Allocated to Sprint 2

| Story ID | Story Summary | Points | Assignee | AI Tool |
|----------|---------------|--------|----------|---------|
| S2-01 | Build Create Listing form with title, price, category, image, and description fields | 5 | Team Member 1 | Google Stitch + Claude Code |
| S2-02 | Add Publish Listing button and validation for required fields | 3 | Team Member 1 | GitHub Copilot |
| S2-03 | Store completed listings in database | 5 | Team Member 2 | Claude Code |
| S2-04 | Show newly created listings in My Studio | 3 | Team Member 2 | Claude Code |
| S2-05 | Track analytics events: `listing_started`, `listing_form_completed`, `listing_completed` | 3 | Team Member 3 | GitHub Copilot |
| S2-06 | Create analytics dashboard for activation funnel | 1 | Team Member 3 | None |
| **Sprint 2 Total** | | **20** | | |

---

## Sprint 2 Analytics Events

| Event Name | Trigger | Why It Matters |
|------------|---------|----------------|
| `listing_started` | User taps Create New Listing | Shows how many creators enter the activation funnel. |
| `listing_form_completed` | User fills all required fields | Shows whether creators understand and complete the form. |
| `listing_completed` | User taps Publish Listing and listing saves successfully | Main activation event. |
| `listing_viewed_in_studio` | User sees the new listing in My Studio | Confirms that the creator can verify their listing after publishing. |

---

## Sprint 2 Risks

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| Database setup takes longer than expected | Medium | High | Use a simple schema first: users, products, listings. |
| Image upload is technically difficult | High | Medium | Use image URL upload or placeholder image upload for MVP if needed. |
| Analytics events fire at the wrong time | Medium | High | Test each event manually before Checkpoint 3. |
| Create Listing form becomes too complex | Medium | Medium | Keep only required MVP fields. Add advanced fields later. |

---

# Sprint 3: Creator Management + Marketplace Improvement

**Dates:** May 22 to June 4 2026  
**Sprint Goal:** Creators can better manage listings, and buyers can search or filter products more easily.  
**Demo:** Creator edits or views active listings, while buyer uses search/category filters to browse the marketplace.

---

## Capacity

**Sprint 3 commitment:** 18 story points  
This should be adjusted after Sprint 2 velocity.

---

## Stories Allocated to Sprint 3

| Story ID | Story Summary | Points | Assignee | AI Tool |
|----------|---------------|--------|----------|---------|
| S3-01 | Add My Listings screen for creators | 4 | Team Member 1 | Google Stitch + Claude Code |
| S3-02 | Add listing status tags: Active and Draft | 3 | Team Member 1 | GitHub Copilot |
| S3-03 | Allow creators to edit listing title, price, category, and description | 5 | Team Member 2 | Claude Code |
| S3-04 | Add marketplace search by product title/category | 3 | Team Member 2 | GitHub Copilot |
| S3-05 | Add category filter chips for Crochet, Jewelry, Fashion, Art, and Accessories | 2 | Team Member 3 | GitHub Copilot |
| S3-06 | Conduct 5 usability tests with handmade creators or potential sellers | 1 | All | None |
| **Sprint 3 Total** | | **18** | | |

---

## Sprint 3 Risks

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| Edit listing feature becomes too large | Medium | High | Limit editing to text fields first. Image editing can be postponed. |
| Search/filter implementation may conflict with seeded data | Low | Medium | Standardize product categories before implementation. |
| Recruiting creator testers is difficult | High | Medium | Use classmates or friends who make crafts, jewelry, crochet, art, or digital products. |
| Too much time spent on buyer features | Medium | Medium | Keep creator activation and listing management as the priority. |

---

# Sprint 4: Demo Day

**Dates:** June 5 to June 11 2026  
**Sprint Goal:** The app is stable, demo-ready, documented, and connected clearly to the product analytics story.  
**Demo Day:** June 11 2026

---

## Capacity

**Sprint 4 commitment:** 11 story points  
Sprint 4 is shorter, so the team should focus on polish, bug fixes, documentation, and presentation.

---

## Stories Allocated to Sprint 4

| Story ID | Story Summary | Points | Assignee | AI Tool |
|----------|---------------|--------|----------|---------|
| S4-01 | Fix bugs found during usability testing | 3 | Team Member 1 | GitHub Copilot |
| S4-02 | Polish mobile UI for marketplace, cart, studio, listing, and profile screens | 3 | Team Member 2 | Google Stitch |
| S4-03 | Complete README, setup instructions, and architecture notes | 2 | Team Member 3 | None |
| S4-04 | Complete AI usage log and event schema documentation | 1 | Team Member 3 | None |
| S4-05 | Update pitch deck and venture packet with real product screenshots and analytics | 2 | All | None |
| **Sprint 4 Total** | | **11** | | |

---

## Sprint 4 Risks

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| Last-minute bugs break the demo flow | Medium | High | Freeze new features by June 8 and only fix bugs after that. |
| Analytics dashboard has too little data | Medium | Medium | Run test sessions before Demo Day to generate event data. |
| Team spends too much time on presentation instead of product stability | Medium | High | Assign one person to demo script while others handle bug fixes. |

---

# Full Backlog Summary

| Story ID | Summary | Sprint | Points |
|----------|---------|--------|--------|
| S1-01 | Project repository and app setup | 1 | 2 |
| S1-02 | Mobile marketplace feed | 1 | 4 |
| S1-03 | Bottom navigation | 1 | 3 |
| S1-04 | Cart screen | 1 | 3 |
| S1-05 | My Studio dashboard | 1 | 3 |
| S1-06 | Screen navigation | 1 | 2 |
| S2-01 | Create Listing form | 2 | 5 |
| S2-02 | Publish Listing button and validation | 2 | 3 |
| S2-03 | Product listing database storage | 2 | 5 |
| S2-04 | Show listings in My Studio | 2 | 3 |
| S2-05 | Analytics event tracking | 2 | 3 |
| S2-06 | Analytics dashboard | 2 | 1 |
| S3-01 | My Listings screen | 3 | 4 |
| S3-02 | Listing status tags | 3 | 3 |
| S3-03 | Edit listing feature | 3 | 5 |
| S3-04 | Marketplace search | 3 | 3 |
| S3-05 | Category filter chips | 3 | 2 |
| S3-06 | Usability testing | 3 | 1 |
| S4-01 | Bug fixes | 4 | 3 |
| S4-02 | UI polish | 4 | 3 |
| S4-03 | Repository documentation | 4 | 2 |
| S4-04 | AI usage log and event schema documentation | 4 | 1 |
| S4-05 | Pitch deck and venture packet updates | 4 | 2 |

**Total story points across all sprints:** 66  
**Unallocated backlog points:** 0

---

# Milestone Alignment

| Milestone | Date | What Our Product Must Be Able to Do |
|-----------|------|--------------------------------------|
| Checkpoint 2 | Wed 22 Apr | Roadmap submitted, prototype testable, event schema planned |
| Sprint 1 Review | May 7 | Core screens built and deployed: Explore, Cart, My Studio, Profile |
| Checkpoint 3 | Thu 21 May | Creator can publish a listing, data persists, analytics dashboard live |
| Peer Assessment | Thu 4 Jun | Product can be demoed without explanation and tested by users |
| Demo Day | Thu 11 Jun | 7-minute pitch and live product demo ready |

---

# Product Metrics

## Primary Metric

| Metric | Definition | Why It Matters |
|--------|------------|----------------|
| Weekly completed product listings per active creator | Number of successful `listing_completed` events per active creator each week | Shows whether creators are actually activating and adding marketplace supply. |

## Supporting Metrics

| Metric | Definition | Why It Matters |
|--------|------------|----------------|
| Listing start rate | Percent of active creators who tap Create New Listing | Shows whether users are entering the creator funnel. |
| Listing completion rate | Percent of users who start a listing and successfully publish it | Shows whether the form is clear and usable. |
| Marketplace browse rate | Percent of users who view product cards on Explore | Shows whether the buyer side has enough engagement. |
| Cart add rate | Percent of users who add an item to cart | Shows whether buyers are interested in products. |
| Creator return rate | Percent of creators who return to My Studio after publishing | Shows whether creators see value after activation. |

---

# Technical Scope

## Frontend

| Area | Technology / Approach |
|------|------------------------|
| UI Framework | React or Next.js |
| Styling | Tailwind CSS or CSS modules |
| Prototype Source | Google Stitch high-fidelity prototype |
| Deployment | Vercel |

## Backend

| Area | Technology / Approach |
|------|------------------------|
| Authentication | Simple email login or temporary demo login |
| Database | Supabase, Firebase, or simple backend database |
| Product Storage | Products/listings table |
| Analytics | Mixpanel, PostHog, or similar event tracking tool |

## Data Model Draft

| Table | Important Fields |
|-------|------------------|
| users | id, name, email, role |
| listings | id, creator_id, title, price, category, description, image_url, status, created_at |
| cart_items | id, user_id, listing_id, quantity |
| events | event_name, user_id, timestamp, metadata |

---

# Change Log

| Date | Version | Changes | Author |
|------|---------|---------|--------|
| [Date] | 1.0 | Initial product roadmap created for Nemesis Platform | Ketevan Shavadze |

---

*Product Roadmap | Nemesis Platform | CS-PD-2026 | Spring 2026*