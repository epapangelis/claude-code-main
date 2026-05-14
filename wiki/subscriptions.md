# Subscriptions Board

**Summary**: Documents the Subscriptions module in Instafleet — the Customer Success team's workspace for managing active car subscription contracts.

**Sources**: raw/Instafleet/Subscriptions Board - Instafleet/

**Last updated**: 2026-04-29

---

## Overview

The Subscriptions board is owned by the **Customer Success** team. It tracks all active and historical subscription contracts — from delivery through to return or cancellation.

Located in sidebar under: **Customer Success → Subscriptions**

---

## Subscription Lifecycle

Subscriptions move through the following statuses:

```
Created → For Delivery → Active → Expiring → Renewal → For Return → Ended
                                                                    ↓
                                                                Cancelled
```

| Status | Description |
|---|---|
| **Created** | Record created, vehicle not yet delivered |
| **For Delivery** | Vehicle being prepared and scheduled for delivery |
| **Active** | Subscription is live; customer has the vehicle |
| **Expiring** | Contract nearing its end date |
| **Renewal** | Customer in renewal process |
| **For Return** | Vehicle scheduled for return |
| **Ended** | Contract completed normally |
| **Cancelled** | Subscription terminated early |

---

## List View

The default view of the Subscriptions board. Columns include:

| Column | Notes |
|---|---|
| Internal ID | Instafleet internal reference |
| Car ID | Vehicle identifier |
| Type | Subscription type |
| Subscription | Status badge (colour-coded) |
| Created At | Date record was created |
| Updated At | Last modification date |
| Vehicle | Make/model |
| Plate | Vehicle licence plate |
| Owner | Customer name |
| Amount | Monthly contract value (€) |
| Pipeline ID | Linked pipeline reference |
| Promised Delivery Date | Scheduled delivery date |

---

## Subscription Detail Page

Clicking a subscription opens the full detail view. It has a **left sidebar** with key metadata and a **tabbed main area**.

### Left Sidebar Fields

**Subscription info**
- Start Date
- End Contract Date
- Payment Due Date
- Out of SLA (toggle)
- Promised Delivery Date Range
- Contract Condition
- Duration
- Outstanding Charges (add)
- Outstanding Charges Next Amount
- Contract Value
- Marketing Campaign
- Selected Offers
- Coupon Discount

**Vehicle Information**
- Vehicle (make/model/trim)
- Type
- FIP
- Car ID
- Chassis Number
- Contract ID
- New/Used
- Mileage
- Fuel type
- Class
- Fleet/Recurring flag
- Nauclation (?)

---

## Tabs

### Products Tab

Pricing line items for the subscription. Each item shows:

| Column | Description |
|---|---|
| Name | Product type |
| Discount | Discount value |
| VAT | VAT rate |
| Net Price (per unit) | Pre-VAT price |
| Gross Price (per unit) | Price incl. VAT |
| Months | Duration (where applicable) |

**Display To Offer** toggle on each item controls customer-facing visibility.

Standard product line items (same as [[booking#Products]]):
- Sign Up Fee Normal
- Monthly Fee Car/Van
- User's Deposit
- Instated (with months selector)
- Extra Months
- Deposit from Vehicle Sale
- Price/km Cars
- Extra Km
- Free Fuel
- Extra Guarantee

A **"Create Contract"** action is available from this tab.

---

### Bundles Tab

Lists any add-on bundles attached to the subscription. Can be empty. Action: **Add New Bundle**.

---

### Members Tab

Lists all people associated with the subscription.

| Column | Description |
|---|---|
| Active Driver | Boolean flag |
| Internal ID | Instafleet user ID |
| Role | e.g. Contact |
| Full Name | — |
| Email | — |
| Phone Number | — |
| Type | — |
| Updated At | — |
| Edit | Edit action |

Action: **Add New Member**

---

### Delivery/Return Tab

Manages the physical handover and return of the vehicle.

#### Delivery Section
- **Inspection plan** — pre-delivery inspection record
- **Delivery plan**:
  - Driver Information (name, phone)
  - Distance Mode
  - Customer ID
  - Delivery Date
  - Delivery Address
  - Comment ID
  - Driver Location link
  - Loan Car PIN

#### Return Section
- **Inspection plan** — return condition record
- **Return plan** — return date and logistics

#### Tires Section (for both Delivery and Return)
Captures tyre details at handover:

| Field | Description |
|---|---|
| Dimension | Tyre size |
| Position | e.g. Front Left, Front Right, etc. |
| Product | Tyre brand/model |
| VAT | — |
| Gross | Gross price |
| Quantity | — |
| Mileage | Odometer at time of check |
| Weight | — |
| Profile | Tread depth |
| Height | — |
| Image | Photo upload |

Additional checkboxes: Pressure & Warning Penny, Body Tire, Extra Tire, Changing Cities.

---

### Documents Tab

Stores uploaded files associated with the subscription.

| Column | Description |
|---|---|
| Type | Document type |
| ID | Internal document ID |
| File name | Uploaded file name |
| Uploaded | Upload date |

---

### Fees Tab

Tracks any fees charged outside the regular contract.

| Column | Description |
|---|---|
| Status | Fee status |
| Created At | Date fee was raised |
| Type | Fee type |
| Amount | Amount (€) |
| Action | Action buttons |

---

### History Tab

Append-only activity log for the subscription. Sub-tabs:

- **All** — all events
- **Comments** — manual notes left by agents
- **Emails** — email communications
- **SMS** — SMS messages sent
- **Changelog** — system-recorded field changes (e.g. `Promotion.status.away → subscriptionEnded`)

Each entry shows timestamp and the agent who made the change.

---

### Linked Subscriptions Tab

Lists other subscriptions linked to this one (e.g. renewals, replacements).

| Column | Description |
|---|---|
| Subscription ID | — |
| Subscription Type | — |
| Status | — |
| Vehicle | — |
| Plate | — |
| Owner | — |
| Amount | — |
| Pipeline ID | — |
| Create At | — |

---

### Payment & Billing Tab

#### Initial Payment Details
- Payment Method
- Bank of Payment
- Customer's IBAN
- Date of Initial Payment
- Paid Amount

#### Recurring Payment Infos
- Payment Method
- Bank of Payment
- Customer's IBAN
- Payment Due Date
- Paid Amount

#### Billing Details
Individual or company billing entity. Editable via **Add Billing Detail**.

#### Guarantor Agreement
Add guarantor via **Add Guarantor** action.

---

## Filters

The Subscriptions board supports the following filters (see [[navigation]] for full filter reference):

- Subscription Status
- Type
- Labels
- Assignees
- Procurement Stage
- Reservation Type
- Vehicle Availability Status
- Booking Agent
- Bundle Type / Bundle Status
- Delivery Status / Delivery Location
- Out of SLA
- ERFUDD Alerts (toggle)

Filters can be pinned and custom filter sets can be saved.

---

## Related pages

- [[booking]]
- [[navigation]]
- [[design-system]]
