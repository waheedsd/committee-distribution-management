# Distribution-Day User Journey

## 1. Purpose

This document describes the end-to-end journey for preparing a distribution event, preparing beneficiary allocations and tokens, distributing the product on distribution day, handling exceptions, and completing end-of-day reconciliation and audit.

The current MVP supports one product/item per distribution event. The journey is intentionally written at the business level so future distribution types can be supported without changing the core beneficiary, allocation, token, and distribution concepts.

## 2. Actors

- Super Admin
- Admin
- Operator
- Beneficiary / family representative

## 3. Before Distribution

Before the actual distribution day, the Operator visits beneficiary locations, collects beneficiary and family details, prepares the allocation, generates a token, and shares the token with the family representative. Any one person from the family may collect the allocated product on distribution day by presenting the family token or using the registered mobile number for lookup.

### Step 1 — Create Distribution Event

**Actor:** Admin

**Input:**
- Distribution date
- Distribution location
- Expected number of beneficiaries
- One product/item for the event
- Product quantity
- Other event details, if required

**Action:** Admin creates the distribution event.

**System result:** Distribution event is created with its date, location, product and quantity details.

**UX:** Show distribution date, location, product/item, quantity, expected beneficiaries, and event status.

### Step 2 — Prepare Allocation

**Actor:** Operator

**Input:**
- Beneficiary name
- Registered mobile number
- Optional alternate mobile number
- Number of family members

**Action:** Operator records beneficiary/family details. The system automatically calculates the product quantity according to the committee-approved allocation rule.

**System result:** Beneficiary is associated with the distribution event and receives an allocation for the event.

**UX:** Beneficiary details form, family member count, calculated allocation quantity, and allocation status.

### Step 3 — Generate / Prepare Token

**Actor:** Operator / System

**Input:** Beneficiary allocation.

**Action:** System generates a unique 5-character token and Operator shares it with the family representative, instructing them to bring the token on distribution day.

**System result:** Token is associated with the family's allocation for the distribution event.

**Token purpose:** The 5-character token identifies the family's allocation for a specific distribution event. For the MVP, token generation may incorporate a unique identifier and date/time information. The generation mechanism can be improved later without changing the token's business purpose.

**UX:** Display the token clearly and provide an appropriate way for the Operator to share it.

---

## 4. Distribution Day

On distribution day, a beneficiary/family representative arrives at the event location. Any one person from the family can collect the product on behalf of the family.

### Step 4 — Beneficiary Arrives

**Actor:** Beneficiary / family representative

**Intent:** Present the token and collect the allocated product.

**Input:**
- 5-character token, or registered mobile number if the token is unavailable

**Action:** Beneficiary presents the token to the Operator.

**System result:** Operator can locate the family's beneficiary, allocation, and distribution information.

**UX:** Operator-facing search/identification screen.

### Step 5 — Token / Beneficiary Identification

**Actor:** Operator

**Action:** Operator identifies the family using either the token or registered mobile number.

**System result:** System displays the matching beneficiary/family, distribution event, allocation, and relevant status.

**UX:** Search by token/mobile number and display beneficiary, family, event, and allocation details.

### Step 6 — Eligibility Verification

**Actor:** Operator + System

**Rule:** Eligibility is decided separately for each distribution event by the committee. Being registered/approved does not by itself mean the beneficiary is eligible for every event.

**Action:** System verifies that the beneficiary/family is eligible for the current distribution event. Operator verifies the displayed beneficiary details.

**Normal identity verification:** Token or registered mobile number plus beneficiary details displayed by the system is sufficient for normal verification.

**If another family member/person arrives:** Operator verifies the available beneficiary details. If additional remarks or a photo are required for an exception, they may be recorded according to committee policy.

### Step 7 — Allocation Verification

**Actor:** Operator + System

**Action:** System displays the allocation for the current event. Operator verifies the family/member details and allocated quantity before handing over the product.

**System result:** Operator knows exactly what quantity is expected to be distributed.

### Step 8 — Payment / Collection

Distribution itself does not require payment.

An optional donation can be recorded separately. Anyone may make a donation; it does not need to be associated with the beneficiary or distribution.

Optional donor details:
- Name
- Mobile number
- Image

Donation amount is required when a donation is recorded.

### Step 9 — Distribution Confirmation

**Actor:** Operator + System

**Action:** Operator hands over the product according to the verified allocation and confirms the distribution in the application.

**System result:** System records the actual distribution with:
- Distribution event
- Beneficiary/family
- Allocation
- Quantity distributed
- Operator details
- Date and time

The same allocation must not be distributed again during the same event.

**Important:** Distribution completion is recorded as a distribution outcome. Token status must not be treated as the only source of truth for whether the product was actually distributed.

### Step 10 — Completion

When the distribution is confirmed, the allocation is treated as distributed and cannot be distributed again for the same event.

When the event finishes, the system supports reconciliation between expected beneficiaries, allocations, actual attendance, completed distributions, remaining quantity, uncollected allocations, exceptions, and donations.

---

## 5. Exceptions

### Invalid token

If the token cannot be validated, Operator must not distribute the product using that token. Operator can use the registered mobile number to locate the beneficiary and verify the allocation where appropriate.

### Missing token

If the beneficiary has lost or does not have the token, Operator can search using the registered mobile number and review the beneficiary/allocation details before proceeding according to the verification rules.

### Duplicate token

A duplicate token is a corner case where the same token appears to identify multiple beneficiaries/allocations.

- Do not distribute until the conflict is resolved.
- Operator verifies the displayed details.
- Inform Admin for resolution.
- Record the exception if required.

### Beneficiary not eligible

If the beneficiary is not eligible for the current distribution event, the Operator must not distribute the allocated product.

A previously completed allocation is also not eligible for another distribution during the same event.

### Allocation unavailable

If the allocated product or quantity is unavailable, Operator informs Admin and follows the committee-approved shortage policy.

**Pending committee decision:** Whether partial distribution is allowed and, if so, how the actual quantity should be recorded.

### Already distributed

If the allocation has already been completed for the current event, the system must prevent another distribution and show that the allocation has already been distributed.

### Network / system failure

If the system cannot confirm the distribution because of a network or system failure, Operator must not assume that the distribution was recorded. The final implementation must safely handle retries and prevent duplicate distribution records.

### Uncollected allocation / reallocation

If a beneficiary does not attend:
1. Committee first contacts the beneficiary.
2. If the beneficiary remains unavailable, the product may be considered for a new beneficiary according to committee policy.

**Pending committee decision:**
- Who is allowed to perform the reallocation?
- What status should the original allocation receive?
- How should the relationship between the original and new allocation be recorded and audited?

---

## 6. End of Day

### Reconciliation

The event should be reconciled using at least:

- Total beneficiaries expected
- Total allocations
- Total beneficiaries attended
- Total distributions completed
- Total quantity distributed
- Total quantity remaining
- Uncollected allocations/beneficiaries
- Exceptions
- Donations

The reconciliation should make it possible to compare planned/allocated quantities with actual distributed quantities.

### Uncollected allocations

Identify uncollected allocations and flag them for follow-up according to committee policy. The final reallocation policy is pending committee confirmation.

### Reporting

Generate a summary containing:
- Total expected beneficiaries
- Total allocations
- Total attended
- Total distributed
- Quantity distributed
- Quantity remaining
- Uncollected beneficiaries and allocations
- Exceptions
- Donation summary
- Beneficiary/allocation status and relevant operator details

### Audit

The system should retain an audit trail for important actions, including:
- Who created a beneficiary
- Who changed family/member count
- Who generated a token
- Who changed an allocation
- Who completed a distribution
- Who performed any approved reallocation or exception resolution

Distribution records should also retain the operator and date/time of the action.

---

## 7. Open Questions / Pending Committee Decisions

1. Product shortage: Is partial distribution allowed? If yes, how is the actual quantity handled?
2. Uncollected allocation: Who can reallocate it to a new beneficiary?
3. Uncollected allocation: What happens to the original allocation when it is reallocated?
4. Uncollected allocation: What audit information is required for reallocation?
5. Future product types: Should the same beneficiary/token/allocation/distribution journey support grocery, clothing, and other distribution types? This is outside the current MVP scope.

---

## 8. Assumptions / Current MVP Decisions

1. A distribution event has a required date and location.
2. The MVP supports one product/item per distribution event.
3. Eligibility is decided separately for each distribution event by the committee.
4. One token is issued per family allocation for the event.
5. Any one person from the family may collect the allocation.
6. The token contains 5 characters and is used to identify the family's allocation for the event.
7. Token generation currently incorporates unique identifier and date/time information and may be improved later.
8. Token/mobile lookup plus displayed beneficiary details is sufficient for normal identity verification.
9. Allocation quantity is automatically calculated using the committee-approved allocation rule.
10. Distribution does not require payment; donations are optional and independent.
11. Duplicate distribution of the same allocation during the same event is not allowed.
12. Product management/selection is outside the current MVP scope.
13. Reallocation rules are pending committee confirmation.
