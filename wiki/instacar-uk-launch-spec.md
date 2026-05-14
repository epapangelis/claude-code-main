# instacar UK Launch Specification

**Summary**: Phase 1 launch spec for instacar UK, covering two main flows (buy + sell-to-us), branding, tech adaptations, and key action items.
**Context**: [instacar]
**Sources**: instacar-uk-launch-spec.md
**Last updated**: 2026-04-23

---

## Overview

**Status**: Planning / Kickoff (April 2026)
**Project Lead**: Alexandros Chatzisavvas
**Stakeholders**: Chatzisavvas, Togias, Dimos, Antonis
**Domain target**: instacar.uk (check pending with Togias)

**Context**: instacar UK is a separate [[instafleet]] workspace (same pattern as instacar/instaride/kineo), not a new backend service. Same frontend/backend structure with UK-specific adaptations only.

**Branding**: All cars listed as **"Instacar Approved Used Cars"** -- leverages BMW/Mercedes certified used car trust model. (source: instacar-uk-launch-spec.md)

---

## Phase 1 Verticals

Only 2 main flows in Phase 1:

1. **/buy** -- used car marketplace (like current /buy listing)
2. **Sell-to-us** -- InstaTrade-style: evaluate your car, buy a replacement

**Out of scope for Phase 1**: new cars, unified view, PreLeads (TBD), pre-book payments.

---

## Required Pages

### Routing

`/` permanently redirects (301) to `/buy`. There is no homepage in Phase 1. (source: UK-3)

### Core Buy Flow

| Page | URL | Key Features | Priority |
|------|-----|--------------|----------|
| Vehicle Listing | /buy | Used cars only, GBP/miles, filters, admin badges | Must |
| Vehicle Detail | /buy/[id] | 100-pt inspection (photos), HPI badge, docs, grey CarFinance, WhatsApp | Must |

### Sell / Instatrade Vertical

Two-page flow: landing page first, then plate lookup. (source: UK-5, UK-6)

| Page | URL | Key Features | Priority |
|------|-----|--------------|----------|
| Instatrade Info | /instatrade | Explains sell/trade-in offer, drives to plate lookup | Must |
| Plate Lookup + Lead Capture | /instatrade/find-your-vehicle | Enter UK reg plate, call UK Instatrade API, capture personal details, create lead + callback | Must |

### Static Pages

| Page | URL | Content | Priority |
|------|-----|---------|----------|
| About | /about | Instacar Promise, EUR150M, awards, social proof | Must |
| FAQs | /faq | Warranty/returns/delivery/HPI Q&A | Must |
| Terms | /terms | UK Consumer Rights Act compliant | Must |
| Privacy Policy | /privacy | UK GDPR compliant; copy from Legal; linked from cookie banner and footer | Must |
| Contact | /contact | WhatsApp, Aircall, social | Must |

---

## Instacar Promise (10 Guarantees)

Displayed on: homepage hero, About, every listing. Aligns with UK Consumer Rights Act 2015 + HPI standards.

1. **12-month warranty** -- free on major components (vs statutory 6 months)
2. **30-day faulty return** -- full refund (statutory, bold marketing)
3. **14-day change of mind** -- online buys (Consumer Contracts Regulations)
4. **14-day swap** -- equal/higher value car, under 1k miles, GBP 299 fee
5. **100-point inspection** -- full report + photos per item on listing
6. **HPI clear + GBP 500** -- finance/write-off/mileage guarantee
7. **Free delivery** -- 30 miles from Warrington; quoted beyond
8. **Free MOT x3 years** -- partner garage (TBD: service revenue play)
9. **Customer-first** -- fix issues upfront
10. **No hidden fees** -- listed price = final price

---

## Tech and Integrations

| Area | Details | Status |
|------|---------|--------|
| Localisation | GBP, miles | Confirmed |
| Comms | WhatsApp (not Viber), Aircall | Confirmed -- routing decision pending (UK-17) |
| Contact email | drive@instacar.uk or hello@instacar.uk -- decision with Apostolos + Togias (UK-18) | TBD |
| Valuation | UK Instatrade API -- enter UK reg plate, returns vehicle details (UK-6) | Confirmed |
| Data Flow | Instafleet UK workspace <-> UK API <-> DB | Scoping in progress (UK-8) |
| Admin badges | Configurable | Confirmed |
| CarFinance | Greyed out/disabled Phase 1 | Confirmed |
| Cookie consent | Cookiebot (or equivalent) -- UK GDPR + PECR compliance, required before go-live (UK-14) | TODO |
| Marketing copy | USPs + copy for homepage, about, listing, VDP -- unblocks multiple frontend tickets (UK-13) | Urgent/Pending |

---

For current action items and status, see Linear project: **instacar-uk**.

---

## Backlog (Post Phase 1)

- Full "We Buy Any Car" instant valuation
- Pre-book payments
- Broader marketplace features
- Autotrader auto-leads (TBD)
- PreLeads (TBD)
- Transparency docs per vehicle

---

## instafleet UK — Phase 1 Scope (CTO call, 2026-04-23)

(source: cto-call-instafleet-uk-brief.md)

### instafleet Pages Needed (Sales team only)

- Availability screen — check car status
- Bookings list + detail — view/manage bookings
- Booking creation modal — create new bookings
- Lead capture modal for Instatrade — reg plate lookup → valuation → personal details → create lead/booking

CS subscription tabs, ARM, and subscription detail screens are postponed to Phase 2 (when app launches).

### Database Requirements

| Area | Detail |
|------|--------|
| Localisation | GBP, miles, UK phone format |
| Instatrade | Lead record type (plate lookup → valuation → contact details → create lead/booking) |
| HPI | Vehicle history badge/report data |
| Delivery | Radius config (Warrington-based; quoted beyond 30 miles) |

### Open Tech Decisions

1. **Parallel build vs. schema-first** — Build instafleet UK in parallel with frontend, or finalize DB shape first?
2. **Single vs. separate DB instance** — Same database with workspace filtering, or separate UK instance?
3. **Kanban stages** — To be defined with Chatzisavvas (not blocking initial DB setup)

### Phase 1 Exclusions

- No subscriptions (Phase 2, with app launch)
- No CS team interface
- No ARM

---

## Related pages
- [[instafleet]]
- [[instacar]]
- [[customer-facing-platform]]
