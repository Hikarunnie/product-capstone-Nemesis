# Event Schema

**Team:** Nemesis  
**Product:** Nemesis Platform  
**Date:** April 15, 2026  
**Version:** 1.0  
**Status:** Blueprint (instrumentation in Lab 6)

---

## North Star Metric

> Weekly successfully managed product listings per active creator

**Activation event that drives NSM:** `listing_completed`

---

## Universal Properties

Every event automatically includes these properties. Do not repeat them in individual event definitions.

| Property | Type | Description |
|----------|------|-------------|
| `user_id` | string (UUID) | System-generated user identifier. Never an email address. |
| `timestamp` | ISO 8601 datetime | When the event fired. Always include timezone (Z for UTC). |
| `session_id` | string (UUID) | The session in which the event occurred. |
| `platform` | enum: web, ios, android | The platform the event was fired on. |

---

## Event Definitions


### ACQUISITION

---

#### `user_signup_completed`

**AARRR Stage:** Acquisition  
**Description:** User successfully creates an account  
**Fires when:** Registration is completed successfully  
**NSM connection:** None — acquisition only
**Rationale:** Tracks successful account creation, which is the first step in acquisition before any onboarding or product usage.

| Property | Type | Required | Description | Example |
|----------|------|----------|-------------|---------|
| `signup_method` | enum | Yes | Method used to sign up | `"email"` |
| `user_role` | enum | Yes | Type of user | `"creator"` |

---

### ACTIVATION

---

#### `onboarding_started`

**AARRR Stage:** Activation  
**Description:** User begins onboarding process  
**Fires when:** First onboarding screen is opened  
**NSM connection:** Indirect — leads to listing creation
**Rationale:**Captures entry into onboarding, which is the first behavioral signal of activation intent.
| Property | Type | Required | Description | Example |
|----------|------|----------|-------------|---------|
| `entry_source` | string | Yes | Where user came from | `"instagram"` |
| `step_number` | integer | No | Current onboarding step | `1` |

---

#### `onboarding_completed`

**AARRR Stage:** Activation  
**Description:** User completes onboarding  
**Fires when:** Final onboarding step is submitted  
**NSM connection:** Enables listing creation
**Rationale:** Confirms user has completed setup, enabling them to create listings.
| Property | Type | Required | Description | Example |
|----------|------|----------|-------------|---------|
| `profile_completed` | boolean | Yes | Profile fully completed | `true` |
| `onboarding_time_seconds` | integer | No | Time to complete onboarding | `120` |

---

#### `listing_created`

**AARRR Stage:** Activation  
**Description:** User starts creating a product listing  
**Fires when:** "Create Listing" button is clicked  
**NSM connection:** Step toward NSM
**Rationale:** Tracks intent to create a product listing, the first step toward activation.
| Property | Type | Required | Description | Example |
|----------|------|----------|-------------|---------|
| `listing_id` | string | Yes | Unique listing ID | `"lst_123"` |
| `category` | string | Yes | Product category | `"crochet"` |

---

#### `listing_completed` ← ACTIVATION EVENT (NSM DRIVER)

**AARRR Stage:** Activation  
**Description:** User successfully completes and saves a listing  
**Fires when:** Listing is saved with required fields (title, price, image)  
**NSM connection:** Each `listing_completed` event increments the weekly count of successfully managed listings per user.
**Rationale:** Core activation event that measures successful creation of a usable listing and drives the North Star Metric.
| Property | Type | Required | Description | Example |
|----------|------|----------|-------------|---------|
| `listing_id` | string | Yes | Unique listing ID | `"lst_123"` |
| `price_set` | float | Yes | Final product price | `25.0` |
| `has_image` | boolean | Yes | Whether image was uploaded | `true` |
| `category` | string | No | Product category | `"crochet"` |

**Example payload:**
```json
{
  "event_name": "listing_completed",
  "user_id": "user_abc123",
  "timestamp": "2026-04-15T14:23:45Z",
  "session_id": "sess_xyz789",
  "platform": "web",
  "listing_id": "lst_123",
  "price_set": 25.0,
  "has_image": true,
  "category": "crochet"
}
```

---

### RETENTION

---

#### `user_session_started`

**AARRR Stage:** Retention  
**Description:** User returns to the app  
**Fires when:** App/dashboard is opened  
**NSM connection:** Tracks returning creators
**Rationale:** Tracks returning users and overall retention behavior.
| Property | Type | Required | Description | Example |
|----------|------|----------|-------------|---------|
| `device_type` | string | Yes | Device used | `"mobile_web"` |
| `session_number` | integer | No | Session count | `5` |

---

#### `listing_updated`

**AARRR Stage:** Retention  
**Description:** User edits an existing listing  
**Fires when:** Changes are saved  
**NSM connection:** Improves listing quality → supports successful listings
**Rationale:** Measures post-creation engagement and improvements to listing quality.
| Property | Type | Required | Description | Example |
|----------|------|----------|-------------|---------|
| `listing_id` | string | Yes | Listing ID | `"lst_123"` |
| `fields_updated` | array | No | Updated fields | `["price", "description"]` |

---

### REFERRAL

---

#### `listing_shared`

**AARRR Stage:** Referral  
**Description:** User shares a listing externally  
**Fires when:** Share button is clicked  
**NSM connection:** Indirect — may drive traffic to listings
**Rationale:** Captures referral behavior when users distribute listings externally.
| Property | Type | Required | Description | Example |
|----------|------|----------|-------------|---------|
| `listing_id` | string | Yes | Listing ID | `"lst_123"` |
| `share_channel` | enum | Yes | Sharing method | `"instagram"` |

---

## Event Summary Table

| Event Name | AARRR Stage | Priority | NSM Driver |
|-----------|-------------|----------|-----------|
| `user_signup_completed` | Acquisition | Must | No |
| `onboarding_started` | Activation | Must | No |
| `onboarding_completed` | Activation | Must | No |
| `listing_created` | Activation | Must | No |
| `listing_completed` | Activation | Must | **YES** |
| `user_session_started` | Retention | Must | Indirect |
| `listing_updated` | Retention | Should | Indirect |
| `listing_shared` | Referral | Should | No |

**Total events:** 8  
**Must-have events:** 6  
**Should-have events:** 2

---

## Privacy Confirmation

- [x] No email addresses in any event property
- [x] No user names or display names in any event property
- [x] No phone numbers in any event property
- [x] No physical addresses in any event property
- [x] No payment card details in any event property
- [x] All user identification uses system-generated UUIDs only

**Schema reviewed by:** Nemesis Team on April 15, 2026

---

## Instrumentation Notes for Lab 6

| Event Name | Where in Code | Frontend or Backend |
|-----------|--------------|-------------------|
| `user_signup_completed` | After signup success | Backend |
| `onboarding_started` | First onboarding screen load | Frontend |
| `onboarding_completed` | Final onboarding submit | Frontend |
| `listing_created` | Create button click | Frontend |
| `listing_completed` | After successful save | Frontend |
| `user_session_started` | App open / dashboard load | Frontend |
| `listing_updated` | Save edit action | Frontend |
| `listing_shared` | Share button click | Frontend |

---

## Analytics Tool Selection

- [ ] Mixpanel
- [ ] Amplitude
- [x] PostHog
- [ ] Google Analytics 4

**Our choice:** PostHog 
**Reason:** Event-based tracking, strong free tier, easy integration for MVP 
**Free tier limit:** Generous for early-stage usage

---

## Change Log

| Date | Version | Changes | Author |
|------|---------|---------|--------|
| April 15, 2026 | 1.0 | Initial schema blueprint | Nemesis Team |

---

*Event Schema | Nemesis | CS-PD-2026 | Spring 2026*