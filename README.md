# Musa — Product Capstone 2026

**Tagline:** A simple selling flow for handmade creators who want to publish products, show their studio, and avoid messy DM-based order management.

| Field       | Details                                               |
| ----------- | ----------------------------------------------------- |
| Course      | CS-PD-2026 Product Development for Software Engineers |
| Semester    | Spring 2026                                           |
| Institution | Kutaisi International University                      |
| Team        | Nemesis                                               |
| Product     | Musa                                                  |

---

## Live Links

- **Live Product:** [Open Musa](https://musa-front.pages.dev/)
- **Demo Video:** [Watch Demo Video](https://drive.google.com/file/d/11aw6MfCuA-AOYxVXjkOf3xqtV0mKBXZW/view)
- **Analytics Dashboard:** [`03-build/analytics/dashboard-link.md`](./03-build/analytics/dashboard-link.md)
- **Analytics Screenshot:** [`03-build/analytics/analytics-screenshot.png`](./03-build/analytics/analytics-screenshot.png)
- **Architecture Diagram:** [`03-build/architecture/architecture-diagram.png`](./03-build/architecture/architecture-diagram.png)
- **Final Case Study:** [`09-final/case-study.md`](./09-final/case-study.md)
- **Launch Video Documentation:** [`09-final/demo-video.md`](./09-final/demo-video.md)

---

## Problem Statement

Aspiring and early-stage handmade creators struggle to start and sustain online selling because the process feels emotionally risky and operationally unstructured. Many creators either delay publishing because they feel their products, photos, prices, and page must be perfect, or they begin selling through Instagram/Facebook DMs and become overwhelmed by scattered questions, unclear orders, pricing confusion, and manual tracking.

---

## Solution

Musa is a lightweight marketplace and creator-studio tool for handmade sellers.

It helps creators:

- create a simple public studio;
- publish handmade products;
- show product prices, categories, and details clearly;
- make products easier for buyers to discover;
- reduce reliance on chaotic Instagram/Facebook DMs;
- move early selling into a clearer product and order flow.

The goal is not to replace creators’ social media presence. The goal is to give handmade creators a structured selling layer that makes the first step of publishing and managing products easier.

---

## Target Users

Musa is built for beginner and early-stage handmade creators, especially people who make:

- crochet items;
- jewelry;
- clothing and accessories;
- paintings;
- plushies;
- pottery;
- other handmade crafts.

Our ideal customer is a creator who already makes handmade products but struggles with at least one of these pains:

- hesitates to start selling because everything feels like it must be perfect;
- uses Instagram/Facebook DMs for orders;
- loses track of prices, colors, sizes, delivery details, or buyer requests;
- needs a simpler option than a full e-commerce platform.

---

## Discovery Evidence

The problem was validated through creator interviews, synthesis, usability testing, and early traction evidence.

Important discovery and validation files:

- [`01-discovery/interview-logs/`](./01-discovery/interview-logs/)
- [`01-discovery/synthesis/patterns-analysis.md`](./01-discovery/synthesis/patterns-analysis.md)
- [`01-discovery/synthesis/final-problem-statement.md`](./01-discovery/synthesis/final-problem-statement.md)
- [`01-discovery/synthesis/competitive-landscape-seed.md`](./01-discovery/synthesis/competitive-landscape-seed.md)
- [`02-design/user-testing/usability-findings.md`](./02-design/user-testing/usability-findings.md)
- [`04-gtm/traction/`](./04-gtm/traction/)

Representative interview insights:

> “I feel like I need everything to be perfect before I start.”

> “People would text me randomly and I would forget who ordered what.”

These insights shaped Musa’s focus on reducing emotional friction and replacing scattered DM-based selling with a clearer listing and studio flow.

---

## Product Features

The deployed MVP includes:

- user registration and login;
- creator studio creation;
- product listing creation;
- product discovery/explore page;
- product cards with images, category, price, and studio information;
- product detail pages;
- profile and published-products flow;
- favorites/cart/order-related flows;
- backend API for users, studios, products, favorites, cart, and orders;
- analytics documentation for product learning and traction evidence.

---

## Tech Stack

| Area                | Technology                         | Purpose                                                                 |
| ------------------- | ---------------------------------- | ----------------------------------------------------------------------- |
| Frontend            | Next.js, React, TypeScript         | User interface, routing, reusable components                            |
| Styling             | Tailwind CSS                       | Fast responsive styling and consistent UI                               |
| Backend             | Django, Django REST Framework      | API, authentication, product/studio/order logic                         |
| Authentication      | JWT                                | Token-based authentication between frontend and backend                 |
| Database            | PostgreSQL                         | Relational storage for users, studios, products, and order-related data |
| Frontend Deployment | Cloudflare Pages                   | Public hosting for the frontend                                         |
| Backend Deployment  | Render                             | Hosted backend/API environment                                          |
| Version Control     | Git + GitHub                       | Collaboration, commit history, and final repository review              |
| Analytics           | Analytics dashboard + event schema | Tracks user/product behavior and supports product decisions             |

More detail: [`03-build/architecture/tech-stack.md`](./03-build/architecture/tech-stack.md)

---

## Architecture Overview

Musa uses a separated frontend-backend architecture.

The frontend is a Next.js application for buyer and creator-facing pages such as login, signup, explore, studio, profile, product creation, product detail, and published products. The backend is a Django REST API that manages authentication, users, studios, products, favorites, cart, and orders. PostgreSQL stores the main application data. Analytics artifacts document the North Star Metric, tracked events, dashboard link, and dashboard screenshot.

Architecture documentation:

- [`03-build/architecture/system-design.md`](./03-build/architecture/system-design.md)
- [`03-build/architecture/tech-stack.md`](./03-build/architecture/tech-stack.md)
- [`03-build/architecture/architecture-diagram.png`](./03-build/architecture/architecture-diagram.png)

---

## Analytics

Analytics evidence is documented in:

- [`03-build/analytics/dashboard-link.md`](./03-build/analytics/dashboard-link.md)
- [`03-build/analytics/analytics-screenshot.png`](./03-build/analytics/analytics-screenshot.png)
- [`03-build/analytics/event-schema.md`](./03-build/analytics/event-schema.md)
- [`03-build/analytics/north-star-metric.md`](./03-build/analytics/north-star-metric.md)

Our North Star Metric is:

> Weekly successfully managed product listings per active creator.

This metric reflects whether creators are actually using Musa to publish and manage selling activity, not only visiting the product.

---

## Repository Structure

```text
.
├── 00-foundation/
│   ├── team-contract.md
│   ├── team-problem-statement.md
│   └── team-icp.md
│
├── 01-discovery/
│   ├── interview-logs/
│   ├── outreach/
│   └── synthesis/
│       ├── patterns-analysis.md
│       ├── final-problem-statement.md
│       └── competitive-landscape-seed.md
│
├── 02-design/
│   ├── prototypes/
│   │   └── high-fidelity/
│   │       └── figma-link.md
│   └── user-testing/
│       └── usability-findings.md
│
├── 03-build/
│   ├── analytics/
│   │   ├── analytics-screenshot.png
│   │   ├── dashboard-link.md
│   │   ├── event-schema.md
│   │   └── north-star-metric.md
│   ├── architecture/
│   │   ├── architecture-diagram.png
│   │   ├── system-design.md
│   │   └── tech-stack.md
│   ├── experiments/
│   │   └── experiment-results.md
│   ├── privacy-security/
│   │   ├── consent-form.md
│   │   └── security-tabletop.md
│   ├── reliability/
│   │   ├── error-budget.md
│   │   └── slo-sheet.md
│   ├── roadmap/
│   └── workflow/
│
├── 04-gtm/
│   ├── financials/
│   │   ├── unit-economics.md
│   │   └── 12-month-model.xlsx
│   ├── traction/
│   ├── growth-strategy.md
│   ├── growth_projection.xlsx
│   └── loops-and-moats.md
│
├── 05-fundraising/
│   ├── pitch-deck.pdf
│   └── one-pager.pdf
│
├── 06-strategy/
│   ├── competitive-analysis.md
│   ├── ecosystem-map.md
│   ├── moat-statement.md
│   ├── prioritization-framework.md
│   ├── product-roadmap.md
│   └── strategy-canvas.md
│
├── 07-team/
│   └── contribution-logs/
│
├── 08-legal/
│   └── privacy-notice.md
│
├── 09-final/
│   ├── case-study.md
│   └── demo-video.md
│
├── docs/
│   ├── ai-usage-log.md
│   └── standup-log.md
│
├── LICENSE
└── README.md
```

---

## Go-To-Market

Musa’s go-to-market plan focuses on early handmade creators and design partners.

GTM materials:

- [`04-gtm/growth-strategy.md`](./04-gtm/growth-strategy.md)
- [`04-gtm/loops-and-moats.md`](./04-gtm/loops-and-moats.md)
- [`04-gtm/traction/`](./04-gtm/traction/)

The first acquisition channels focus on direct outreach to handmade creators, student/community groups, and early design-partner relationships.

---

## Business Model

Musa uses an 8% platform fee per successful order.

Financial materials:

- [`04-gtm/financials/unit-economics.md`](./04-gtm/financials/unit-economics.md)
- [`04-gtm/financials/12-month-model.xlsx`](./04-gtm/financials/12-month-model.xlsx)
- [`04-gtm/growth_projection.xlsx`](./04-gtm/growth_projection.xlsx)

The financial model includes revenue projections, cost structure, CAC/LTV assumptions, payback period, and growth scenarios.

---

## Traction

Traction evidence is documented in:

- [`04-gtm/traction/`](./04-gtm/traction/)
- [`03-build/analytics/dashboard-link.md`](./03-build/analytics/dashboard-link.md)
- [`03-build/analytics/analytics-screenshot.png`](./03-build/analytics/analytics-screenshot.png)

This includes design-partner evidence, waitlist/early-interest evidence, and analytics evidence from product usage.

---

## Fundraising Materials

Final Demo Day materials:

- [`05-fundraising/pitch-deck.pdf`](./05-fundraising/pitch-deck.pdf)
- [`05-fundraising/one-pager.pdf`](./05-fundraising/one-pager.pdf)

The pitch deck covers:

1. Problem with ICP and verbatim quote
2. Solution
3. Why Now
4. Market Size
5. Product
6. Traction
7. Business Model
8. Go-To-Market
9. Competition and moat
10. Ask

---

## Strategy

Strategy materials:

- [`06-strategy/competitive-analysis.md`](./06-strategy/competitive-analysis.md)
- [`06-strategy/strategy-canvas.md`](./06-strategy/strategy-canvas.md)
- [`06-strategy/ecosystem-map.md`](./06-strategy/ecosystem-map.md)
- [`06-strategy/moat-statement.md`](./06-strategy/moat-statement.md)
- [`06-strategy/product-roadmap.md`](./06-strategy/product-roadmap.md)
- [`06-strategy/prioritization-framework.md`](./06-strategy/prioritization-framework.md)

---

## Privacy, Security, and Reliability

Privacy, security, and reliability documentation:

- [`03-build/privacy-security/consent-form.md`](./03-build/privacy-security/consent-form.md)
- [`03-build/privacy-security/security-tabletop.md`](./03-build/privacy-security/security-tabletop.md)
- [`03-build/reliability/slo-sheet.md`](./03-build/reliability/slo-sheet.md)
- [`03-build/reliability/error-budget.md`](./03-build/reliability/error-budget.md)
- [`08-legal/privacy-notice.md`](./08-legal/privacy-notice.md)

---

## Team

| Name              | Role                 | GitHub                                                 |
| ----------------- | -------------------- | ------------------------------------------------------ |
| Ketevan Shavadze  | Program Lead         | [@Ketishavadze](https://github.com/Ketishavadze)       |
| Gvantsa Nozadze   | Discovery / GTM Lead | [@Gvantsa-N](https://github.com/Gvantsa-N)             |
| Ani Kharabadze    | Tech Lead            | [@Hikarunnie](https://github.com/Hikarunnie)           |
| Tamar Vatcharadze | Discovery Lead       | [@takovatcharadze](https://github.com/takovatcharadze) |

Contribution evidence:

- [`07-team/contribution-logs/`](./07-team/contribution-logs/)

---

## Setup Instructions

### Prerequisites

Install:

- Git
- Node.js
- npm
- Python
- pip
- PostgreSQL

---

### Clone Repository

```bash
git clone https://github.com/Hikarunnie/product-capstone-Nemesis.git
cd product-capstone-Nemesis
```

---

### Frontend Setup

Enter the frontend directory used by the project:

```bash
cd frontend
```

Install dependencies:

```bash
npm install
```

Create local environment file if needed:

```bash
cp .env.example .env.local
```

Run locally:

```bash
npm run dev
```

Frontend local URL:

```text
http://localhost:3000
```

---

### Backend Setup

Enter the backend directory used by the project:

```bash
cd backend
```

Create a virtual environment:

```bash
python -m venv .venv
```

Activate it.

Windows:

```bash
.venv\Scripts\activate
```

macOS/Linux:

```bash
source .venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Create local environment file if needed:

```bash
cp .env.example .env
```

Run migrations:

```bash
python manage.py migrate
```

Start backend:

```bash
python manage.py runserver
```

Backend local URL:

```text
http://127.0.0.1:8000
```

---

## Environment Variables

Common environment variables:

```text
DATABASE_URL=
SECRET_KEY=
DEBUG=
ALLOWED_HOSTS=
CORS_ALLOWED_ORIGINS=
NEXT_PUBLIC_API_URL=
```

Production secrets are not committed to the repository.

---

## AI Usage and Process Evidence

Process documentation:

- [`docs/ai-usage-log.md`](./docs/ai-usage-log.md)
- [`docs/standup-log.md`](./docs/standup-log.md)

---

## Final Submission

Final submission checklist:

- Repository is public.
- Final tag is `cp4-submission`.
- README includes product name, tagline, problem statement, live product URL, demo video link, team members, tech stack, setup instructions, architecture overview, and license declaration.
- Required folders `00-foundation` through `09-final` are present.
- Required CP4 evidence is organized in the repository.
- Links in this README resolve correctly.

---

## License

This project is released under the MIT License. See [`LICENSE`](./LICENSE) for details.
