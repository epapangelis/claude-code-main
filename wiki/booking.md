# Booking Board

**Summary**: Documents the Bookings module in Instafleet — the sales pipeline used to manage leads from first contact through to contract signing.

**Sources**: raw/Instafleet/Booking Board - Instafleet/

**Last updated**: 2026-04-29

---

## Overview

The Booking Board is the Sales team's primary workspace. It tracks every lead from initial contact through to a signed contract. It supports two view modes: **Kanban** and **List**.

Located in sidebar under: **Sales → Bookings**

---

## Pipeline Stages

The booking pipeline has 15 sequential stages:

| # | Stage | Notes |
|---|---|---|
| 1 | **Prelead** | Initial lead, not yet contacted |
| 2 | **Hot Prelead** | High-priority lead |
| 3 | **Lead In** | Lead has been engaged |
| 4 | **No Answer** | Contact attempted, no response |
| 5 | **2nd Call Attempt** | Follow-up call made |
| 6 | **Tel Contact No1** | First successful phone contact |
| 7 | **Follow Up** | Ongoing follow-up |
| 8 | **Docs Uploaded** | Customer has uploaded documents |
| 9 | **Docs Received** | Documents received and verified |
| 10 | **Counter Offer** | Negotiation in progress |
| 11 | **Rejected** | Lead rejected |
| 12 | **Approved** | Booking approved |
| 13 | **instapayment** | Payment step initiated |
| 14 | **Customer Paid** | Payment confirmed |
| 15 | **Buy the Car** | Final stage — contract signed |

---

## Views

### Kanban View
Cards are grouped by pipeline stage. Each card shows:
- Customer name
- Vehicle (make/model)
- Contract type badge (e.g. Fleet, Instacar)
- Contract period badge (e.g. 24 Month, 36 Month, 48 Month)
- Pipeline stage
- Contract value (€)

### List View
A tabular view of all bookings. Columns include:

- Stage (colour-coded badge)
- Customer Name
- Created ID
- Origin
- Contract Type
- Contract Period
- Labels
- Customer Type
- Holding Company
- Email
- User ID
- Phone Number

---

## Adding a New Booking

Triggered via the **Add Booking** button. Opens a multi-section modal:

### User Details
| Field | Required |
|---|---|
| First Name | Yes |
| Last Name | Yes |
| Email | Yes |
| Phone Number | Yes |
| Language | Yes |
| Region | Yes |
| Account Type | — |

### Booking Details
| Field | Notes |
|---|---|
| Origin | Dropdown |
| Company | — |
| Referral ID | — |
| Labels | Multi-select |
| Campaign | — |
| Coupon | — |
| Apply Marketing Campaign | Checkbox |

### Consent
- Consent TOS
- Consent Newsletter
- Email Offer
- Consent Contract

### Vehicle Details
| Field | Notes |
|---|---|
| Vehicle | Required |
| Contract Type | Required |
| Contract Period | Required |

### Products
Detailed pricing configuration. See [[#Products]] section below.

---

## Booking Ticket (Detail Page)

Each booking opens a full detail page with tabs across the top:

| Tab | Description |
|---|---|
| **Booking Details** | Core contract fields, marketing discounts, linked offers |
| **Products** | Pricing line items |
| **Payment & Billing** | Payment method, billing details, guarantor |
| **Other Offers Requested** | Alternative offers presented |
| **Cross Offer** | Cross-sell offers |
| **Documents** | Uploaded files |
| **Counter Offer** | Negotiation record |
| **instapayment** | Payment processing details |
| **Components** | — |
| **Customer Paid** | Payment confirmation |
| **Buy the Car** | Final contract step |

### Booking Details Tab

**Contract Details**
- Origin
- Contract Type
- Duration
- Instalment Months
- Initial Payment
- Initial Payment + tax
- Promised Delivery Date
- Contract Value

**Marketing Discounts**
- Marketing Campaign ID
- Coupon

**Linked Offers**
Table of related offers: ID, Contract Type, Vehicle, Initial Payment. Editable via "Add Linked Offer".

### Right Sidebar — Ticket Details
Always visible on the booking ticket:

| Field | Notes |
|---|---|
| Assignees | Team member assigned to ticket |
| Status | Current booking status |
| Order Name | — |
| Customer Types | — |
| Label | Tag/category |
| Due Date | — |
| Pipeline ID | Internal pipeline reference |
| Vehicle ID | Linked vehicle |
| Subscription Type | — |

**Vehicle Details panel** (below ticket details):
- Vehicle photo
- Vehicle name (e.g. MG MG3 HYBRID+ EXCITE)
- Labels (e.g. Fleet, Customer)
- Vehicle ID
- "Change Vehicle" action

**User Information panel**:
- Full name (linked)
- Address
- Contact email
- Phone
- TIN (tax ID)
- Language

---

## Products

Products are the pricing line items on a booking or subscription. Each item has:

| Column | Description |
|---|---|
| Name | Product type |
| Discount | Discount % or amount |
| VAT (%) | VAT rate |
| Quantity | Number of units |
| Months | Duration in months |
| Net Price | Pre-VAT price |
| Gross Price | Price incl. VAT |

**Standard product line items:**

| Product | Notes |
|---|---|
| Sign Up Fee Normal | One-time setup fee |
| Monthly Fee Car/Van | Core subscription monthly charge |
| Car Fee | — |
| User's Deposit | Refundable deposit |
| Instated | Fee with associated months duration |
| Extra Months | Additional contract months |
| Deposit from Vehicle Sale | Deposit offset from vehicle trade-in |
| Price/km Cars | Per-km overage rate |
| Extra Km | Additional km allowance |
| Extra | Miscellaneous extra |
| Free Fuel | Fuel inclusion |
| Extra Guarantee | Additional guarantee product |

Each product has a **Display To Offer** toggle that controls whether it is shown in the customer-facing offer.

---

## Payment & Billing Tab

### Initial Payment Details
- Payment Method
- Bank of Payment
- Customer's IBAN
- Date of Initial Payment
- Paid Amount

### Recurring Payment Infos
- Payment Method
- Bank of Payment
- Customer's IBAN
- Payment Due Date
- Paid Amount

### Billing Details
Free-text / structured billing info (individual or company).

### Guarantor Agreement
Option to add a guarantor.

### History
Activity log with sub-tabs: All, Comments, Emails, SMS, Changelog.

---

## Filters

Available filters on the Booking Board (see also [[navigation]]):
- Stage
- Contract Type
- Contract Period
- Customer Types
- Assignees
- Labels

---

## Related pages

- [[subscriptions]]
- [[navigation]]
- [[design-system]]
