# Sprint 1 Plan

**Team:** Nemesis  
**Product:** Art&Craft Platform  
**Sprint:** 1 of 4  
**Dates:** April 24 to May 7, 2026  
**Product Owner:** Ani Kharabadze  
**Scrum Master:** Ketevan Shavadze  
**Version:** 1.0

---

## Sprint Goal

A creator can sign up, create a product listing with a title, category, price, and image, and see it published — end to end — in a deployed application.

---

## Sprint Ceremonies

| Ceremony | When | Where | Who Facilitates |
|----------|------|-------|----------------|
| Sprint Planning | Lab 8, Apr 24/25 | In person | Scrum Master |
| Daily Standup | Daily | Slack channel | Async — each member posts |
| Sprint Review | Week 10, May 7 | Google Meet | Product Owner |
| Retrospective | May 7 or 8 | In person | Scrum Master |

**Async standup format:**
```
Yesterday: [what I completed]
Today: [what I am working on]
Blocker: [anything stopping me — or "none"]
AI note: [what AI generated yesterday and whether it was accepted/modified/discarded]
```

**Blocker escalation:** If a blocker is not resolved within 24 hours, Ketevan Shavadze pings the team in the Slack channel.

---

## Definition of Done

A story is Done when all of the following are true:

- [ ] Code reviewed by at least one other team member (not the original author)
- [ ] Pull request merged to `main` via GitHub PR — no direct pushes to main
- [ ] Acceptance criteria confirmed as met by the Product Owner
- [ ] If AI-generated: code annotated with comments explaining the logic
- [ ] If AI-generated: entry added to `docs/ai-usage-log.md` (tool, task, files changed, review notes)
- [ ] Feature works in the deployed environment, not just locally
- [ ] No known bugs introduced into the main branch

---

## Calibration Anchors

| Points | What It Looks Like for Our Team |
|--------|--------------------------------|
| 1 | A single, obvious change. One file. No logic. Example: change a button label or update a color. |
| 3 | A clear feature with a defined path. Some edge cases. Example: add a form with validation. |
| 5 | A non-trivial feature requiring multiple components or a data layer. Example: image upload with storage. |
| 8 | A complex feature with significant uncertainty. Consider splitting before committing. |

---

## Sprint 1 Backlog

### Story S1-01

**User Story:**  
As a handmade creator, I want to sign up with my email so that I can access the Nemesis platform and start selling.

**Interview Evidence:**  
Source: Interview 05 (Studio138, April 4, 2026) — "I stopped posting because I didn't know what price to put on my products and how to seem more trustworthy without manually following every random profile I came across." — A dedicated platform with real accounts removes the trust problem from the start.

**Story Points:** 3  
**Assignee:** Ani Kharabadze  
**AI Tool:** Google AI Studio  
**AI Tool Rationale:** Good for scaffolding auth forms and backend signup logic quickly.

**Acceptance Criteria:**

```
AC1:
Given I am on the signup screen,
When I enter a valid email and password and submit,
Then my account is created and I am redirected to the creator dashboard.

AC2:
Given I am on the signup screen,
When I submit with an email that is already registered,
Then I see an error message telling me the email is already in use.

AC3:
Given I am on the signup screen,
When I submit with an empty field,
Then I see a validation error and the form is not submitted.
```

**Notes:** Use UUID for user_id — never store email as identifier in events. This event fires `user_signup_completed`.

---

### Story S1-02

**User Story:**  
As a creator, I want to fill in a product title, category, price, and description so that my listing has all the information a buyer needs.

**Interview Evidence:**  
Source: Interview 10 (KK, April 8, 2026) — "Sometimes I feel like I'm either underpricing or overpricing — I don't really know what's correct." — A structured listing form with required fields guides creators toward complete, confident listings.

**Story Points:** 3  
**Assignee:** Tamar Vatcharadze  
**AI Tool:** Google AI Studio  
**AI Tool Rationale:** Good for generating form components with validation logic.

**Acceptance Criteria:**

```
AC1:
Given I am on the Create Listing screen,
When I fill in title, category, price, and description and click Save Draft,
Then my listing is saved and I can see it in My Listings as a draft.

AC2:
Given I am on the Create Listing screen,
When I try to publish with a missing required field (title or price),
Then I see an inline validation error and the listing is not published.

AC3:
Given I have filled in all required fields,
When I click Publish Listing,
Then the listing is saved and marked as active.
```

**Notes:** Category should be a dropdown matching the prototype: All Crafts, Crochet, Jewelry, etc. Price must be a positive number. This is a step toward firing `listing_completed`.

---

### Story S1-03

**User Story:**  
As a creator, I want to upload an image for my listing so that buyers can see what my product looks like.

**Interview Evidence:**  
Source: Interview 02 (Meg, April 7, 2026) — "I thought about creating an Instagram page, but then I realized I'd have to post regularly, gain followers, take pictures, write stories… it just seemed like too much work." — A simple, built-in image upload removes one of the biggest friction points creators associate with selling online.

**Story Points:** 5  
**Assignee:** Ani Kharabadze  
**AI Tool:** Google AI Studio  
**AI Tool Rationale:** Useful for generating upload component and storage integration boilerplate.

**Acceptance Criteria:**

```
AC1:
Given I am on the Create Listing screen,
When I click the image upload area and select a PNG or JPG file under 10MB,
Then the image is uploaded and previewed in the listing form.

AC2:
Given I have uploaded an image and filled all required fields,
When I click Publish Listing,
Then the listing is saved with the image and marked as active.

AC3:
Given I try to upload a file that is not an image,
Then I see an error message and the file is rejected.
```

**Notes:** `has_image: true` must be included in the `listing_completed` event payload. Max file size 10MB. Accepted types: PNG, JPG.

---

### Story S1-04

**User Story:**  
As a creator, I want to see a confirmation screen after publishing my listing so that I know it went live successfully.

**Interview Evidence:**  
Source: Interview 09 (DA, April 8, 2026) — "I feel like I need everything to be perfect before I start, so I keep delaying it." — A clear confirmation moment gives creators positive feedback and reduces the anxiety around publishing.

**Story Points:** 1  
**Assignee:** Gvantsa Nozadze  
**AI Tool:** None  
**AI Tool Rationale:** Simple screen render — no AI needed.

**Acceptance Criteria:**

```
AC1:
Given I have successfully published a listing,
When the publish action completes,
Then I see a confirmation screen with the message "Your handmade item is now live" and a button to go to My Studio.

AC2:
Given I am on the confirmation screen,
When I click "Go to My Studio",
Then I am redirected to my creator dashboard showing the new listing.
```

**Notes:** This is the moment `listing_completed` fires. Match the prototype copy: "Your handmade item is now live ✨".

---

### Story S1-05

**User Story:**  
As a creator, I want to see my published listings in My Studio so that I can track what I have listed.

**Interview Evidence:**  
Source: Interview 04 (M.P., April 3, 2026) — "I'd like a simpler system where orders, payments and customer communication are all in one place." — A central dashboard where creators can see their listings is the first step toward the organized workspace creators need.

**Story Points:** 3  
**Assignee:** Gvantsa Nozadze  
**AI Tool:** Google AI Studio  
**AI Tool Rationale:** Useful for generating dashboard list components with dynamic data.

**Acceptance Criteria:**

```
AC1:
Given I have published at least one listing,
When I open My Studio,
Then I can see my listings with their title, price, category, and status (active/draft).

AC2:
Given I have no listings yet,
When I open My Studio,
Then I see an empty state with a prompt to create my first listing.
```

**Notes:** Active listings count feeds into the NSM tracking. Status should clearly distinguish draft vs active.

---

## Sprint 1 Summary

| Story ID | Summary | Points | Assignee | AI Tool | Status |
|----------|---------|--------|----------|---------|--------|
| S1-01 | Creator signup with email | 3 | Ani Kharabadze | Google AI Studio | Not started |
| S1-02 | Create listing form (title, category, price, description) | 3 | Tamar Vatcharadze | Google AI Studio | Not started |
| S1-03 | Image upload for listing | 5 | Ani Kharabadze | Google AI Studio | Not started |
| S1-04 | Listing published confirmation screen | 1 | Gvantsa Nozadze | None | Not started |
| S1-05 | My Studio — view published listings | 3 | Gvantsa Nozadze | Google AI Studio | Not started |
| **Total** | | **15** | | | |

**Capacity check:** 15 points committed. Target is 60% or below maximum capacity — adjust if team estimates max at 20–25 points.

---

## Sprint Review Criteria

At Sprint Review (May 7, Google Meet), the team will demo:

1. A new creator signs up with email and lands on the dashboard
2. The creator fills in a listing form (title, category, price, image) and publishes it
3. The confirmation screen appears and the listing shows up in My Studio

The demo must be live. No screenshots. No pre-recorded video. The application runs in front of the reviewer.

---

## AI Usage Log Reference

All AI-assisted work in Sprint 1 must be logged in `docs/ai-usage-log.md`.

Entry format:
```
Date: [YYYY-MM-DD]
Story: [Story ID and summary]
Tool: [Tool name]
Task: [What AI was asked to do]
Files changed: [List of files]
Accepted / Modified / Discarded: [Which]
Review notes: [What was checked, what was changed from the AI output]
Reviewer: [Name]
```

---

## Change Log

| Date | Changes | Author |
|------|---------|--------|
| April 24, 2026 | Sprint 1 plan created | Nemesis Team |

---

*Sprint 1 Plan | Nemesis | CS-PD-2026 | Spring 2026*