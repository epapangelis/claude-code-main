# Chris Noulis: instafleet Projects for Prioritization

**Date**: 2026-04-20  
**From**: Chris Noulis  
**Channel**: Slack  
**Request**: Book 30-minute meeting to walk through 4 projects for upcoming sprint prioritization

---

## 4 Projects Flagged

Chris flagged these 4 projects as high priority due to direct impact on productivity and business performance:

### 1. Bundle sales with monthly fee
- **Goal**: Lift MRR on the existing customer base
- **Context**: Currently a BGT shortfall
- **Status**: Needs prioritization

### 2. Procurement book
- **Goal**: Track budget deltas on purchase decisions
- **Key requirement**: Separate "committed" vs "non-committed" at order stage
- **Key requirement**: Reintroduce "customs" stage before payment in the flow
- **Detailed description**: See section below

### 3. Dealer system access
- **Goal**: Improve booking dashboard, subscription view, and ticketing
- **Benefit**: Enable dealers to manage leads and increase productivity
- **Detailed description**: See section below

### 4. instacar+ pilot on SV cars
- **Goal**: Differentiate proposition and test operations in a controlled setup
- **Scope**: ~500 customers, limited functionality with manual support
- **Technical**: Open subscription, include in instadriver app

---

## Detailed: Procurement Book

### Overview
Build a "procurement book" — a set of procurement reports that track budget deltas on purchase decisions, pulling directly from instafleet instead of relying on Excel files maintained by the procurement team.

### Business Context
Currently, vehicles tied to WDs (won deals) convert into purchase commitments late in the sales cycle without early visibility. This creates recurring friction between Sales, Finance, and Procurement, leading to forced, last-minute alignment decisions that are often suboptimal, with negative implications on both UTR and MRR.

### Requirement 1: "Commitment" vs "Flexible" classification

**What**: Add a dropdown field when opening an order (Fleet → Vehicles → Order)

**Options**:
- "Commitment": Vehicles we are obliged to purchase regardless of WD status
- "Flexible": Vehicles we will only purchase if a WD materializes

**Why**: Currently all orders are grouped together, creating lack of visibility on which orders will definitely impact the budget vs which are conditional.

**Business impact**: If "commitment" orders are clearly identified from the outset, they can be tracked systematically against monthly BGT parameters (orders, payments, sales), allowing for proactive and aligned decision-making.

### Requirement 2: New "Customs" stage in delivery flow

**What**: Add a dedicated "customs" stage before "payment process" in the vehicle delivery flow

**Why**: Vehicles arrive in Greece and await clearance. Currently, Procurement artificially uses "payment process" stage to reflect this, shifting dates forward when vehicles are not ready for payment, distorting visibility.

**Correct flow**:
1. Vehicles move into "customs" stage when arrived in Greece
2. Remain in customs until genuinely ready to proceed to payment
3. Transition to payment when WD secured OR for "commitment" orders
4. "Flexible" orders without WDs may be cancelled and never enter payment

**Auto ERFUDD logic**:
- Each vehicle in "customs" stage should have +30 calendar days applied to ERFUDD, recalculated daily
- This reflects realistic lead time from customs to delivery (assuming immediate progression to payment)
- Once vehicle transitions to "payment process", existing payment-stage ERFUDD logic takes over

**Note**: A similar stage may have existed and been removed; reintroduction is important for restoring clarity and accuracy.

---

## Detailed: Dealer System Access

### Overview
Improve the dealer dashboard to enable partners to manage leads and increase productivity. Dealers should have visibility into inhouse data similar to what instafleet shows internally.

### Vehicle Inventory View (Reservation status = Free)

**Columns to display** (data already available):
- Status (Available / On Hold / Arm etc)
- Go to Website link for direct site access
- Website Availability (Αναμένεται / 2-day delivery)
- Vehicle Category Class
- Price MM – 12M – 24M – 36M
- ERFUDD view (as inhouse instafleet shows)

**Filters** at top of dashboard (view as inhouse instafleet)

**Car Campaign** visibility in both inhouse and dealer views

### Bookings Dashboard

**View**:
- View as inhouse instafleet
- View only own deals (filtered by user)

**Booking creation**:
- Binding between user and referral ID / Company
- Auto-populate referral ID on creation (not manual selection)
- Template with partner details in offer PDF email
- Include THL and Name in offer
- Send offer with link to upload supporting documentation
- If offer is edited: route to approval path → credit check (if approved)
- Pre-selected km packages for "Extra klm"
- View History table

### Subscription Dashboard

**View**:
- View as inhouse instafleet
- View only own deals, no management/edit capability

### Generic Ticketing

**Capability**:
- Create tickets
- Access only own tickets

---

## Next Steps

Chris is requesting:
1. Calendar a 30-minute meeting before approaching Antonis for prioritization
2. Provide view on feasibility and estimated timeline (especially for Procurement book)
