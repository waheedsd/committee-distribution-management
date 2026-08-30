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

Input:
- Operator use beneficiary token details or mobile number to search  

Action: 

System result:
- Operator use beneficiary token details or mobile number to search 
- check the status
- check the quantity 

UX:
- search beneficary using token and mobile number
- find beneficary and token status
- find quantity of product
---

### Step 5 — Token / Beneficiary Identification
- After completing step 4:
- Identify token by scan token or by searching token or beneficiary mobile details


### Step 6 — Eligibility Verification
- After finding token check its details of allocation and find out status of beneficiary token in application 
- Find beneficiary visiting  1st time with valid token or visiting again with expired token

### Step 7 — Allocation Verification
- Allocation verified by checking family members and quatity allocated.

### Step 8 — Payment / Collection
- Optional
- If any Beneficary or any other person interested then he can donate

### Step 9 — Distribution Confirmation
- Confirm the distribution by handover product to beneficiary based on allocation and update same in application 
- After updating status token get expire.
- If token expired expected as beneficiary recevied benefits and product based on allocation.

### Step 10 — Completion
- Once beneficary token is update after receving product token will expire
- In event if distibution completes with all beneficiary then overall distribution completes.
- At the reconcilation happens between total allocation and distribution completed among beneficiary.
---

## 5. Exceptions
- Operator working as field level 
- add all beneficary and family member details
- generating token and sharing to beneficary
- Beneficary atteding on event with token
- operator verify token and allocation details 
- beneficiary receive product and update token by operator
- Once token updated with final status token will expire and beneficiary will not use same token again
- At the end will have summary of event with beneficary attended, product left in quantity, unattended beneficiary and their product quantity, duplicate token and invalid token

### Invalid token
- once beneficary collected product then token gets expire


### Missing token
- on searching token if beneficary is missing then token is missing

### Duplicate token
- It is a corner case
- Duplicate token means on search of token multiple beneficiary found
- In case of mutiple beneficiary verify both details. 
- In this case inform to admin and go to next beneficiary

### Beneficiary not eligible
- If token status is updated and expired then Beneficiary not allowed to take another product.

### Allocation unavailable
- If allocated product and quantity is not available then inform to Admin and find where 

### Already distributed
- If token status is updated with final state and token expire then beneficiary already received product.

## 6. End of Day
- At the end of the event or end of the day all beneficary will get allocated details.

### Reconciliation
- No of beneficary expected to attend at event and allocated details should match at event and all beneficary need to get their benfits 

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
2. Vaid Token with beneficiary on distribution day
3. Allocation of product quantity should be automatic
