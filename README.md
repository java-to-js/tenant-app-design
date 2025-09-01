# Tenant Management App - Design Document

## App Overview
A tenant management application for homeowners who rent rooms for long-term stays. This is an administrative tool focused on managing existing tenant relationships, not a marketplace for finding tenants.

## Key Features Identification

### Core User Roles
- **Property Owner/Landlord**: Primary user who manages properties and tenants
- **Tenant**: Secondary user with limited access to their own data

### Essential Features
1. **Property Management**
   - Register and manage multiple properties
   - Add/edit room details with photos
   - Manage additional utilities comes with room ( AC, Heater etc)
   - Set rent amounts and electricity bill rate
   - Track room availability status
   - Track room maintaninace

   Property = collection of rooms in a single building

2. **Tenant Management**
   - Onboard new tenants
   - Maintain tenant profiles and documents
   - Track lease agreements and terms
   - Manage tenant communication (future)

3. **Financial Management**
   - Rent collection tracking / stats dashboard
   - Payment history
   - Invoice generation
   - Pending/Late payment notifications
   - Maintainance cost tracking
   - Gas, Water electricity bill

4. **Communication & Notifications**
   - Automated rent and utility bill reminder
   - General announcements
   - Maintenance requests

## UI Components & Layouts

### Main Navigation Structure
```
├── Dashboard
├── Properties
│   ├── Property List
│   ├── Room Management
│   └── Property Details
├── Tenants
│   ├── Tenant List
│   ├── Tenant Profile
│   └── Onboarding
├── Finances
│   ├── Rent Collection
│   ├── Payment History
│   └── Invoices
├── Communications
│   ├── Notifications
│   └── Messages
└── Settings
    ├── Profile
    └── App Preferences
```

### Key UI Components

#### 1. Dashboard Layout (Detailed)

**Header Section**
- **Left**: App logo and brand name
- **Center**: Global search bar (search tenants, properties, rooms)
- **Right**: 
  - Notification bell with badge count
  - User avatar with dropdown (profile, settings, logout)
  - Quick add button (+) for adding tenant/property

**Main Content Area (Grid Layout)**

**Top Row - Key Metrics Cards (4 columns)**
- **Total Properties Card**
  - Large number display
  - Sub-text: "X vacant rooms"
  - Trend indicator (up/down arrow with percentage)
  - Quick action: "Add Property"

- **Active Tenants Card**
  - Large number with tenant count
  - Sub-text: "X new this month"
  - Occupancy rate percentage
  - Quick action: "Add Tenant"

- **Monthly Revenue Card**
  - Current month earnings
  - Comparison with previous month
  - Progress bar showing collection percentage
  - Quick action: "View Financials"

- **Pending Actions Card**
  - Number of pending tasks
  - Sub-categories: overdue payments, lease renewals, maintenance
  - Urgency indicator (red/yellow/green)
  - Quick action: "View All"

**Second Row - Split Layout (70% - 30%)**

**Left Panel: Recent Activities Feed**
- **Activity Timeline** (scrollable)
  - Payment received notifications
  - New tenant registrations
  - Lease renewals/expirations
  - Property updates
  - Each item with timestamp, action type icon, and brief description
  - Filter options: All, Payments, Tenants, Properties, Today, This Week

**Right Panel: Quick Actions Widget**
- **Priority Actions Section**
  - "Collect Rent" button with pending count
  - "Send Reminders" with overdue count
  - "Generate Reports" 
  - "Add New Tenant"

- **Upcoming Events**
  - Lease expiration dates (next 30 days)
  - Scheduled maintenance
  - Rent due dates
  - Property inspections

**Third Row - Analytics Section (Full Width)**

**Financial Overview Panel**
- **Monthly Revenue Chart** (Bar/Line chart showing last 6 months)
- **Payment Status Breakdown** (Pie chart: Paid, Pending, Overdue)
- **Top Performing Properties** (List with revenue comparison)
- **Collection Rate Trends** (Percentage over time)

**Fourth Row - Management Widgets (3 columns)**

**Properties Overview Widget**
- **Property List** (Compact view)
  - Property name with thumbnail
  - Occupancy status (X/Y rooms occupied)
  - Monthly revenue from property
  - Quick actions: View Details, Add Room
- **Room Status Visualization**
  - Color-coded room grid (Green: Occupied, Red: Vacant, Yellow: Maintenance)
  - Hover tooltips with tenant name and rent amount

**Tenant Management Widget**
- **Recent Tenant Activities**
  - New move-ins this month
  - Upcoming lease renewals
  - Tenants with payment issues
- **Tenant Communication Center**
  - Unread messages count
  - Recent maintenance requests
  - Quick message broadcast option

**Financial Management Widget**
- **Payment Collection Status**
  - This month's collection percentage
  - Overdue payments list (scrollable)
  - Quick invoice generation
- **Expense Tracking**
  - Monthly expenses summary
  - Recent expense entries
  - Add expense quick action

**Bottom Section - System Status & Shortcuts**
- **System Status Bar**
  - Last backup date
  - Data sync status
  - Storage usage indicator
- **Quick Shortcuts**
  - Frequently used features based on user behavior
  - Customizable shortcut buttons
  - Recently viewed properties/tenants

**Sidebar Navigation (Collapsible)**
- **Main Menu Items** with icons and badges
  - Dashboard (current)
  - Properties (with vacant room count)
  - Tenants (with pending actions count)
  - Finances (with overdue payments count)
  - Communications (with unread messages count)
  - Reports
  - Settings

**Responsive Design Considerations**
- **Desktop (1200px+)**: Full 4-column grid layout
- **Tablet (768px-1200px)**: 2-column layout, stacked widgets
- **Mobile (<768px)**: Single column, collapsible sidebar, essential metrics only

**Dashboard Personalization Options**
- **Widget Customization**
  - Drag-and-drop widget reordering
  - Show/hide specific widgets
  - Resize widgets (small, medium, large)
- **Data Filters**
  - Date range selectors
  - Property-specific views
  - Tenant status filters
- **Theme Options**
  - Light/dark mode toggle
  - Color scheme preferences
  - Dashboard density (compact/comfortable/spacious)

#### 2. Property Management Components
- **Property Card**: Display property overview with image, address, total rooms
- **Room Grid**: Visual grid showing room status (occupied/vacant)
- **Room Form**: Add/edit room details with photo upload
- **Property Details Panel**: Comprehensive property information

#### 3. Tenant Management Components
- **Tenant List Table**: Sortable/filterable table with tenant info
- **Tenant Profile Card**: Photo, contact info, lease details
- **Onboarding Wizard**: Multi-step form for new tenant registration
- **Document Upload**: Secure document storage and viewing

#### 4. Financial Components
- **Payment Dashboard**: Overview of rent collection status
- **Invoice Generator**: Customizable invoice creation
- **Payment History Table**: Detailed payment records
- **Financial Reports**: Charts and analytics

#### 5. Communication Components
- **Notification Center**: In-app notification management
- **Message Thread**: Conversation history between owner and tenant
- **Broadcast Message**: Send messages to multiple tenants

## Database Design

### Core Tables

#### 1. Users Table
```sql
users
├── user_id (PK)
├── user_details_id (FK)
├── created_at
├── updated_at
└── is_active
```

#### 2. User Details Table
```sql
user_details
├── user_details_id (PK)
├── email (unique)
├── password_hash
├── first_name
├── last_name
├── phone_number
├── address_id
├── user_type (owner/tenant)
├── profile_image_url
├── created_at
└── updated_at
```

#### 3. User Address Table
```sql
addresses
├── address_id (PK)
├── address_one
├── address_two
├── city
├── District
├── State
├── zipcode
├── country_id (FK)
├── created_at
├── updated_at
└── is_active
```

#### 4. Country Table
```sql
country
├── country_id (PK)
├── country_code
├── country_name
├── continent
├── created_at
├── updated_at
└── is_supported
```

#### 5. Properties Table
```sql
properties
├── property_id (PK)
├── owner_id (FK → users.user_id)
├── property_name
├── address_line1
├── address_line2
├── city
├── state
├── zip_code
├── country
├── property_type
├── total_rooms
├── created_at
└── updated_at
```

#### 6. Rooms Table
```sql
rooms
├── room_id (PK)
├── property_id (FK → properties.property_id)
├── room_number
├── room_type
├── size_sqft
├── rent_amount
├── security_deposit
├── room_description
├── amenities (JSON)
├── is_available
├── created_at
└── updated_at
```

#### 7. Leases Table
```sql
leases
├── lease_id (PK)
├── room_id (FK → rooms.room_id)
├── tenant_id (FK → users.user_id)
├── lease_start_date
├── lease_end_date
├── monthly_rent
├── security_deposit_amount
├── lease_status (active/expired/terminated)
├── lease_terms (TEXT)
├── created_at
└── updated_at
```

#### 8. Leases_docs
```sql
lease_docs
├── lease_doc_id (PK)
├── lease_id (FK - lease.lease_id)
├── lease_doc_url
├── address_doc_type
├── address_doc_number
├── address_doc_url
├── id_proof_type
├── id_proof_number
├── id_proof_url
├── created_at
└── updated_at
```

#### 9. Transaction Table
```sql
payments
├── transaction_id (PK)
├── lease_id (FK → leases.lease_id)
├── payment_date
├── amount_paid
├── payment_method
├── payment_status (pending/completed/failed)
├── due_date
├── payment_type (rent/utility)
├── payment_reference
├── created_at
└── updated_at
```

#### 10. Invoices Table
```sql
invoices
├── invoice_id (PK)
├── lease_id (FK → leases.lease_id)
├── invoice_number
├── invoice_date
├── due_date
├── total_amount
├── invoice_status (draft/sent/paid/overdue)
├── invoice_pdf_url
├── created_at
└── updated_at
```

#### 11. Notifications Table
```sql
notifications_log
├── notification_id (PK)
├── user_id (FK → users.user_id)
├── notification_type
├── title
├── message
├── is_read
├── created_at
└── expires_at
```

#### 12. Currency Table
```sql
currencies
├── currency_id (PK)
├── currency_code
├── country_id
├── exchange_rate
├── is_supported
├── created_at
└── modified_at
```

#### 13. Roles Table
```sql
roles
├── role_id (PK)
├── role_name
├── role_type
├── created_at
└── modified_at
```

#### 13. User Roles Table
```sql
user_roles
├── user_role_id (PK)
├── user_id (FK)
├── role_id (FK)
├── created_at
└── modified_at
```


## Phase 1 - Must-Have Features (MVP)

### For Property Owners
1. **Account Management**
   - User registration and authentication
   - Profile management
   - Password reset functionality

2. **Basic Property Management**
   - Add/edit property information
   - Add rooms with basic details (rent amount, description)
   - Upload room photos (max 5 per room)
   - Mark rooms as available/occupied

3. **Tenant Onboarding**
   - Simple tenant registration form
   - Basic tenant profile (name, contact, emergency contact)
   - Assign tenant to specific room
   - Create basic lease record

4. **Essential Financial Features**
   - Manual rent payment recording
   - Basic payment history view
   - Simple invoice generation (PDF)
   - Payment status tracking (paid/pending/overdue)

5. **Basic Notifications**
   - Email notifications for overdue payments
   - Simple in-app notification center
   - New tenant onboarding notifications

### For Tenants (Limited Access)
1. **Profile Access**
   - View own profile information
   - Update contact details

2. **Payment Information**
   - View rent payment history
   - Download invoices
   - View current payment status

3. **Basic Notifications**
   - Receive rent reminders
   - View important announcements

## Phase 2 - Enhanced Features

### Advanced Property Management
1. **Enhanced Room Management**
   - Room availability calendar
   - Maintenance scheduling
   - Utility tracking per room
   - Room inspection records

2. **Advanced Tenant Features**
   - Tenant document storage (ID, lease agreement, references)
   - Tenant rating/notes system
   - Lease renewal management
   - Move-in/move-out checklists

3. **Financial Enhancements**
   - Automated rent reminders
   - Late fee calculation and application
   - Expense tracking for properties
   - Financial reporting and analytics
   - Integration with payment gateways
   - Recurring payment setup

4. **Communication System**
   - In-app messaging between owner and tenants
   - Maintenance request system
   - Broadcast messaging to all tenants
   - SMS integration for urgent notifications

5. **Analytics & Reporting**
   - Revenue analytics
   - Occupancy rate tracking
   - Tenant turnover analysis
   - Property performance reports
   - Export capabilities for accounting

6. **Advanced Features**
   - Multi-property owner support
   - Tenant screening integration
   - Automatic lease agreement generation
   - Mobile app companion
   - API for third-party integrations

## Technical Considerations

### Security Requirements
- JWT-based authentication
- Role-based access control (RBAC)
- Secure file upload and storage (s3)
- Data encryption for sensitive information ( Phase 2)
- Audit logging for critical actions (Phasse 3)

### Performance Considerations
- Image optimization and CDN integration ( Phase 2)
- Database indexing strategy
- Caching for frequently accessed data
- Pagination for large data sets

### Scalability Planning
- Modular architecture for feature additions
- Database design supporting multiple properties per owner
- Microservices consideration

