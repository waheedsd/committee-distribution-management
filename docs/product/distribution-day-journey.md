# Distribution-Day User Journey

## 1. Purpose

This document explains about end-end journey from token distribution to beneficiary.
Beneficiary attending to distribution day with valid token and collecting product which is mentioned in the application and with quantity and state management about happy path and unhappy path.


## 2. Actors

- Super Admin
- Admin
- Operator
- Beneficiary

## 3. Before Distribution

Before starting actual distribution of product, CDM operator visits beneficiary location.
collect the beneficiary and family details and add a record in the application.
Generates a token and share to beneficiary by informing to bring this token on distribution day.

### Step 1 — Create Distribution Event

Actor: Admin 

Input: 
- Distribution Date, 
- Distribution Type or product name or description, 
- Quantity, 
- other event details

Action: 

System result: Event created with distribution details

UX: Distribution details with Product name and details, quantity, Distribution date.

### Step 2 — Prepare Allocation

Actor: Operator

Input: 
- Collect Beneficiary details before distribution details.
- collect Beneficiary name, mobile number, if possible alternate number
- collect No of family members
- Automatically allocate product quantity


Action:

System result: Operator visit beneficary location, collect beneficary details.

UX: 
- Collecting beneficiary deatils
- Token generation 
- sharing token to beneficiary

### Step 3 — Generate / Prepare Token

Actor: Operator

Input:
- Generate token 
- share token to benficieary 

Action:

System result: Token Generation and sharing to beneficary

UX: 
- Token generation 
- sharing token to beneficiary
---

## 4. Distribution Day
- On Distribution day Beneficiary arrives at event location with token details
- Verifies token 
- collect product.
- operator verify beneficiary token
- update token 
- Handover product to beneficary

### Step 4 — Beneficiary Arrives

Actor: Beneficiary

Intent: show Token and collect the product

Input:
- beneficiary token

Action: 

System result:
- Beneficiary shows token to operator
- Token verification
- collect product

UX:
- Token sync/verification
- Token status update
---

Actor: Operator

Intent: Operator search beneficiary details by token number/ mobile number and check the product and quantity 
handover product to beneficiary

Input:
- Operator use beneficiary token details or mobile number to search  
- update status of token to Distribution completed

Action: 

System result:
- Operator use beneficiary token details or mobile number to search 
- check the status
- check the quantity 
- update status of token to Distribution completed
UX:
- search beneficary using token and mobile number
- find beneficary and token status
- find quantity of product
- update token after distribution completes
---
### Step 5 — Token / Beneficiary Identification
- Token/ Beneficiary identy by searching in application and its status

Status of token:
INITIALIZE - Entering beneficary details but it is draft state
ACTIVE - beneficary activated
VERIFIED - token/beneficary verified
COLLECTED - distribution completed

### Step 6 — Eligibility Verification
- If token status is not COLLECTED then beneficiary is elgible.

### Step 7 — Allocation Verification
- If token status is VERIFIED then allocation is verified.

### Step 8 — Payment / Collection
- Optional
- If any Beneficary or any other person interested then he can donate

### Step 9 — Distribution Confirmation
- Update token status to COLLECTED to confirm distribution

### Step 10 — Completion
- If token status is COLLECTED then distribution is completed.
---

## 5. Exceptions

### Invalid token
If token is invalid with not VERIFIED status then check with beneficiary mobile number and search in application 
If still not exist check with Admin to take future action.

### Missing token
If token is missing and able to find details with mobile number then 
regenerate token and update its status.

### Duplicate token
If duplicate token then verify with mobile number.
If mobile number is different and beneficary is different.
Deactivate one token.
regenerate new token to another user

### Beneficiary not eligible
If token status is distribution completed then Beneficiary not allowed to take another product.

### Allocation unavailable

### Already distributed
If token status is COLLECTED then beneficiary already received product.


## 6. End of Day

### Reconciliation


### Uncollected allocations
- Reach out to beneficiary and possible distribute product and update status of token to COLLECTED

### Reporting
- Generate a report with total token, quantity, attended on event and quantity of product distributed
- left over quantity and no of beneficiary
- list of beneficiary and their quantity and status with operator details

### Audit
- log each action of operator, admin and super admin to track his actions
---

## 7. Open Questions

1. Beneficiary can provide same mobile number to different families but each family have a unique token number
2. Beneficiary can absent to collect the product on distribution day
3. Operator can enter typo mistake.
4. Network latency
5. token can be QR code or 5 charaters

## 8. Assumptions

1. Each family have unique beneficiary
2. updating status of token with out idempotency
3. Allocation of product quantity should be automatic
