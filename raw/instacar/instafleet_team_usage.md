# Instafleet — Team Usage Overview

This document describes how each internal team currently uses Instafleet.
It serves as context for product decisions, PRDs, and the Pipedrive/Trello migration.

---

## 1. Sales Team

The Sales team uses Instafleet primarily for vehicle availability and booking management.

### Screens used:
- **Availability screen** — check which cars are available and their current statuses
- **Bookings list** — view all bookings, filter by status or other criteria
- **Booking detail screen** — view full details of a specific booking
- **Booking modal** — create new bookings

### Current dependency on Pipedrive:
- The Bookings list and Booking detail screens are **used in parallel with Pipedrive deals**
- Sales reps switch between Instafleet and Pipedrive to get all the information they need for a booking
- **This is the core gap the Kill Pipedrive initiative must solve** — all deal/booking data must be consolidated inside Instafleet so Sales can work from a single tool

---

## 2. CS (Customer Success) Team

The CS team uses Instafleet to manage active subscriptions and customer communication.

### Primary screen: Subscription (list + detail)

The subscription detail screen contains multiple tabs:

- **Delivery & Return** — delivery and return details and dates
- **Communication** — direct communication with the customer
- **Status** — current subscription status
- **Drivers** — driver information linked to the subscription
- **Documents** — subscription-related documents
- **Changelog / History** — full history of changes to the subscription

---

## 3. ARM Team (Accidents, Repairs & Maintenance)

The ARM team uses Instafleet to manage vehicle incident and maintenance tickets.

### Screens used:
- **ARM ticket detail** — view full details of a repair, maintenance, or accident/claim ticket

---

## Summary: Teams vs. Tools

| Team | Instafleet | Pipedrive | Trello |
|---|---|---|---|
| Sales | ✅ Availability, Bookings | ✅ Deal details (parallel use) | — |
| CS | ✅ Subscriptions | — | — |
| ARM | ✅ Tickets | — | — |

> **Note:** The Kill Pipedrive project targets the Sales team's dependency on Pipedrive for booking/deal details. Once complete, Sales should operate entirely within Instafleet.
> The Kill Trello project scope to be defined — current Trello usage per team TBD.
