# AR&M — Accidents, Repairs and Maintenance

**Summary**: Documents the AR&M module in Instafleet — the team's workspace for managing vehicle repair tickets, work orders, and the financial approval flow.

**Sources**: raw/Instafleet/AR&M - instafleet/

**Last updated**: 2026-04-29

---

## Overview

AR&M covers three boards: **Repairs**, **Maintenance**, and **Accidents/Claims**. All three boards share the same structure — the screenshots document Repairs specifically.

Located in sidebar under: **AR&M → Repairs / Maintenance / Accidents/Claims**

---

## Repair Ticket Stages

Tickets move through the following stages:

| Stage | Description |
|---|---|
| **Open Cases** | Ticket created, not yet in progress |
| **In Progress** | Repair actively being worked on |
| **Service Point** | Vehicle at the service point / workshop |
| **Out Date** | Vehicle has left the service point |
| **Billing** | Repair costs being invoiced |
| **Done** | Ticket resolved and closed |
| **Cancelled** | Ticket cancelled |

---

## List View

The AR&M list view shows all repair tickets. Columns include:

| Column | Notes |
|---|---|
| ID | Repair ticket ID (e.g. REP-00117) |
| Request Date | Date the ticket was created |
| Repair Stage | Colour-coded badge (Open Cases, In Progress, Done, etc.) |
| Service Point | Workshop/service centre assigned |
| Reason | e.g. Repair, For Sale - Repair |
| Out Date from Service Point | Date vehicle left the service point |
| Date to Service Point | Date vehicle was sent to service point |

**Top bar filters:** Stage, Service Point, Assignee

---

## Filters

### Quick Filters (top bar)
- Stage
- Service Point
- Assignee

### Custom Filters
A condition builder modal ("Set AR&M Repairs Filters") allows stacking multiple filter conditions:
- Field (e.g. Service Plate, Request Date, Date To Service Point)
- Operator (e.g. equals, contains, before, after)
- Value
- "Add condition" to stack multiple conditions

> **Note:** The custom filter condition builder is planned to be rolled out across all other Instafleet boards in a future update.

---

## Repair Ticket — Detail Page

Each ticket opens a full detail page. A **progress strip** at the top shows the current stage visually.

### Tabs

| Tab | Description |
|---|---|
| **Ticket Details** | Core ticket information and work order |
| **Work Order** | Line items for repair work and service point offers |
| **Financial Details** | Costs, approval flags, invoice details |
| **Comments** | Agent notes and communication log |
| **History** | System-generated audit trail |

---

## Ticket Details Tab

### Ticket Details Section

| Field | Notes |
|---|---|
| Do we need a Temp Car? | Yes/No toggle |
| Temporary Car ID | ID of the loaner vehicle if applicable |
| Kilometres | Odometer reading |
| Service Point | Workshop assigned (dropdown) |
| Expected Out from Service Point | Planned return date |
| Out Date from Service Point | Actual return date |
| Send offer e-mail | Toggle |
| Date of Roadside Assistance | If roadside assistance was involved |
| instaDelivery | Delivery date |
| ZAI | — |
| Taxes | — |

### Work Order Section

Each ticket contains a **Work Order** with a unique ID (e.g. WO22019115).

Work line items are structured as:

| Column | Description |
|---|---|
| Work Type | Type of repair work (e.g. Repair) |
| Details | Detail code or description |
| Side 1 | Part/component reference |
| Side 2 | Additional reference |
| Offer Amount | Cost offered by service point |
| Change Client Amount | Amount charged to the client |

Multiple work line items can be added ("Add line offer"). Each item can also be removed ("Remove This Work Type").

**Service point offers:** Offers can be submitted by service points and compared on pricing. The agent selects the preferred offer before proceeding to financial approval.

---

## Financial Details Tab

### Summary

| Field | Description |
|---|---|
| Total Offer Amount | Sum of all offer amounts from work order |
| Total Charge Client Amount | Total amount charged to the client |

### Additional Info (approval flags)

| Flag | Options | Notes |
|---|---|---|
| Offer Approved | Yes / No | Has the offer been approved internally |
| No cost for instacar | Yes / No | Whether instacar absorbs the cost |
| Email Sent & approved by client for charges | Yes / No | Client sign-off on charges |
| Invite ticket to billing | Yes / No | Triggers billing workflow |

### Invoice Details

| Field | Notes |
|---|---|
| Total Invoice Cost | Final invoiced amount (€) |
| Invoice Date | Date of invoice |

---

## Comments Tab

- Free-text comment area with a **Comment** button to submit
- Existing comments displayed with: agent avatar, name, timestamp, content

---

## History Tab

System-generated, append-only audit trail. Each entry records:
- Which agent made the change
- Which field was updated
- Timestamp

Example entries:
- `system created the issue`
- `[agent] updated the Temporary Car ID`
- `[agent] updated the Service Point`
- `[agent] updated the Expected Out from Service Point`
- `[agent] updated the Offer Item`
- `[agent] updated the Date of Roadside Assistance`
- `[agent] updated the InstaDelivery`
- `[agent] updated the Invoice Date`

---

## Right Sidebar

Always visible on the ticket detail page.

### Ticket Details Panel

| Field | Notes |
|---|---|
| Assignees | Agent(s) responsible |
| Stage | Current stage badge (e.g. In Progress) |
| Request Date | Date ticket was created |
| Purpose ID | Internal reference |
| Subscription ID | Linked subscription |
| Reason | e.g. Repair |

### Car Details Panel

| Field | Notes |
|---|---|
| Vehicle photo | — |
| Vehicle name | Make/model/trim (e.g. HYUNDAI KONA) |
| Year | — |
| Labels | e.g. auto, automatic, black, 2023 |
| Car ID | — |
| Chassis number | — |
| Insurance Company | e.g. INTERAMERICAN |
| Financing Provider | — |
| Leasing Programme | — |
| Leasing Provider | — |

### Files Panel
Upload area for documents related to the ticket.

### Images Panel
Upload area for photos (e.g. damage photos, inspection images).

---

## Related pages

- [[subscriptions]]
- [[booking]]
- [[navigation]]
