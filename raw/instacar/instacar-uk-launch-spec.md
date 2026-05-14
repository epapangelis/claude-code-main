
# Instacar UK Launch Specification

**Version:** 1.0  
**Date:** April 15, 2026  
**Project Lead:** Alexandros Chatzisavvas  
**Stakeholders:** Chatzisavvas, Togias, [Your Name], Antonis  
**Status:** Planning / Kickoff  

## Overview

**Verticals (Phase 1):** Only **2 main flows**  
1. **/buy** — Used car marketplace (like current /buy listing)  
2. **Sell-to-us** — InstaTrade-style: evaluate your car → buy replacement  

**Branding:** All cars as **"Instacar Approved Used Cars"** (leverages BMW/Mercedes-style trust)[web:22][web:30]  

**Tech Base:** Same backend/frontend structure, UK adaptations only (GBP, miles, WhatsApp).  

**Next Immediate Actions:**  
- Create Linear project (manual, add team)  
- Domain check w/ Togias (`instacar.uk`)  
- Define Instafleet kanban stages for UK leads  

## Required Pages

### Core Flows (/buy vertical)

| Page | URL | Key Features | Priority |
|-----|-----|--------------|----------|
| Homepage | `instacar.uk/buy` or `/` | Hero w/ Promise, featured cars, trust badges, browse CTA | Must |
| Vehicle Listing | `/buy` | Used cars only, GBP/miles, filters, admin badges | Must |
| Vehicle Detail | `/buy/[id]` | 100-pt inspection (photos), HPI badge, docs, grey CarFinance, WhatsApp | Must |
| Find My Car | `/find` or modal | Lead form | Must |

### Sell Vertical

| Page | URL | Key Features | Priority |
|-----|-----|--------------|----------|
| Sell/Evaluation | `/sell` or `/instatrade` | Valuation (API), exchange field, → buy flow | Must |

### Static Pages

| Page | URL | Content | Priority |
|-----|-----|---------|----------|
| About | `/about` | Instacar Promise, €150M, awards, social proof | Must |
| FAQs | `/faq` | Warranty/returns/delivery/HPI Q&A | Must |
| Terms | `/terms` | UK Consumer Rights Act compliant | Must |
| Contact | `/contact` | WhatsApp, Aircall, social | Must |

## Instacar Promise (10 Guarantees)

Display prominently: Homepage hero, About, every listing.  
*Legal note: Aligns w/ UK Consumer Rights Act 2015 + HPI standards, positioned as superior.*[web:17][web:19][web:25]

1. **12-month warranty** — Free on major components (vs statutory 6mo)
2. **30-day faulty return** — Full refund (statutory, bold marketing)
3. **14-day change mind** — Online buys (Consumer Contracts Regs)
4. **14-day swap** — Equal/higher value car, <1k miles, £299 fee
5. **100-point inspection** — Full report + photos per item on listing
6. **HPI clear + £500** — Finance/write-off/mileage guarantee
7. **Free delivery** — 30mi Warrington; quoted beyond
8. **Free MOT x3 years** — Partner garage *(TBD: service revenue play)*
9. **Customer-first** — Fix issues upfront
10. **No hidden fees** — Listed price = final price

## Tech & Integrations

| Area | Details | Status |
|------|---------|--------|
| Localization | GBP (£), miles | Confirmed |
| Comms | WhatsApp (not Viber), Aircall calls | Confirmed |
| Valuation | InstaTrade API + exchange field | Confirmed |
| Data Flow | Instafleet ↔ UK API ↔ DB | Map needed |
| Admin | Badges configurable | Confirmed |
| CarFinance | Greyed out/disabled | Confirmed |

**Out of scope now:** New cars, unified view, PreLeads (TBD), pre-book payments.

## Business & Ops (TBD)

- **Instafleet kanban** for UK leads/bookings  
- **Autotrader** auto-leads?  
- **PreLeads** yes/no?  
- **Transparency docs** per vehicle  

## Action Items

| Action | Owner | Status |
|--------|-------|--------|
| Linear project creation | [Your Name] | TODO |
| Domain setup check | Togias | TODO |
| Instafleet kanban definition | Chatzisavvas | Next mtg |
| MOT promise (#8) review | Antonis/Team | Discuss |
| Legal/terms review | Legal | Early |
| API mappings | Backend | Post-Linear |
| Wireframes (2 verticals) | Product/Frontend | Post-kickoff |

## Backlog

- Full "We Buy Any Car" instant valuation  
- Pre-book payments  
- Broader marketplace features  

---
*Generated from meeting notes. Update as decisions finalize.*
