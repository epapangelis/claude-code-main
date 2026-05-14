# Instafleet Navigation

**Summary**: Documents the global navigation structure of Instafleet, including the sidebar, global search, and filter system.

**Sources**: raw/Instafleet/Instafleet Navigation & General Infos/

**Last updated**: 2026-04-29

---

## Sidebar

The sidebar is the primary navigation structure. It is collapsible (via the `<<` icon top right) and organized into the following sections:

### My Hub
- **My Tasks** — personal task list for the logged-in agent

### Favorites
Collapsible section for pinned items (user-defined).

### Workspace

| Section | Sub-pages |
|---|---|
| **Overview** | Power BI, Daily Bookings, Generic Tickets |
| **Sales** | Bookings, Availability Table, Reservations, Campaigns, B2B, Instatrade |
| **Fleet** | Vehicles, Purchase Orders |
| **Sell Vehicles** | Availability, Vehicles, Leasing Buyouts, Requests, Defleet, Sell Vehicles B2B |
| **Customer Success** | Dashboard, Subscriptions, Green Card, Traffic Offenses, Contracts |
| **AR&M** | Dashboard, Repairs, Maintenance, Accidents/Claims |
| **Logistics** | Table, Drivers |
| **Billing** | Billing Table |
| **Services** | Inbox, Insurances, Roadside Assistance, Service Points |
| **Products** | Products Table |
| **Catalog** | Cars, Ebikes, Competition |
| **Marketplace** | Tires, Car Wash, Orders |
| **CRM** | Users, Payments, Private Vehicles |
| **Drivers** | Delivery, Returns, Inspections |
| **Unified View** | Mailboxes, Templates |
| **Credit Check** | Reports, Credit Check Table |
| **Reports** | Instapayment Reports, AVIS Report, ARNM Reports, Export Data |
| **Utilities** | Tools |
| **Visuals** | Videos |

### Admin
- **Admin Area**: Agents, Teams, Configuration, Permissions, Partners, Email Boxes

---

## Global Search

Accessible from the top bar. Supports searching across all major entity types:

| Category | Notes |
|---|---|
| Users | Returns name, email, phone |
| Bookings | — |
| Vehicles | — |
| Vehicle Sales | — |
| Leasing Buyouts | — |
| Requests | — |
| Subscriptions | — |
| Orders | — |
| Service Points | — |
| Roadside Assistance | — |
| Insurances | — |
| Catalog (Cars) | — |

Results are grouped by category with counts shown in the left panel (e.g. "Users 10", "Bookings 10").

---

## Filters

A filter panel available on list views (e.g. Subscriptions, Bookings). Filters are accessible via the funnel icon.

### Available filter categories

- Subscription Status
- Type
- Bundle Type
- Bundle Status
- Delivery Status
- Delivery Location
- Labels
- Assignees
- Procurement Stage
- Reservation Type
- Vehicle Availability Status
- Booking Agent
- Out of SLA

### Subscription Status values

| Status | Description |
|---|---|
| Created | Subscription record created, not yet delivered |
| For Delivery | Vehicle being prepared for delivery |
| Active | Subscription is live and running |
| Expiring | Contract approaching end date |
| Renewal | In renewal process |
| For Return | Vehicle due for return |
| Ended | Contract completed |
| Cancelled | Subscription cancelled |

### Filter behaviours
- Filters can be **pinned** (blue pin icon) to persist across sessions.
- **Custom Filters** option available for saving filter combinations.
- **Reset Filters** button clears all active filters.
- **ERFUDD Alerts** toggle available on the Subscriptions board.

---

## Related pages

- [[booking]]
- [[subscriptions]]
- [[design-system]]
