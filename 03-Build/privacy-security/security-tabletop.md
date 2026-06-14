# Security Tabletop and STRIDE Threat Model

**Team:** Nemesis
**Product:** Musa
**Date:** 14 June 2026
**Document:** Security tabletop for CP4 final repository review

---

## 1. Purpose

This document applies the STRIDE threat model to Musa’s highest-traffic and highest-risk user flows. Musa is a handmade marketplace and storefront product where creators can open studios and publish products, while buyers can browse products, view product details, add favourites/cart items, and interact with order-related flows.

The goal of this tabletop is to identify realistic security threats, document mitigations or accepted MVP risks, and record dependency audit and secrets-check results before final submission.

---

## 2. Product Architecture Summary

Musa uses a separated frontend and backend architecture.

| Layer          | Technology                                           | Security relevance                                                          |
| -------------- | ---------------------------------------------------- | --------------------------------------------------------------------------- |
| Frontend       | Next.js / React deployed on Cloudflare Pages         | Handles user interface, routing, public product browsing, and API calls     |
| Backend        | Django + Django REST Framework deployed on Render    | Handles authentication, authorization, studios, products, carts, and orders |
| Database       | PostgreSQL on Render                                 | Stores users, studios, product listings, cart/order-related data            |
| Authentication | Django authentication / JWT-style API authentication | Protects user-specific and creator-specific actions                         |
| Hosting        | Cloudflare Pages + Render                            | Provides deployed production environments with HTTPS                        |
| Analytics      | Cloudflare dashboard evidence                        | Shows real usage data for the deployed product                              |

---

## 3. Assets Being Protected

| Asset                            | Why it matters                                                   |
| -------------------------------- | ---------------------------------------------------------------- |
| User accounts                    | Unauthorized access could expose or modify user data             |
| Authentication tokens            | Token theft could allow account takeover                         |
| Studio ownership                 | A creator must not be able to edit another creator’s studio      |
| Product listings                 | Listings must not be changed or deleted by unauthorized users    |
| Cart, favourites, and order data | Buyer-specific data must remain private                          |
| Environment secrets              | Leaked keys or database URLs could compromise production systems |
| Analytics and research data      | User activity and feedback should be handled responsibly         |

---

## 4. Five Highest-Traffic / Highest-Risk User Flows

| Flow ID | Flow                                                   | Why it was selected                                      |
| ------- | ------------------------------------------------------ | -------------------------------------------------------- |
| F1      | Browse Explore page and product listings               | Main discovery flow for buyers and visitors              |
| F2      | View product detail page                               | Main product interest flow                               |
| F3      | User registration and login                            | Required for accounts and protected actions              |
| F4      | Creator creates or updates studio and product listings | Core creator flow with ownership and data-integrity risk |
| F5      | Add favourites/cart items and order-related actions    | Buyer intent flow with private user-specific data        |

---

## 5. STRIDE Threat Model

---

## F1 — Browse Explore Page and Product Listings

| STRIDE category        | Threat                                                                                         | Risk level | Mitigation or acceptance                                                                                |
| ---------------------- | ---------------------------------------------------------------------------------------------- | ---------: | ------------------------------------------------------------------------------------------------------- |
| Spoofing               | A fake frontend or API could pretend to be Musa and show manipulated listings                  |     Medium | Mitigated by using the official deployed Musa URL, official API URL, and HTTPS                          |
| Tampering              | Product listing API responses could be modified in transit                                     |     Medium | Mitigated by production HTTPS through Cloudflare Pages and Render                                       |
| Repudiation            | Anonymous visitors can deny browsing actions                                                   |        Low | Accepted because anonymous browsing is low risk and does not perform destructive actions                |
| Information disclosure | Public listing APIs could expose private user fields such as email or internal account details |       High | Mitigated by serializers returning only public product and studio fields needed for display             |
| Denial of service      | High traffic to Explore could overload the backend or database                                 |     Medium | Mitigated with Cloudflare hosting layer, basic monitoring, and future pagination/caching plan           |
| Elevation of privilege | A visitor could try to access creator-only actions from public pages                           |       High | Mitigated by backend authentication and permission checks; hiding UI buttons is not treated as security |

**Decision:** Mitigated with accepted MVP limitations. Future improvement: add stronger pagination, caching, and request throttling.

---

## F2 — View Product Detail Page

| STRIDE category        | Threat                                                                                 | Risk level | Mitigation or acceptance                                                                                                |
| ---------------------- | -------------------------------------------------------------------------------------- | ---------: | ----------------------------------------------------------------------------------------------------------------------- |
| Spoofing               | A malicious user could create a misleading studio name to impersonate another creator  |     Medium | Partly mitigated by linking studios to authenticated users; accepted for MVP until stronger creator verification exists |
| Tampering              | A user could change the product ID in API requests and attempt to edit another product |       High | Mitigated by backend object-level ownership checks for update/delete actions                                            |
| Repudiation            | A creator may deny editing product details                                             |     Medium | Mitigated by storing product ownership and created/updated timestamps                                                   |
| Information disclosure | Product detail response may expose private fields                                      |       High | Mitigated by limiting API responses to public product fields                                                            |
| Denial of service      | Repeated product detail requests could overload the API                                |     Medium | Accepted for MVP due to low traffic; future mitigation is API throttling and caching                                    |
| Elevation of privilege | A buyer could attempt creator-only edit/delete actions                                 |       High | Mitigated by server-side authorization checks, not only frontend controls                                               |

**Decision:** Mitigated. Remaining risk around creator impersonation is accepted for MVP and should be revisited before wider public launch.

---

## F3 — User Registration and Login

| STRIDE category        | Threat                                                                 | Risk level | Mitigation or acceptance                                                                               |
| ---------------------- | ---------------------------------------------------------------------- | ---------: | ------------------------------------------------------------------------------------------------------ |
| Spoofing               | Attacker logs in as another user using stolen credentials              |       High | Mitigated by Django password hashing and backend authentication checks                                 |
| Tampering              | Attacker modifies a JWT/token or request payload                       |       High | Mitigated by HTTPS and backend token validation                                                        |
| Repudiation            | A user denies creating an account or logging in                        |     Medium | Mitigated by account creation records and timestamps where available                                   |
| Information disclosure | Login errors may reveal whether an email exists                        |     Medium | Mitigated by using generic login error messages where possible                                         |
| Denial of service      | Repeated login attempts could brute force accounts or overload backend |       High | Accepted for MVP with mitigation plan: add DRF throttling/rate limiting before wider launch            |
| Elevation of privilege | A normal user becomes admin/staff through modified request data        |       High | Mitigated by not accepting staff/admin fields from public signup and enforcing permissions server-side |

**Decision:** Mostly mitigated. Rate limiting is accepted as a known MVP gap and should be addressed before wider public launch.

---

## F4 — Creator Creates or Updates Studio/Product Listings

| STRIDE category        | Threat                                                                      | Risk level | Mitigation or acceptance                                                                    |
| ---------------------- | --------------------------------------------------------------------------- | ---------: | ------------------------------------------------------------------------------------------- |
| Spoofing               | A user pretends to own another studio                                       |       High | Mitigated by linking each studio to an authenticated user account                           |
| Tampering              | A creator edits or deletes another creator’s product                        |       High | Mitigated by backend ownership checks before update/delete                                  |
| Repudiation            | Creator denies creating or changing a listing                               |     Medium | Mitigated with authenticated user ownership and timestamps                                  |
| Information disclosure | Draft/private creator data could be shown publicly                          |       High | Mitigated by exposing only intended public product/studio fields                            |
| Denial of service      | Large image uploads or repeated product creation could overload the backend |     Medium | Accepted for MVP; future mitigation is upload validation, size limits, and throttling       |
| Elevation of privilege | User bypasses frontend and calls protected API endpoints directly           |       High | Mitigated by requiring authentication and checking permissions in backend views/serializers |

**Decision:** Mitigated for ownership and authorization. Upload and rate-limit protections are accepted MVP risks with future mitigation.

---

## F5 — Favourites, Cart, and Order-Related Actions

| STRIDE category        | Threat                                                    | Risk level | Mitigation or acceptance                                                          |
| ---------------------- | --------------------------------------------------------- | ---------: | --------------------------------------------------------------------------------- |
| Spoofing               | A user acts as another buyer                              |       High | Mitigated by requiring authentication for user-specific actions                   |
| Tampering              | A user modifies cart/order data belonging to another user |       High | Mitigated by filtering user-specific records by authenticated user                |
| Repudiation            | A buyer denies adding an item or creating an order        |     Medium | Mitigated by storing user association and timestamps                              |
| Information disclosure | One user sees another user’s favourites/cart/orders       |       High | Mitigated by backend querysets restricted to `request.user`                       |
| Denial of service      | Repeated add/remove actions create excessive writes       |     Medium | Accepted for MVP; future mitigation is throttling and duplicate-action validation |
| Elevation of privilege | Buyer accesses seller/admin order management              |       High | Mitigated by backend permission checks and user/role-based filtering              |

**Decision:** Mitigated for privacy and authorization. Rate limiting remains accepted for MVP.

---

## 6. Highest-Priority Security Risks

| Priority | Risk                                       | Reason                                                  | Status                                                                     |
| -------: | ------------------------------------------ | ------------------------------------------------------- | -------------------------------------------------------------------------- |
|        1 | Unauthorized studio/product editing        | Could damage creator trust and product integrity        | Mitigated with backend ownership checks                                    |
|        2 | User seeing another user’s cart/order data | Serious privacy issue                                   | Mitigated by filtering by authenticated user                               |
|        3 | Authentication token misuse                | Could cause account takeover                            | Mitigated with backend token validation and HTTPS                          |
|        4 | Secrets committed to GitHub                | Could expose database/API access                        | Checked through secrets scan                                               |
|        5 | Critical/high dependency vulnerabilities   | Known vulnerabilities could compromise frontend/backend | Checked with `npm audit` and `pip-audit`; critical/high findings addressed |

---

## 7. Mitigation Summary

| Security area            | Mitigation                                                                                    |
| ------------------------ | --------------------------------------------------------------------------------------------- |
| Authentication           | Django authentication / JWT-style API authentication                                          |
| Password storage         | Django password hashing                                                                       |
| Authorization            | Backend permission checks for protected actions                                               |
| Studio/product ownership | Creator actions tied to authenticated user ownership                                          |
| User-specific data       | Favourites, cart, and orders filtered by authenticated user                                   |
| Transport security       | Production deployments use HTTPS                                                              |
| Public/private fields    | API serializers expose only needed public fields                                              |
| Dependency security      | `npm audit` and `pip-audit` reviewed and remediated                                           |
| Secrets management       | Secrets stored in deployment environment variables; repository scanned for secret-like values |

---

## 8. Dependency Audit Results

---

## 8.1 Frontend Dependency Audit

**Repository checked:**
`https://github.com/Hikarunnie/Musa_front.git`

**Command used:**

```bash
npm audit
```

### Initial result

The frontend audit initially reported:

```txt
2 vulnerabilities:
- 1 critical vulnerability affecting Next.js
- 1 moderate vulnerability affecting PostCSS
```

The critical Next.js finding included advisories related to cache poisoning, denial of service, authorization bypass, SSRF, request smuggling, image optimization issues, and XSS in affected Next.js versions.

### Action taken

The team upgraded the affected Next.js dependency. The original critical finding was removed. After the first upgrade, `npm audit` still reported one high-severity Next.js-related finding and one moderate PostCSS-related finding. The team then upgraded Next.js to `16.2.9` in a controlled way and verified that the frontend still builds.

### Build verification

Command used:

```bash
npm run build
```

Result:

```txt
Next.js 16.2.9 production build completed successfully.
The build compiled successfully, ran TypeScript checks, collected page data, generated static pages, and finalized page optimization.
```

A warning appeared about multiple lockfiles and inferred workspace root. This warning does not block the production build, but the team should clean duplicate lockfiles after submission to avoid workspace confusion.

### Final frontend audit result after remediation

```txt
npm audit reported 2 moderate severity vulnerabilities:
- PostCSS <8.5.10
- Next.js depends on the vulnerable PostCSS version

No critical vulnerabilities remained.
No high vulnerabilities remained.
```

### Frontend decision

The frontend critical and high dependency findings were addressed before final submission. The remaining moderate PostCSS-related findings are documented as an accepted MVP risk because the suggested `npm audit fix --force` path can install an incompatible or breaking Next.js version. The team will address the remaining moderate findings after the deadline through a tested dependency upgrade branch.

---

## 8.2 Backend Dependency Audit

**Repository checked:**
`https://github.com/Ketishavadze/MusaBackend.git`

**Command used:**

```bash
pip-audit
```

### Initial result

The backend audit initially reported 14 known vulnerabilities in 3 packages:

```txt
django 5.2.14:
- PYSEC-2026-199
- PYSEC-2026-197
- PYSEC-2026-200
- PYSEC-2026-198
- PYSEC-2026-201

pip 25.0.1:
- PYSEC-2026-196
- CVE-2025-8869
- CVE-2026-1703
- CVE-2026-3219
- CVE-2026-6357

pyjwt 2.12.1:
- PYSEC-2026-179
- PYSEC-2026-175
- PYSEC-2026-177
- PYSEC-2026-178
```

### Action taken

The team upgraded the affected backend dependencies:

```txt
Django upgraded from 5.2.14 to 5.2.15
PyJWT upgraded from 2.12.1 to 2.13.0
pip-audit was rerun against the active backend virtual environment by setting PIPAPI_PYTHON_LOCATION to the .venv Python interpreter.
```

### Final backend audit result after remediation

```txt
No known vulnerabilities found
```

### Backend verification

The backend should be checked with:

```bash
python manage.py check
python manage.py migrate
```

Expected result:

```txt
python manage.py check completed successfully.
python manage.py migrate completed successfully.
```

### Backend decision

The backend dependency vulnerabilities were addressed before final submission. No critical or high backend dependency findings remain open.

---

## 9. Secrets Check Result

Secrets were checked in the documentation repository, frontend repository, and backend repository using a recursive PowerShell search for secret-like names.

### Command used

```powershell
Get-ChildItem -Recurse -File |
Where-Object {
    $_.FullName -notmatch "\\.git\\" -and
    $_.FullName -notmatch "\\node_modules\\" -and
    $_.FullName -notmatch "\\.venv\\" -and
    $_.FullName -notmatch "\\.next\\"
} |
Select-String -Pattern "SECRET_KEY|API_KEY|PASSWORD|TOKEN|PRIVATE_KEY|DATABASE_URL"
```

### Patterns searched

```txt
SECRET_KEY
API_KEY
PASSWORD
TOKEN
PRIVATE_KEY
DATABASE_URL
```

### Result

```txt
No production secrets were found in committed files. Matches were limited to documentation examples, environment variable names, local development references, or example configuration fields.
```

### Decision

Production secrets are stored in Render and Cloudflare environment variable settings, not in GitHub. If a real production value is ever found in the repository, the value must be removed from Git history where possible and rotated immediately in the relevant deployment platform.

---

## 10. Accepted MVP Risks

| Accepted risk                             | Reason for acceptance                                                                                    | Future mitigation                                                               |
| ----------------------------------------- | -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| Limited rate limiting                     | MVP traffic is low and deadline is close                                                                 | Add DRF throttling and/or Cloudflare rate rules                                 |
| Limited audit logs                        | MVP focuses on core marketplace functionality                                                            | Add structured logs for login, product edits, and order changes                 |
| Basic creator verification                | Manual creator trust is acceptable for MVP                                                               | Add verified creator badges or moderation                                       |
| Remaining moderate frontend audit finding | No critical/high frontend findings remain; forced fix path risks incompatible downgrade/breaking changes | Resolve through tested dependency upgrade branch after submission               |
| Multiple frontend lockfile warning        | Build still passes and product deploys                                                                   | Remove unnecessary parent lockfile or configure workspace root after submission |
| Manual security review                    | Course timeline is limited                                                                               | Add automated CI security checks later                                          |

---

## 11. Security Review Outcome

The Musa team reviewed the highest-risk product flows using STRIDE and identified the most important security concerns:

1. Account protection
2. Creator ownership checks
3. Private user data isolation
4. Dependency vulnerabilities
5. Secrets management

The team’s final decision is to continue with the MVP because the highest-impact threats are either mitigated through backend authentication/authorization or explicitly accepted as MVP risks with a future mitigation plan.

Before a wider public launch, the next security priorities are:

1. Add backend API throttling for login and write-heavy endpoints.
2. Add stronger upload validation for product images.
3. Add structured audit logging for product and order changes.
4. Add automated dependency scanning in CI.
5. Review all serializers to ensure private fields are never exposed publicly.
6. Clean duplicate frontend lockfiles or configure the Next.js workspace root.
7. Resolve remaining moderate frontend dependency findings through a tested upgrade branch.

---

## 12. Final Decision

The repository satisfies the CP4 security tabletop requirement by documenting:

* STRIDE analysis for 5 highest-traffic / highest-risk user flows
* A mitigation or accepted-risk decision for every STRIDE threat
* Frontend dependency audit results with critical/high findings addressed
* Backend dependency audit results with vulnerabilities remediated
* Secrets check command and result
* Accepted MVP risks with future mitigation plans
