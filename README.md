# Musa — Simple storefronts for handmade creators

**Musa** helps handmade creators turn Instagram interest into clear product listings, simple storefronts, and manageable orders.

## Product Tagline

**From handmade creativity to a real online shop — without DM chaos.**

---

## Problem Statement

Many handmade creators want to sell their work, but they delay starting because publishing products, prices, photos, and a shop page feels emotionally risky and “not ready enough.” Creators who do start often manage orders through Instagram or Facebook DMs, which leads to lost details, unclear availability, repeated questions, and missed sales.

---

## Live Product

[Open the live Musa product](https://musa-front.pages.dev/)

---

## Demo Video

[Watch the 60-second Musa demo video](https://drive.google.com/file/d/11aw6MfCuA-AOYxVXjkOf3xqtV0mKBXZW/view?usp=sharing)

---

## Team Members

* Ani Kharabadze
* Ketevan Shavadze
* Gvantsa Nozadze
* Tamar Vatcharadze

---

## Product Overview

Musa is a lightweight marketplace and storefront tool for handmade creators. It allows creators to open a studio, publish products, show prices clearly, and make their items easier for buyers to discover and order.

Our target users are early-stage handmade creators who currently sell through informal channels such as Instagram, Facebook, personal messages, or word of mouth. Musa reduces the friction between making a craft and presenting it as a sellable product.

---

## Core Features

* Creator account registration and login
* Studio creation for handmade sellers
* Product listing creation with name, description, price, category, and image
* Product discovery page for buyers
* Product detail pages
* Favourite products
* Cart flow
* Order-related backend structure
* Studio-based product ownership
* Deployed frontend and backend

---

## Tech Stack

### Frontend

* **Next.js** — React framework for the user interface
* **TypeScript** — safer and clearer frontend development
* **Tailwind CSS** — fast styling and responsive layout
* **Cloudflare Pages** — frontend deployment

### Backend

* **Django** — backend framework
* **Django REST Framework** — REST API development
* **JWT Authentication** — user authentication
* **PostgreSQL** — relational production database
* **Render** — backend and database hosting

### Product and Documentation Tools

* **Figma / Stitch** — high-fidelity prototype and product design
* **GitHub** — version control and repository management
* **Analytics dashboard** — event and product usage tracking
* **AI tools** — used for assisted documentation, planning, and implementation support, documented in [`docs/ai-usage-log.md`](docs/ai-usage-log.md)

---

## Repository Structure

```txt
.
├── 00-foundation/
│   ├── team-contract.md
│   ├── team-problem-statement.md
│   └── team-icp.md
│
├── 01-discovery/
│   └── synthesis/
│       ├── patterns-analysis.md
│       ├── final-problem-statement.md
│       └── competitive-landscape-seed.md
│
├── 02-design/
│   ├── prototypes/high-fidelity/figma-link.md
│   └── user-testing/usability-findings.md
│
├── 03-build/
│   ├── architecture/
│   │   ├── system-design.md
│   │   ├── tech-stack.md
│   │   └── architecture-diagram.png
│   ├── analytics/dashboard-link.md
│   ├── experiments/experiment-results.md
│   ├── privacy-security/
│   │   ├── consent-form.md
│   │   └── security-tabletop.md
│   └── reliability/
│       ├── slo-sheet.md
│       └── error-budget.md
│
├── 04-gtm/
│   ├── growth-strategy.md
│   ├── financials/
│   │   ├── unit-economics.md
│   │   └── 12-month-model.xlsx
│   ├── growth-projection.xlsx
│   ├── loops-and-moats.md
│   └── traction/
│
├── 05-fundraising/
│   ├── pitch-deck.pdf
│   └── one-pager.pdf
│
├── 06-strategy/
│   ├── competitive-analysis.md
│   ├── strategy-canvas.md
│   ├── ecosystem-map.md
│   ├── moat-statement.md
│   ├── product-roadmap.md
│   └── prioritization-framework.md
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

## Architecture Overview

Musa uses a client-server architecture.

The frontend is a Next.js application deployed on Cloudflare Pages. Users interact with pages such as Explore, Login, Signup, Studio, Product Details, Cart, and Create Listing. The frontend communicates with the backend through REST API requests.

The backend is built with Django REST Framework and exposes API endpoints for authentication, users, studios, products, favourites, cart, and orders. PostgreSQL stores structured product, studio, user, and order-related data. JWT authentication is used to protect user-specific actions such as creating a studio or publishing a product.

For a more detailed explanation, see:

* [`03-build/architecture/system-design.md`](03-build/architecture/system-design.md)
* [`03-build/architecture/tech-stack.md`](03-build/architecture/tech-stack.md)
* [`03-build/architecture/architecture-diagram.png`](03-build/architecture/architecture-diagram.png)

---

## Setup Instructions

### Prerequisites

Before running the project locally, install:

* Node.js 20 or later
* npm
* Python 3.12 or later
* pip
* PostgreSQL
* Git

---

## Frontend Setup

Clone the repository:

```bash
git clone https://github.com/Hikarunnie/product-capstone-Nemesis.git
cd product-capstone-Nemesis
```

Go to the frontend folder:

```bash
cd frontend
```

Install dependencies:

```bash
npm install
```

Create a local environment file if needed:

```bash
cp .env.example .env.local
```

Add the backend API URL:

```env
NEXT_PUBLIC_API_URL=http://127.0.0.1:8000
```

Run the frontend:

```bash
npm run dev
```

The frontend should run at:

```txt
http://localhost:3000
```

---

## Backend Setup

From the repository root, go to the backend folder:

```bash
cd backend
```

Create and activate a virtual environment.

On macOS/Linux:

```bash
python -m venv .venv
source .venv/bin/activate
```

On Windows PowerShell:

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

Install Python dependencies:

```bash
pip install -r requirements.txt
```

Create a local `.env` file if needed:

```bash
cp .env.example .env
```

Example environment variables:

```env
SECRET_KEY=replace-with-local-secret-key
DEBUG=True
DATABASE_URL=postgresql://username:password@localhost:5432/musa
ALLOWED_HOSTS=127.0.0.1,localhost
CORS_ALLOWED_ORIGINS=http://localhost:3000
```

Run migrations:

```bash
python manage.py migrate
```

Start the backend server:

```bash
python manage.py runserver
```

The backend should run at:

```txt
http://127.0.0.1:8000
```

---

## Main API Areas

The backend includes API support for:

* User registration
* User login
* Current user profile
* Studio creation and retrieval
* Product creation, listing, editing, and deletion
* Favourite products
* Cart
* Orders

---

## Discovery and Validation Evidence

The product direction is based on customer discovery with handmade creators and potential buyers. The research showed two repeated pain points:

1. Creators hesitate to start selling because the process feels emotionally risky and they feel their shop must look perfect before publishing.
2. Creators who already sell often manage everything through DMs, which makes order tracking and communication messy.

Discovery evidence and synthesis are documented in:

* [`01-discovery/synthesis/patterns-analysis.md`](01-discovery/synthesis/patterns-analysis.md)
* [`01-discovery/synthesis/final-problem-statement.md`](01-discovery/synthesis/final-problem-statement.md)
* [`00-foundation/team-icp.md`](00-foundation/team-icp.md)

---

## Go-To-Market Summary

Musa’s initial go-to-market strategy focuses on reaching early-stage handmade creators through specific local and community-based channels. The first target segment is student and young creator communities where handmade selling already happens informally through social media.

The go-to-market plan includes:

* KIU student creator communities
* Instagram handmade creator outreach
* Local craft and small-business communities

Detailed growth planning is documented in:

* [`04-gtm/growth-strategy.md`](04-gtm/growth-strategy.md)
* [`04-gtm/financials/unit-economics.md`](04-gtm/financials/unit-economics.md)
* [`04-gtm/loops-and-moats.md`](04-gtm/loops-and-moats.md)

---

## Business Model

Musa uses a transaction-based platform model. The planned business model is an **8% platform fee per completed order**.

This model aligns Musa’s revenue with creator success: Musa earns only when creators successfully sell products through the platform.

Financial assumptions, CAC, LTV, payback period, and projections are documented in:

* [`04-gtm/financials/unit-economics.md`](04-gtm/financials/unit-economics.md)
* [`04-gtm/financials/12-month-model.xlsx`](04-gtm/financials/12-month-model.xlsx)
* [`04-gtm/growth-projection.xlsx`](04-gtm/growth-projection.xlsx)

---

## Traction

Traction evidence is documented in:

* [`04-gtm/traction/`](04-gtm/traction/)
* [`03-build/analytics/dashboard-link.md`](03-build/analytics/dashboard-link.md)
* [`05-fundraising/pitch-deck.pdf`](05-fundraising/pitch-deck.pdf)

The traction evidence includes user interest, analytics, and validation signals collected during the product development process.

---

## Privacy, Security, and Reliability

Musa documents privacy, consent, security, and reliability practices as part of the final product repository.

Privacy and security documents:

* [`03-build/privacy-security/consent-form.md`](03-build/privacy-security/consent-form.md)
* [`03-build/privacy-security/security-tabletop.md`](03-build/privacy-security/security-tabletop.md)
* [`08-legal/privacy-notice.md`](08-legal/privacy-notice.md)

Reliability documents:

* [`03-build/reliability/slo-sheet.md`](03-build/reliability/slo-sheet.md)
* [`03-build/reliability/error-budget.md`](03-build/reliability/error-budget.md)

---

## Fundraising Materials

Final Demo Day fundraising materials are included in:

* [`05-fundraising/pitch-deck.pdf`](05-fundraising/pitch-deck.pdf)
* [`05-fundraising/one-pager.pdf`](05-fundraising/one-pager.pdf)

The pitch deck includes the required 10 slides:

1. Problem
2. Solution
3. Why Now
4. Market Size
5. Product
6. Traction
7. Business Model
8. Go-To-Market
9. Competition
10. Ask

---

## Strategy Documents

The final strategy section includes competitive analysis, strategy canvas, ecosystem map, moat statement, product roadmap, and prioritization framework.

See:

* [`06-strategy/competitive-analysis.md`](06-strategy/competitive-analysis.md)
* [`06-strategy/strategy-canvas.md`](06-strategy/strategy-canvas.md)
* [`06-strategy/ecosystem-map.md`](06-strategy/ecosystem-map.md)
* [`06-strategy/moat-statement.md`](06-strategy/moat-statement.md)
* [`06-strategy/product-roadmap.md`](06-strategy/product-roadmap.md)
* [`06-strategy/prioritization-framework.md`](06-strategy/prioritization-framework.md)

---

## Final Submission Materials

Final case study and demo video documentation are included in:

* [`09-final/case-study.md`](09-final/case-study.md)
* [`09-final/demo-video.md`](09-final/demo-video.md)

---

## AI Usage Disclosure

AI tools were used to support documentation drafting, code debugging, product planning, and repository organization. All AI-assisted work was reviewed by team members before being accepted, modified, or discarded.

The full AI usage log is available here:

* [`docs/ai-usage-log.md`](docs/ai-usage-log.md)

---

## Standup Documentation

Sprint standup history is documented in:

* [`docs/standup-log.md`](docs/standup-log.md)

---

## Open-Source License

This project is released under the **MIT License**.

See the full license here:

* [`LICENSE`](LICENSE)

---

## Repository Status

This repository is the final Demo Day submission for:

**CS-PD-2026 | Checkpoint 4: Demo Day**
**Kutaisi International University**
**Team Nemesis**
**Product: Musa**
