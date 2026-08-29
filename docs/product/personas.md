# Committee Distribution Management — Personas
CDM(Committe Distribution Management) project consists of four roles
1. Admin
2. Operator
3. Beneficiary
4. Super admin
## Super Admin
- Super Admin responsible for managing Dashboard
### Who are they?
- Super Admin are high level user with all permissions
### Goals
- Super Admin Goals are to manage users(Admin, Operator, Beneficiary) of CDM application
### Responsibilities
- Super Admin can create Operator and Beneficiary
- Super Admin can deactivate Operator and Beneficiary
- Super Admin can summary of total beneficiary participated
- Super Admin can generate Reports
- Super Admin can see collected total money

### Pain points
- To manage Admin and other user
- Super Admin not able to manage beneficiary at distribution day
- Super Admin not able to generate token
- Super Admin not add beneficiary at ground level
### Permissions
- ADD_USER
- UPDATE_USER
- DEACTIVATE_USER

### Important screens
- Login
- Dashboard
- Report
- Alerts & notification
---
## Admin
- Admin responsible for managing & monitoring of distribution and having access to add deactivate user, operator
### Who are they?
- Admin can also perform duties of operator
### Goals
- Admin Goals are to manage and monitor the distribution
### Responsibilities
- Admin can create/ deactivate a operator and beneficiary
- Admin can Add/deactivate operator and beneficiary

### Pain points
- To manage distribution in the absence of operator
- Check the status of Beneficier
- Avoid duplication beneficier

### Permissions
- Inherit <OPERATOR_PERMISSIONS>
- ADD_BENEFICIARY
- DEACTIVATE_BENEFICIARY
- UPDATE_PRODUCT_QUANTITY
- TOKEN_REGENERATION
- USER_LIST

### Important screens
- Login
- Dashboard
- create Token
- generate token
- Distribution day
- Queue Management
- Report
- Alerts & notification
---

## Operator
- Operator works at field level with particpant and work closely with participant

### Who are they?
- Operator are ground level staff who works with participants.
- Operator are second level users with limited permissions.
### Goals
- Operator goals are to collect participant infomation and register in CDM application 
### Responsibilities
- Operator can add, update, deactivate beneficiary
- Operator can update their family details
- Operator can create a token
### Pain points
- Handling and verifying beneficier
- searching beneficier and updating status by verifying user token
- updating attendence status of beneficier
### Permissions
- UPDATE_BENEFICIARY_STATUS
- DEACTIVATE_BENEFICIARY
- ADD_BENEFICIARY
- UPDATE_BENEFICIARY
- ADD_BENEFICIARY_DETAILS
- UPDATE_BENEFICIARY_DETAILS
### Important screens
- Login
- Dashboard
- create Token
- generate token
- Distribution day
- Queue Management
- Report
- Alerts & notification
---

## Beneficiary / User
- Beneficiary/ user are participants who are registered to get benefits 
### Who are they?
- Beneficiary are registed users
### Goals
- Beneficiary are users who can benefits to them and their family
### Responsibilities
- Beneficiary need to attend at distribution day with token details to collect distributed products/items
### Pain points
- Beneficiary registration
- Missing token
- Not attending on distribution day
### Permissions
- TOKEN_VIEWER
### Important screens
- token screen
- status
---

## Open Questions

1. Do same admin can login to multiple devices?
2. Do same beneficiary added to multiple families?
3. Do operator can deactivate beneficiary?
4. Do beneficiary need authentication?
5. Do token helps to authenticate without log-in?
6. Do session need to handle with expiry?
7. Do we need password less log-in?
8. Do we have nay screens with out authentication? 