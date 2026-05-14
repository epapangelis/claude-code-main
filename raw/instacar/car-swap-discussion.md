# Car Swap & Subscription Linking — Discussion Summary

**Date:** April 15, 2026  
**Project:** Instafleet — Kill Pipedrive Initiative  
**Feature:** Car Swap & Subscription Linking (PRD-SWAP-001 v1.0)

---

## Context

The discussion was part of the broader "Kill Pipedrive" initiative — replacing unstructured Pipedrive notes with structured, first-class data inside Instafleet. The Car Swap feature is a core workstream: enabling CS agents to manage vehicle swaps from within Instafleet rather than tracking them manually.

---

## What Was Produced

### PRD (PRD-SWAP-001 v1.0)

A full product requirements document covering:

- **Swap entitlement rules by contract period**
  - Month-to-Month: unlimited swaps
  - 12-month: 1 swap
  - 24-month: 2 swaps
  - 36-month: 2 swaps

- **Booking Label enum**
  `New` | `Car Swap Same Contract` | `Renewal No Swap` | `Renewal With Swap` | `Temp` | `Predel`

- **Bidirectional subscription linking** — agents can navigate the full subscription chain
- **Pricing delta indicators** — upsale / downsale badges on bookings and subscriptions
- **Deposit / Instastart carry-forward logic**
- **Data model changes** for Booking and Subscription
- **API endpoint specifications**
- **Scenario matrix and edge cases**
- **Success metrics**
- **Four-phase implementation plan**

### UI Mockups (4 screens)

All mockups matched the existing Instafleet design system:

1. **Booking Creation Modal** — new Subscription Linking section
2. **Booking Detail sidebar** — swap card with linked subscription
3. **Subscription Detail** — swap panel with entitlement display
4. **Subscription List** — swap type badges and delta indicators

---

## Three Hard Problems Identified

### 1. Multi-Booking Race Pattern

When a swap booking is created from within the subscription screen:
- Multiple competing bookings can exist simultaneously for the same customer
- The **first booking to reach "For Delivery" status** wins
- All other competing bookings are auto-cancelled
- A new linked subscription is created automatically

**Risk:** Race conditions if two bookings reach "For Delivery" near-simultaneously.  
**Recommendation:** Atomic state transition with a lock or optimistic concurrency check.

---

### 2. Deposit (Instastart) Proration Math

Remaining deposit carries forward to the new subscription:

```
remaining_deposit = deposit × (remaining_months / total_months)
```

This becomes the new subscription's Instastart requirement.

**Edge cases:**
- New car has a different monthly fee
- Contract duration changes on the new subscription
- Partial months (mid-cycle swaps)

**Recommendation:** Build deposit proration as an isolated calculation service. Write 8–10 concrete scenarios with exact numbers for **Finance validation before engineering begins**.

---

### 3. Bidirectional Subscription Linking

The full subscription chain must be navigable in both directions — CS agents need to see where a subscription came from and where it leads.

**Recommendation:** Model as a doubly linked list at the data layer (`previous_subscription_id`, `next_subscription_id`) with a chain view in the UI.

---

## Recommended Engineering Decomposition

| Workstream | Description |
|---|---|
| Multi-booking race pattern | Atomic state transitions, concurrency handling |
| Deposit proration engine | Isolated calculation service, Finance-validated |
| Linking & UI layer | Bidirectional chain, swap badges, delta indicators |

---

## Competitive Reference

Loopit and JRNY (comparable subscription fleet platforms) handle vehicle swaps as a first-class operation with structured state machines — not freeform notes. The Instafleet approach aligns with this pattern.

---

## Linear Project

**URL:** `linear.app/instacar/project/car-swaps-instafleet-process-15d6a362f76b`  
**Status at time of discussion:** Empty shell — no issues, milestones, or documents yet.

**Next step:** Populate with issues and milestones once Finance validates deposit calculation scenarios.

---

## Open Actions

- [ ] Write 8–10 deposit calculation scenarios (exact numbers) and share with Finance for validation
- [ ] Populate the Linear project with issues and milestones
- [ ] Revisit Figma file (`DzJ17Kk2eyyTBGndp4qrAx`, node `19220:136048`) for redesigned subscription screens — timed out during this session
- [ ] Confirm whether PRD needs updating based on the additional complexity scoped in this discussion
