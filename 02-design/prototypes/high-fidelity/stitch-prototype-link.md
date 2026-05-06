# High-Fidelity Prototype: Stitch

**Team:** [Nemesis]  
**Product:** Craft Market  
**Tool:** Google Stitch  
**Created:** [5/6/2026]  
**Status:** Draft

---

## Prototype Link

**Stitch shareable link:**  
[https://stitch.withgoogle.com/projects/2247648172852572160]

---

## What This Prototype Covers

**Core user flow prototyped:**  
The prototype shows a handmade craft marketplace where buyers can browse products, while creators can access their studio and complete the main activation flow by creating and publishing a new product listing.

### Screens included

| Screen | Purpose | Activation Event Fired |
|---|---|---|
| Marketplace / Craft Market | Buyer browses handmade products, searches, filters, and views product cards. | None |
| Cart | Buyer reviews selected products and proceeds toward checkout. This supports the secondary buyer behavior. | None |
| My Studio | Creator views their workspace, active listings, earnings, and starts creating a new listing. | None |
| Create Listing | Creator uploads product images, enters product title, category, price, and description, then publishes the listing. | `listing_completed` |
| Profile | User accesses creator-related options such as My Studio, My Listings, Settings, and Become a Seller. | None |

**Activation moment screen:**  
Create Listing

**What the user does at activation:**  
The user taps **“Publish Listing”** after completing the product listing form.

**NSM connection:**  
The activation event `listing_completed` directly supports the North Star Metric because every completed listing increases the number of products available on the marketplace. More listings create more value for buyers, improve marketplace variety, and show that creators are successfully adopting the platform.

---

## Stitch Brief Used


**Product name:**  
Nemesis Craft Market

**Primary user:**  
Handmade creators who want a simple way to sell their products online, especially creators who already make crafts such as crochet items, jewelry, accessories, and handmade decorations.

**Most important flow:**  
Creator activation flow: Marketplace → Seller/Studio entry point → Create Listing → Publish Listing.

**Screens required:**

1. Marketplace / Craft Market feed
2. Cart screen
3. Creator workspace / My Studio
4. Create Listing form
5. Profile / Seller entry screen

**Activation moment:**  
The activation moment happens when the creator successfully publishes a new product listing by tapping **“Publish Listing.”**

**Visual style:**  
Soft handmade marketplace aesthetic with rounded cards, warm cream backgrounds, pastel pink listing cards, earthy green buttons, clean mobile-first layout, and product-focused imagery. The design should feel friendly, creative, cozy, and simple enough for beginner sellers.

---

## Key Prompts Used

### Initial prompt

Design a high-fidelity mobile-first marketplace app called “Nemesis Platform” for creators and buyers. The app has two user behaviors:

- Buyers browsing and purchasing products
- Creators creating product listings

However, the primary focus is creator activation, where the key event is:

`listing_completed`

The design should support browsing and buying, but the core evaluated flow must remain listing creation.

Create a scrollable marketplace feed with product cards, search, filter chips, and a clear seller entry point. Include a creator workspace, a create listing form, and a success/activation moment after publishing. Use a modern mobile marketplace style with rounded cards, soft colors, and minimal clutter.

### Iteration prompts

Make the app feel more handmade, cozy, and craft-focused instead of a generic SaaS marketplace. Use soft cream backgrounds, pastel pink cards, earthy green buttons, and rounded mobile UI components.

Update the marketplace screen so it looks like a craft market. Show handmade products such as crochet tops, jewelry, bowls, cardigans, press-on nails, and accessories. Keep the product cards image-heavy with title, price, and an Add button.

Add a creator dashboard called “My Studio” where sellers can manage their listings, see active products, and start creating a new listing. Make “Create New Listing” the most important CTA on this screen.

Create a clean listing creation form. Include product image upload, product title, category dropdown, price input, description field, Save Draft, and Publish Listing. Make the Publish Listing button visually dominant because this is the activation event.

Add a cart screen to support the buyer flow, but keep it secondary. Show selected handmade items, order summary, checkout button, and small marketplace-related details like gift wrapping or matched yarn.

Add a profile screen with creator-related navigation such as My Studio, My Listings, Settings, Logout, and Become a Seller. Make it feel consistent with the rest of the app.

Refine the navigation bar so the main app sections are Explore, Cart, My Studio, and Profile. Use highlighted green pills to show the active tab.

Make the product cards and studio listing cards match the handmade brand identity. Use real-looking craft images, rounded corners, soft shadows, and small status tags like Active or New.

---

## Design Decisions

**Decision 1:**  
We made **Create New Listing** the main button in the creator workspace because our interview findings showed that creators often know how to make products but do not always know what to do after posting or how to structure the selling process. A clear listing workflow helps reduce confusion and guides them toward the activation event.

**Decision 2:**  
We kept the listing form simple with only the most important fields: product images, title, category, price, and description. This connects to the insight that beginner handmade sellers can feel uncertain or overwhelmed when selling online. A simple form makes listing creation feel faster and less intimidating.

**Decision 3:**  
We used a warm handmade visual style with soft colors, craft images, rounded cards, and creator-focused language because the product is meant for handmade creators, not mass-market sellers. The UI should feel personal, creative, and trustworthy so creators feel like the platform fits their work.

---

**Stitch Prototype | [Nemesis] | CS-PD-2026 | Spring 2026**