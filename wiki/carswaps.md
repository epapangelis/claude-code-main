# Car Swaps

**Summary**: Feature enabling CS agents to manage vehicle swaps from within instafleet — replacing manual Pipedrive notes with structured, first-class swap data, linked subscriptions, and product carry-over logic.
**Context**: [instacar]
**Sources**: car-swap-discussion.md, booking_creation_modal_swap_section.html, booking_detail_sidebar_and_warnings.html, subscription_list_swap_indicators.html, subscription_detail_swap_trigger.html, car_swap_modal.html
**Last updated**: 2026-04-22

---

## What this feature does

A CS agent can initiate a car swap from within a subscription's detail view. The swap creates a new linked booking, carries forward relevant products (with proration where applicable), and links the old and new subscriptions bidirectionally so the full chain is navigable.

Part of the [[kill-pipedrive]] initiative — structured swap data replaces freeform Pipedrive notes.

---

## Swap entitlement rules

| Contract type | Swaps allowed |
|---|---|
| Month-to-Month | Unlimited |
| 12-month | 1 |
| 24-month | 2 |
| 36-month | 2 |

---

## Booking label enum

`New` | `Car Swap Same Contract` | `Renewal No Swap` | `Renewal With Swap` | `Temp` | `Predel`

---

## The trigger button

Lives in the **top-right of the subscription detail header bar**, to the left of the kebab menu.

| Subscription state | Button state |
|---|---|
| Active + swaps remaining | Enabled — "Initiate Car Swap" (blue) |
| Active + swap limit reached | Disabled (grey) + "N/N swaps used" pill |
| Ended / inactive | Hidden entirely |

A **swap eligibility indicator** also lives inside the General section of the subscription detail — filled pips = used swaps, empty pips = remaining (e.g. ● ○ = 1 of 2 used).

**Mockup**: `raw/instacar/subscription_detail_swap_trigger.html`

---

## The modal

Near-full-screen overlay, split into three zones.

### Header bar
- Title: "Car Swap" + subscription internal ID
- Swap sequence badge (e.g. "Swap 2 of 2")
- Swap reason dropdown: Upgrade / Customer request / Vehicle issue / Downgrade / Family change / Vehicle unavailable / Other
- Close (X) button

### Left panel — Current subscription (read-only)
Reference view the agent uses while configuring the swap.

- Vehicle card: make/model, plate, monthly fee, contract type, remaining months, swap entitlement pips
- Products (current values): Sign Up Fee Normal, Monthly Fee Car/Van, User's Deposit, Instastart (with month count), Extra Months
- Bundles (current, read-only)

### Right panel — New subscription (agent configures)

Three numbered steps:

**Step 1 — Link new booking**
Agent searches by booking ID, plate, or vehicle. Only bookings labelled Car Swap Same Contract, Renewal No Swap, or Renewal With Swap appear. Confirm button is disabled until a booking is linked.

**Step 2 — Product carry-over**
Each product has a transfer rule and status icon:

| Product | Rule | Agent action |
|---|---|---|
| Sign Up Fee Normal | Not transferred | None (locked off) |
| Monthly Fee Car/Van | Auto — from linked booking | Read-only (new price auto-filled) |
| User's Deposit | Agent decides | Editable field + checkbox |
| Instastart | Auto-prorated: `deposit × (remaining_months / total_months)` | Read-only (calculated, shown as formula) |
| Extra Months | TBD — open question | Locked pending rule definition |

**Step 3 — Pricing comparison**
Old monthly vs new monthly side-by-side with delta badge (▲ upsale / ▼ downsale). A contextual warning appears for significant upsale (>30%) or downsale.

### Footer
Cancel + Confirm Car Swap. Confirm is disabled until Step 1 is complete.

**Mockup**: `raw/instacar/car_swap_modal.html`

---

## Warning states (contextual)

Appear as banners in the booking detail sidebar and inside the modal:

| Warning | Trigger |
|---|---|
| Swap limit exceeded | Customer has used all allowed swaps for their contract type |
| Significant upsale | New monthly fee is >30% higher than current |
| Significant downsale | New monthly fee is >30% lower than current |
| Pending swap exists | Another swap booking already exists for this subscription |

---

## Three hard problems

### 1. Multi-booking race condition
Multiple competing swap bookings can exist simultaneously. The first to reach "For Delivery" status wins; all others are auto-cancelled and a new linked subscription is created.

**Risk**: Race condition if two bookings reach "For Delivery" near-simultaneously.
**Recommendation**: Atomic state transition with a lock or optimistic concurrency check.

### 2. Deposit (Instastart) proration
```
remaining_deposit = deposit × (remaining_months / total_months)
```
Becomes the new subscription's Instastart requirement.

**Edge cases**: new car has a different monthly fee; contract duration changes; mid-cycle (partial month) swaps.
**Recommendation**: Build as an isolated calculation service. Write 8--10 concrete scenarios with exact numbers for Finance validation before engineering begins.

### 3. Bidirectional subscription linking
The full chain must be navigable in both directions — CS agents need to see where a subscription came from and where it leads.

**Recommendation**: Model as a doubly linked list at the data layer (`previous_subscription_id`, `next_subscription_id`) with a chain view in the UI.

---

## Subscription list changes

Swap-type subscriptions show additional indicators in the subscription list:

- **Type badge**: Swap #1, Renewal + Swap, Temp, Predel (colour-coded)
- **Parent link**: subscription ID of the origin sub shown below the new sub's ID
- **Delta indicator**: ▲ (upsale) or ▼ (downsale) in the Contract Value column

**Mockup**: `raw/instacar/subscription_list_swap_indicators.html`

---

## Open questions

- **Extra Months**: Does it carry over, get voided, or get recalculated on the new sub?
- **Bundles**: Do active bundles (roadside assistance, GPS) transfer automatically or does the agent decide?
- **Sign Up Fee**: Is there ever a case where it is recharged on a swap?
- **Display To Offer toggle**: Do carry-over products inherit the toggle state from the origin subscription?
- **Who can initiate**: CS only, or Sales as well?
- **Instastart month count**: Does the month count reset or continue on the new subscription?

---

## Linear project

`linear.app/instacar/project/car-swaps-instafleet-process-15d6a362f76b`

Status: empty shell as of April 2026 — no issues or milestones yet. Next step is Finance validation of deposit calculation scenarios, then populate with issues.

---

## Related pages
- [[kill-pipedrive]]
- [[instafleet-subscriptions]]
- [[subscriptions-data-model]]
- [[instafleet]]
