# Tenant Management App - Workflows & UML Diagrams

## 1. User Registration & Onboarding Workflows

### Property Owner Registration Flow
```
Start → Email/Password Entry → Email Verification → Profile Setup → 
Property Addition → Room Configuration → Photo Upload → Dashboard Access
```

**Detailed Steps:**
1. **Registration Form** → Validate email uniqueness → Send verification email
2. **Email Verification** → Activate account → Redirect to profile setup
3. **Profile Setup** → Basic info (name, phone, address) → Upload profile photo
4. **Property Addition** → Property details form → Address validation
5. **Room Configuration** → Add rooms → Set rent amounts → Upload photos
6. **Dashboard Access** → Welcome tour → Ready to use

### Tenant Onboarding Flow
```
Owner Creates Tenant Record → System Sends Invitation → Tenant Registration → 
Profile Completion → Document Upload → Lease Agreement → Portal Access
```

**Detailed Steps:**
1. **Owner Initiates** → Fill tenant basic info → Select room → Set lease terms
2. **System Generated Invitation** → Email with secure link → Temporary password
3. **Tenant Registration** → Password setup → Accept terms
4. **Profile Completion** → Personal details → Emergency contacts → Employment info
5. **Document Upload** → ID verification → References → Bank details
6. **Lease Agreement** → Review terms → Digital signature → Final confirmation
7. **Portal Access** → Welcome message → Feature overview

## 2. Property Management Workflows

### Adding New Property Flow
```
Dashboard → Add Property → Property Details Form → Address Verification → 
Room Addition → Photo Upload → Review & Save → Property Dashboard
```

### Room Management Flow
```
Property View → Add/Edit Room → Room Details → Rent Setting → 
Photo Upload → Amenities Selection → Availability Status → Save
```

### Property Maintenance Flow
```
Issue Reported → Create Maintenance Request → Assign Vendor → 
Schedule Work → Update Status → Mark Complete → Generate Report
```

## 3. Financial Management Workflows

### Rent Collection Flow
```
Monthly Trigger → Generate Invoices → Send Notifications → 
Payment Recording → Status Update → Receipt Generation
```

**Automated Process:**
1. **Monthly Trigger** (1st of month) → System generates invoices for all active leases
2. **Notification Dispatch** → Email invoices to tenants → SMS reminders
3. **Payment Recording** → Owner marks payment received → System updates status
4. **Receipt Generation** → Auto-generate receipt → Email to tenant

### Manual Payment Recording Flow
```
Finance Dashboard → Select Tenant → Enter Payment Details → 
Validate Amount → Update Records → Generate Receipt → Send Confirmation
```

### Invoice Generation Flow
```
Select Tenant/Lease → Choose Invoice Template → Add Line Items → 
Calculate Totals → Preview Invoice → Generate PDF → Send to Tenant
```

## 4. Communication Workflows

### Notification System Flow
```
Event Trigger → Notification Creation → Priority Assessment → 
Delivery Channel Selection → Send Notification → Track Delivery → Update Status
```

### Maintenance Request Flow
```
Tenant Submits Request → Owner Notification → Issue Assessment → 
Vendor Assignment → Schedule Work → Progress Updates → Completion Confirmation
```
