# Instacar UK Launch - Stakeholder Summary
**Date**: 28 April 2026  
**Team**: instacar-uk  
**Project**: uk launch v1  
**Total Issues**: 19

---

## Executive Overview

Instacar UK is in active development with 7 tasks in progress and 12 remaining. The core website build is advancing (VLP, VDP, and Instatrade flows) but is blocked by several upstream decisions on marketing copy, contact channels, and backend scope.

---

## Status Breakdown

### 🟢 In Progress (7 tasks)

**Website Pages Being Built**:
- **UK-4** — Vehicle Listing Page (`/buy`) — **URGENT** ⭐ | Vangelis Papangelis
- **UK-2** — Vehicle Detail Page (`/buy/[id]`) — **URGENT** ⭐ | Vangelis Papangelis
- **UK-6** — Instatrade Plate Lookup (`/instatrade/find-your-vehicle`) — **URGENT** ⭐ | Vangelis Papangelis
- **UK-5** — Instatrade Info Page (`/instatrade`) — **URGENT** ⭐ | Vangelis Papangelis
- **UK-7** — UK Footer Component — **URGENT** ⭐ | Vangelis Papangelis

**Compliance / Content**:
- **UK-10** — FAQ Page (`/faq`) — **URGENT** ⭐ | Vangelis Papangelis
- **UK-15** — Privacy Policy (`/privacy`) — **MEDIUM** | Vangelis Papangelis

---

### 🟡 Todo (2 tasks)

These are not yet started but are next in line:
- **UK-12** — Contact Page (`/contact`) — **URGENT** ⭐ | Vangelis Papangelis
- **UK-9** — About Page (`/about`) — **URGENT** ⭐ | Vangelis Papangelis

---

### 🔴 Backlog (10 tasks — **DECISION / BLOCKER HEAVY**)

#### Blockers Requiring Decisions (Must Resolve First)

**Marketing & Copy**:
- **UK-13** — USPs and Marketing Copy — **URGENT** ⭐ | Dimitris Kalaitzis
  - *Blocker*: No content-dependent pages can finalize without this.

**Contact Channels**:
- **UK-18** — Contact Email Address Setup — **URGENT** ⭐ | Dimitris Togias
  - *Decision needed*: drive@instacar.uk or alternative?
  
- **UK-17** — WhatsApp Setup and Routing — **LOW** | Apostolos Chatzisvvas
  - *Decision needed*: Direct number, shared inbox, or bot routing?
  - *Impact*: Blocks WhatsApp CTAs across site.

- **UK-19** — Aircall Setup and Phone Call Management — **HIGH** | Apostolos Chatzisvvas
  - *Questions*: New UK number? Call routing? Operating hours?

#### Scope & Implementation

- **UK-8** — Backend Scoping (instafleet UK Workspace) — **URGENT** ⭐ | Dimitris Togias
  - *Status*: Scoping discussion only; no implementation until agreed.

- **UK-3** — Homepage Redirect (`/` → `/buy`) — **URGENT** ⭐ | Dimitris Togias
  - *Simple*: Root URL redirect (301) to `/buy`.

- **UK-11** — Terms & Conditions Page (`/terms`) — **URGENT** ⭐ | Apostolos Chatzisvvas
  - *Status*: Backlog; legal content awaited.

#### Compliance & Setup

- **UK-14** — Cookie Consent & Cookiebot Setup — **LOW** | Dimitris Kalaitzis
  - *Needed before launch*: GDPR/PECR compliance.

- **UK-16** — PreLeads Decision — **MEDIUM** | Apostolos Chatzisvvas
  - *Question*: Include PreLeads at Phase 1 launch or post-launch?

---

## Key Metrics

| Status | Count | % |
|--------|-------|---|
| In Progress | 7 | 37% |
| Todo | 2 | 11% |
| Backlog | 10 | 53% |
| **Total** | **19** | **100%** |

| Priority | Count | Status |
|----------|-------|--------|
| 🔴 Urgent | 9 | Mostly in progress; some backlog decisions needed |
| 🟠 High | 1 | Backlog (Aircall setup) |
| 🟡 Medium | 2 | Backlog (PreLeads, Privacy Policy) |
| 🟢 Low | 2 | Backlog (WhatsApp, Cookies) |

---

## Critical Path & Blockers

### 🚧 Blocking Website Progress
1. **UK-13** (Marketing Copy) — Needed for About, Footer, and messaging across pages
2. **UK-8** (Backend Scope) — Needed before Vangelis can finalize integrations
3. **UK-18** (Contact Email) — Needed for Contact page
4. **UK-17** (WhatsApp Routing) — Needed for WhatsApp CTAs

### Timeline
- **In Progress**: 2-3 weeks to complete at current pace
- **Backlog Decisions**: 1-2 weeks to resolve once stakeholders align
- **Post-Decision Build**: 2-3 weeks to implement remaining pages

---

## Recommended Next Actions

### For Product (Dimos)
- [ ] Get marketing copy (UK-13) from Dimitris K. by **EOW**
- [ ] Confirm WhatsApp routing decision (UK-17) by **next week**
- [ ] Schedule backend scope sync with Dimitris T. and tech team (UK-8)

### For Marketing (Dimitris K.)
- [ ] Deliver USPs and copy draft for UK-13
- [ ] Confirm Aircall setup details (UK-19) with ops team

### For Ops (Apostolos)
- [ ] Resolve contact email (UK-18)
- [ ] Confirm WhatsApp destination and Aircall routing (UK-17, UK-19)

### For Legal (External or Internal)
- [ ] Provide Terms (UK-11) and Privacy Policy (UK-15) legal copy

---

## Dependencies Map

```
UK-13 (Marketing Copy) 
  ↓
  UK-9 (About), UK-10 (FAQ), UK-5 (Instatrade), UK-4 (VLP)

UK-8 (Backend Scope)
  ↓
  UK-6 (Plate Lookup), UK-4 (VLP integrations)

UK-18 (Contact Email)
  ↓
  UK-12 (Contact Page)

UK-17 (WhatsApp Routing)
  ↓
  UK-5 (Instatrade), UK-12 (Contact), UK-7 (Footer)
```

---

## Notes

- All website pages are assigned to **Vangelis Papangelis** (primary dev)
- Backlog items are awaiting decision or content from other teams
- No dates set yet; will be determined once decisions are made
- PreLeads (UK-16) is low priority and can be deferred to post-launch if needed
