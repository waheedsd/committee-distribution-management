# Distribution-Day User Journey

## 1. Purpose

This document explains about end-end journey from token distribution to beneficiray.
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
- Generate token 
- share token to benficieary 

Action:

System result: Operator visit beneficary location, collect beneficary details and generate token and share same token to benficiary

UX: 
- Collecting beneficiary deatils
- Token generation 
- sharing token to beneficiary

### Step 3 — Generate / Prepare Token

Actor: Operator

Input:
- collect Beneficiary name, mobile number, if possible alternate number
- collect No of family members
- Automatically allocate product quantity
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
- Token verfication
- collect product

UX:
- Token sync/verfication
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

### Step 6 — Eligibility Verification
- If token status is changed to distribution completed then beneficiary not elgible
- If token status is still active then beneficiary is elgible.

### Step 7 — Allocation Verification
- Allocation verfication can be done by checking product quantity in application 

### Step 8 — Payment / Collection
- Optional
- If any Beneficary or any other person interested then he can donate

### Step 9 — Distribution Confirmation
- Distribution confirms by updating token status as of now.

### Step 10 — Completion
- Distrbution complete by handover product and updating token status to distribution complete
---

## 5. Exceptions

### Invalid token
If token is invalid then check with beneficiary mobile number and search in application 
If still not exist check with Admin to take furthur action.

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

### Payment mismatch

### Network/system failure
In case of Network failure should update status localy
and when network connects it should check status of db and 
create a copy of db and update records in db 

- verify any conflicts manually at initial stages and then merge to one single DB
---

## 6. End of Day

### Reconciliation

### Uncollected allocations

### Reporting

### Audit
- log each action of operator, admin and super admin to track his actions
---

## 7. Open Questions

1. 
2.
3.
4.
5.

## 8. Assumptions

1.
2.
3.
