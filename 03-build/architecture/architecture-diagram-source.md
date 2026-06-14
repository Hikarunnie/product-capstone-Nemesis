# Architecture Diagram — Source

**Final required file:** `03-build/architecture/architecture-diagram.png`  
**Team:** Nemesis  
**Product:** Musa  
**Date:** 21 May 2026

> This file contains the Mermaid source for the architecture diagram. Export the diagram below to PNG using the Mermaid Live Editor and save the PNG as `architecture-diagram.png` in this folder.

---

## 1. Diagram Goal

```text
This diagram shows how a Musa user authenticates, creates a studio, publishes a handmade product listing, and views it on the marketplace feed across the Sprint 1 system.
```

---

## 2. Required Boxes Included

| Box                        | Included | Notes                     |
| -------------------------- | -------- | ------------------------- |
| User                       | Yes      | Marketplace user          |
| Browser / client app       | Yes      | Next.js frontend          |
| Frontend application       | Yes      | React / Next.js UI        |
| Authentication provider    | Yes      | Django authentication     |
| Backend / server logic     | Yes      | Django REST API           |
| Database                   | Yes      | PostgreSQL                |
| Analytics / event tracking | Deferred | No analytics in Sprint 1  |
| External APIs or services  | Yes      | Render + Cloudflare Pages |
| AI touchpoints             | Yes      | Build workflow only       |

---

## 3. Mermaid Diagram

```mermaid
flowchart TD

    U["Musa User<br/>(Web Browser)"]

    subgraph CLIENT["Client - Next.js Frontend (Cloudflare Pages)"]
        direction TB
        F_HOME["Marketplace Feed"]
        F_AUTH["Signup / Login Screen"]
        F_STUDIO["My Studio"]
        F_CREATE["Create Listing Screen"]
        F_PRODUCT["Published Product Card"]
    end

    subgraph SERVER["Server - Django REST API (Render)"]
        direction TB
        SA_AUTH["Authentication Logic<br/>validate credentials + token"]
        SA_STUDIO["Studio Logic<br/>check or create studio"]
        SA_PRODUCT["Product Creation API<br/>validate + create product"]
        SA_FEED["Marketplace Feed API<br/>return published products"]
    end

    subgraph DB["Data - PostgreSQL (Render Postgres)"]
        direction LR
        T_USERS[("users")]
        T_STUDIOS[("studios")]
        T_PRODUCTS[("products")]
    end

    HOSTING["External Hosting<br/>Cloudflare Pages<br/>Render Backend<br/>Render PostgreSQL"]

    AI_NOTE["AI tools: development workflow only<br/>ChatGPT - debugging + docs<br/>Copilot/Cursor - code suggestions<br/>No runtime AI in product"]

    U -->|"opens marketplace URL"| F_HOME

    F_HOME -->|"opens login/signup"| F_AUTH
    F_AUTH -->|"submits email + password"| SA_AUTH
    SA_AUTH -->|"creates or validates user"| T_USERS
    SA_AUTH -->|"returns auth token/session"| F_AUTH
    F_AUTH -->|"redirects after success"| F_STUDIO

    F_STUDIO -->|"checks existing studio"| SA_STUDIO
    SA_STUDIO -->|"reads studio record"| T_STUDIOS
    F_STUDIO -->|"creates studio if missing"| SA_STUDIO
    SA_STUDIO -->|"writes new studio"| T_STUDIOS

    F_STUDIO -->|"opens Create Listing"| F_CREATE
    F_CREATE -->|"submits title, category, price, description, image URL"| SA_PRODUCT
    SA_PRODUCT -->|"writes new product"| T_PRODUCTS
    SA_PRODUCT -->|"returns created product"| F_CREATE

    F_CREATE -->|"refreshes marketplace feed"| SA_FEED
    SA_FEED -->|"reads published products"| T_PRODUCTS
    SA_FEED -->|"returns product cards"| F_HOME
    F_HOME -->|"shows published listing"| F_PRODUCT

    HOSTING -.->|"hosts frontend"| CLIENT
    HOSTING -.->|"hosts backend API"| SERVER
    HOSTING -.->|"hosts database"| DB

    AI_NOTE -.->|"used during development only"| CLIENT
    AI_NOTE -.->|"used during development only"| SERVER

    classDef screen fill:#e8f5e9,stroke:#2e7d32,color:#1b5e20
    classDef server fill:#e3f2fd,stroke:#1565c0,color:#0d47a1
    classDef data fill:#fff8e1,stroke:#ef6c00,color:#e65100
    classDef external fill:#fce4ec,stroke:#c62828,color:#880e4f
    classDef ai fill:#f3e5f5,stroke:#7b1fa2,color:#4a148c,stroke-dasharray: 5 5

    class F_HOME,F_AUTH,F_STUDIO,F_CREATE,F_PRODUCT screen
    class SA_AUTH,SA_STUDIO,SA_PRODUCT,SA_FEED server
    class T_USERS,T_STUDIOS,T_PRODUCTS data
    class HOSTING external
    class AI_NOTE ai
```

## ![alt text](image.png)

## 4. Arrow Logic Summary

| Arrow              | Label                      | From                  | To                     |
| ------------------ | -------------------------- | --------------------- | ---------------------- |
| User opens URL     | opens marketplace URL      | User                  | Marketplace Feed       |
| Open auth screen   | opens login/signup         | Marketplace Feed      | Signup/Login Screen    |
| Submit credentials | submits email + password   | Signup/Login Screen   | Authentication Logic   |
| User validation    | creates or validates user  | Authentication Logic  | users table            |
| Auth response      | returns auth response      | Authentication Logic  | Signup/Login Screen    |
| Redirect           | redirects after success    | Signup/Login Screen   | My Studio              |
| Studio check       | checks existing studio     | My Studio             | Studio Creation Logic  |
| Studio read        | reads studio record        | Studio Creation Logic | studios table          |
| Create studio      | creates studio if missing  | My Studio             | Studio Creation Logic  |
| Studio write       | writes new studio          | Studio Creation Logic | studios table          |
| Open listing form  | opens Create Listing       | My Studio             | Create Listing Screen  |
| Product submit     | submits listing data       | Create Listing Screen | Product Creation API   |
| Product validation | validates required fields  | Product Creation API  | Product Creation API   |
| Product write      | writes new product         | Product Creation API  | products table         |
| Product response   | returns created product    | Product Creation API  | Create Listing Screen  |
| Feed refresh       | refreshes marketplace feed | Create Listing Screen | Marketplace Feed API   |
| Product read       | reads published products   | Marketplace Feed API  | products table         |
| Feed response      | returns product cards      | Marketplace Feed API  | Marketplace Feed       |
| Product display    | shows published listing    | Marketplace Feed      | Published Product Card |

---

## 5. AI Annotation

**AI tools exist only in the development workflow. No runtime AI feature exists in Sprint 1.**

- ChatGPT:
  - Deployment troubleshooting
  - Debugging
  - Documentation support

- Copilot / Cursor:
  - Inline code suggestions
  - Boilerplate generation

- Claude Code:
  - Backend/frontend debugging support

No AI API is called during actual user interaction with Musa.

---

## 6. Final Export Check

- [x] Boxes match the written system design
- [x] Arrows are labeled
- [x] Database is visually distinct
- [x] Auth is shown where it happens
- [x] Analytics status is explicitly mentioned
- [x] Diagram is readable at normal zoom
- [x] PNG exported and committed as `architecture-diagram.png`
