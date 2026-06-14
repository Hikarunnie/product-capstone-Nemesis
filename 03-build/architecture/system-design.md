# System Design Document

**File path:** `03-build/architecture/system-design.md`

**Team:** Nemesis  
**Product:** Musa  
**Date:** 24 April 2026
**Version:** 2.0 — updated 14 May 2026 to reflect Sprint 1 actual build
**Primary author:** Ani Kharabadze

---

## 1. Core Sprint 1 Request

```text
A user creates an account, uploads a handmade product listing, and sees the product published on the marketplace feed.
```

**Current Sprint 1 boundary:**

- In scope:
  - User registration
  - Login/authentication
  - Product creation
  - Marketplace feed
  - Backend API integration
  - PostgreSQL database storage
  - Public deployment

- Out of scope:
  - Payments
  - Messaging system
  - Real order processing
  - Notifications
  - Recommendation system
  - AI-powered product suggestions
  - Advanced analytics

---

## 2. System Goal

By Sprint 1 review, Musa must support a complete marketplace flow through a public deployment. Users should be able to create accounts, authenticate, create handmade product listings, and view products on the public marketplace feed. The frontend communicates with a Django REST backend connected to PostgreSQL for persistent storage. The architecture prioritizes reliability, deployment simplicity, and fast iteration over advanced scalability features. Sprint 1 mainly proves that the full stack works correctly in production.

---

## 3. Component Breakdown

| Component               | Layer       | Responsibility                                                        | Owner        | Technology                     | AI touchpoint, if any |
| ----------------------- | ----------- | --------------------------------------------------------------------- | ------------ | ------------------------------ | --------------------- |
| Frontend web/mobile app | Client      | Renders marketplace UI, product forms, navigation, feed               | Ani          | Next.js / React                | ChatGPT, Copilot      |
| Application logic       | Server      | Handles API requests, business logic, authentication, CRUD operations | Ketevan      | Django + Django REST Framework | ChatGPT               |
| Database                | Data        | Stores users and products permanently                                 | Ketevan      | PostgreSQL                     | None                  |
| Database management     | Data/Admin  | Visual inspection and management of PostgreSQL                        | Ani          | pgAdmin                        | None                  |
| Authentication          | Auth        | User registration and login flow                                      | Backend team | Django Auth / JWT-style auth   | ChatGPT               |
| Analytics               | Measurement | Deferred for Sprint 1                                                 | Team         | None yet                       | None                  |
| External services       | Integration | Deployment and hosting infrastructure                                 | Team         | Render + Cloudflare Pages      | None                  |

---

## 4. Key Data Objects

| Entity               | What it represents                         | Created by            | Read by                         | Stored where               |
| -------------------- | ------------------------------------------ | --------------------- | ------------------------------- | -------------------------- |
| User                 | Marketplace user account                   | Registration form     | Authentication system, frontend | PostgreSQL                 |
| Product              | Handmade marketplace listing               | Product creation form | Marketplace feed                | PostgreSQL                 |
| Product Image URL    | Reference to product image                 | Product form          | Product cards and detail views  | PostgreSQL                 |
| Authentication Token | Temporary authenticated session            | Login endpoint        | Frontend API requests           | Frontend temporary storage |
| API Request          | Communication between frontend and backend | Frontend actions      | Django backend                  | Temporary only             |

---

## 5. User Request Lifecycle

1. User opens the Musa frontend URL hosted on Cloudflare Pages.
2. Frontend loads the marketplace homepage.
3. Frontend checks whether the user is authenticated.
4. User logs in or creates an account.
5. Frontend sends authentication request to Django backend hosted on Render.
6. Backend validates credentials and returns authentication response.
7. Frontend stores authentication token/session locally.
8. User opens the “My Studio” page.
9. Frontend checks whether the user already has a studio/profile.
10. If the user does not have one, frontend creates a new studio profile through the backend API.
11. User opens the “Create Listing” page.
12. User enters product title, category, description, price, and image URL.
13. Frontend sends product creation request to backend API.
14. Django backend validates all required fields.
15. PostgreSQL stores the new product permanently.
16. Backend returns created product response.
17. Frontend refreshes the marketplace feed.
18. User sees the newly published product displayed publicly.

---

## 6. Data Flow Notes

- What data enters from the user?
  - Email
  - Username
  - Password
  - Product title
  - Category
  - Description
  - Price
  - Product image URL

- What data is validated?
  - Authentication credentials
  - Required product fields
  - API request structure
  - Form input formatting

- What data is stored permanently?
  - Users
  - Product listings
  - Product metadata

- What data is temporary or computed?
  - Authentication tokens
  - Frontend state
  - API responses

- What data should never be stored?
  - Plain-text passwords
  - Secret keys
  - Sensitive environment variables

---

## 7. APIs and Integrations

| Service or API   | Why it exists                                          | Request direction       | Risk                     | Fallback plan             |
| ---------------- | ------------------------------------------------------ | ----------------------- | ------------------------ | ------------------------- |
| Django REST API  | Handles backend business logic and database operations | Frontend → Backend      | API deployment failure   | Run backend locally       |
| PostgreSQL       | Persistent relational database storage                 | Backend ↔ Database      | Connection failure       | Local PostgreSQL database |
| Render Hosting   | Hosts backend API and PostgreSQL                       | Public traffic → Render | Free-tier sleeping       | Restart/redeploy backend  |
| Cloudflare Pages | Hosts frontend application                             | Users → Frontend        | Deployment/build failure | Local frontend deployment |

---

## 8. Deployment Topology

- Frontend hosted on:
  - Cloudflare Pages

- Backend hosted on:
  - Render

- Database hosted on:
  - Render PostgreSQL

- Domain or public URL:
  - Cloudflare Pages deployment URL

- Analytics platform:
  - None for Sprint 1

- Auth provider:
  - Django backend authentication

- File storage, if any:
  - Product image URLs only for Sprint 1

---

## 9. AI in the Build and AI in the Product

### AI in the build workflow

| Tool           | Used for what                                        | Owner                | Review rule                   |
| -------------- | ---------------------------------------------------- | -------------------- | ----------------------------- |
| Stitch         | Not approved for Sprint 1                            | Gvantsa N., Tamar V. | Requires approval             |
| Claude Code    | Backend/frontend debugging and suggestions           | Team                 | Every generated line reviewed |
| Github Copilot | Inline coding assistance and autocomplete            | Team                 | No blind acceptance           |
| ChatGPT        | Deployment troubleshooting, debugging, documentation | Ani K., Ketevan S.   | Outputs verified manually     |

### AI in the product, if applicable

Musa does not include runtime AI functionality in Sprint 1. AI tools are used only during development workflows.

---

## 10. Security, Privacy, and Reliability Basics

- Auth risks:
  - Weak authentication validation
  - Token misuse

- Sensitive data handled:
  - User credentials
  - Authentication tokens

- Failure mode if main service goes down:
  - Frontend cannot communicate with backend
  - Login and product creation stop working

- Logging and monitoring plan for Sprint 1:
  - Manual monitoring through Render logs and browser console logs

- One thing you will not promise yet:
  - High scalability or enterprise-level reliability

---

## 11. Technical Risks and Spikes

1. Risk:
   - Frontend/backend deployment communication problems

   - Why it matters:
     - API requests may fail in production

   - Mitigation or spike:
     - Test CORS and environment variables carefully before deployment

   - Owner:
     - Ani

2. Risk:
   - PostgreSQL connection or migration failures

   - Why it matters:
     - Product data cannot be stored correctly

   - Mitigation or spike:
     - Test migrations locally before deployment

   - Owner:
     - Ketevan

3. Risk:
   - Render free-tier sleeping and cold starts

   - Why it matters:
     - Slow initial API response or temporary downtime

   - Mitigation or spike:
     - Monitor deployment logs and restart service if necessary

   - Owner:
     - Team

---

## 12. Open Questions

- Should product images move to real cloud storage later?
- Will analytics be added in Sprint 2?
- Should authentication move to full JWT refresh-token implementation?
- Will payments eventually require a separate microservice?

---

## 13. Final Readiness Check

- [x] Every component has one clear job
- [x] Core request lifecycle is written end to end
- [x] Stack in this file matches `tech-stack.md`
- [x] Top technical risks are named
- [x] Out of scope items are explicit
- [x] Another developer could start work from this document

---

_System Design | TheMergeConflicters | CS-PD-2026 | Spring 2026_
