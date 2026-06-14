# Tech Stack Selection

**Team:** Nemesis  
**Product:** Musa  
**Date:** 21 May 2026  
**Version:** 1.0 — Sprint 1 stack lock

---

## 1. Decision Summary

Sprint 1 optimizes mostly for speed, reliability, cost, and team familiarity. We chose a separate frontend and backend because it makes the project easier to develop, deploy, and debug in layers. The frontend is built with React/Next.js because it allows fast UI development and easy deployment through Cloudflare Pages. The backend uses Django and Django REST Framework because the team is familiar with Python and Django gives us authentication, admin tools, database models, and API structure quickly. PostgreSQL was selected because the product needs reliable relational data for users, products, listings, and future orders. More advanced features such as automated testing, full analytics, and production-scale monitoring are deferred until after the first working deployment.

---

## 2. Stack by Layer

| Layer          | Selected technology                                                  | Why this fits                                                                                     | Alternative considered           | Why rejected                                            | Owner              |
| -------------- | -------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | -------------------------------- | ------------------------------------------------------- | ------------------ |
| Frontend       | Next.js / React                                                      | Fast UI development, component-based structure, good for marketplace-style pages, easy deployment | Plain React with Vite            | Next.js gives better routing and deployment structure   | Ani K.             |
| Backend        | Django + Django REST Framework                                       | Familiar Python stack, fast API development, built-in admin, strong ORM                           | Node.js / Express                | More boilerplate for auth, admin, and models            | Ketevan S., Ani K. |
| Database       | PostgreSQL on Render                                                 | Reliable relational database for users, products, and listings                                    | SQLite                           | Good locally but not suitable for production deployment | Ketevan            |
| Database tool  | pgAdmin                                                              | Helps inspect and manage the PostgreSQL database visually                                         | Terminal-only psql               | Less beginner-friendly and slower for checking tables   | Tamar V.           |
| Authentication | Django authentication / JWT-style API auth                           | Fits naturally with Django backend and frontend API calls                                         | Firebase Auth                    | Adds a separate service and more integration work       | Backend Team       |
| Analytics      | Deferred for Sprint 1                                                | Main priority is working MVP and deployment                                                       | PostHog / Google Analytics       | Not necessary before core flows work                    | Whole Team         |
| Hosting        | Render for backend, Render PostgreSQL, Cloudflare Pages for frontend | Low-cost, simple deployment path, separates frontend and backend clearly                          | Vercel + Railway                 | Team already used Render and Cloudflare Pages           | Team               |
| Testing        | Manual testing for Sprint 1                                          | Faster for MVP validation and demo preparation                                                    | Jest / Playwright / Django tests | Automated setup deferred to reduce Sprint 1 complexity  | Team               |
| Diagramming    | Mermaid / Markdown diagrams                                          | Easy to store in GitHub with architecture docs                                                    | Figma-only diagrams              | Not as easy to version-control inside repo              | Team               |

---

## 3. Approved AI Tools for Sprint 1

| Tool           | Approved use                                                  | Not for                                             | Review rule                                      | Owner               |
| -------------- | ------------------------------------------------------------- | --------------------------------------------------- | ------------------------------------------------ | ------------------- |
| Stitch         | Not approved for Sprint 1                                     | Final code or business logic                        | Any use must be logged and reviewed              | Gvantsa N. Tamar V. |
| Claude Code    | Code suggestions, debugging help, refactoring ideas           | Copy-pasting security-sensitive code without review | Every generated line must be read and tested     | Team                |
| Github Copilot | Inline coding help, small UI/code completions                 | Accepting full features without understanding them  | No generated code is merged without human review | Team                |
| ChatGPT        | Debugging, documentation drafting, deployment troubleshooting | Final decisions without team review                 | Output must be checked before commit             | Ani K., Ketevan S.  |

---

## 4. Deployment Target

- Public deployment target: Frontend on Cloudflare Pages, backend on Render.
- Database region or environment: Render PostgreSQL production database, managed through Render and pgAdmin.
- How local and production differ: Local development can use local environment variables and local database tools, while production uses Render environment variables and hosted PostgreSQL.
- What gets deployed first: Backend API and PostgreSQL database first, then frontend connected to the deployed backend URL.
- What will stay local for now, if anything: pgAdmin is local/admin-only and is not part of the public deployment.

---

## 5. Rejected Architecture Paths

### Rejected Option 1

- Option: Full-stack Next.js app with backend routes in the frontend project.
- Why it was attractive: One project, one deployment, simpler folder structure.
- Why it was rejected now: The team already has a Django backend and separating backend/frontend makes database, API, and admin logic cleaner.

### Rejected Option 2

- Option: Firebase / Firestore.
- Why it was attractive: Built-in hosting, auth, and database services.
- Why it was rejected now: PostgreSQL fits the relational marketplace data better, and Django works more naturally with SQL models.

### Rejected Option 3

- Option: SQLite for production.
- Why it was attractive: Very easy to start with and works locally.
- Why it was rejected now: It is not reliable enough for deployed multi-user production use.

---

## 6. Technical Debt You Are Accepting on Purpose

| Shortcut                                  | Why accepted now                   | Risk created                                    | When to revisit               |
| ----------------------------------------- | ---------------------------------- | ----------------------------------------------- | ----------------------------- |
| Manual testing instead of automated tests | Faster Sprint 1 delivery           | Regression bugs may appear later                | Sprint 2                      |
| Basic analytics deferred                  | MVP functionality matters more now | Less visibility into user behavior              | After public demo works       |
| Simple deployment setup                   | Keeps hosting understandable       | May need better CI/CD later                     | After first stable deployment |
| Basic auth flow                           | Enough for Sprint 1                | Security and permissions may need strengthening | Before real users             |

---

## 7. Final Stack Lock

- Frontend: frontend uses Next.js/React and is deployed on Cloudflare Pages.
- Backend: backend uses Django and Django REST Framework deployed on Render.
- Database: uses PostgreSQL hosted on Render and managed with pgAdmin.
- Auth: Authentication is handled through the Django backend API.
- Analytics: Analytics are deferred for Sprint 1.
- Hosting: Frontend is hosted on Cloudflare Pages, while backend and PostgreSQL are hosted on Render.

No TBD entries remain.
