# Bundle Monthly Charging Spec (Existing Customers)

**Summary**: Draft spec for Component 2 of the bundle sales initiative — converting existing customers' 12-month bundle into a silent monthly extension, including trigger detection, payment mechanism, customer notification, opt-out, and termination enforcement.
**Context**: [instacar]
**Sources**: raw/instacar/Premium Changes in Pricing.md
**Last updated**: 2026-09-09

***

## Status

**Updated 2026-09-09**: monthly bundle charging itself is already live in production (source: Evangelos) — it charges alongside the car's monthly rent. The remaining, unvalidated gap is narrower than originally scoped: **customer notification, opt-out, and apalagi-based termination enforcement** (Sections 4-6). Sections 1-3 are documented for completeness but are not new engineering work.

Sections 4-6 remain a **draft proposal — not yet validated with Chris (CGO), Togias, Zoi, or Polina.** Nothing here should go to engineering until sign-off.

---

## Problem

A 12-month bundle sold at booking creation (Component 1) eventually completes its term. Per CGO alignment, once it completes it should "silently" continue as a monthly charge unless the customer opts out — this is the mechanism for lifting MRR on the existing base.

**Correction (2026-09-09, source: Evangelos)**: monthly charging of premium bundles on active subscriptions already exists in production — the bundle is charged every month together with the car's monthly rent/lease payment. So Sections 1-3 below (trigger detection, payment mechanism, monthly extension mechanics) describe a flow that is already live, not a gap. **The confirmed remaining gap is customer notification (Section 4), opt-out (Section 5), and termination enforcement (Section 6)** — nothing in instafleet tells the customer this happened, and opt-out/apalagi enforcement are still unconfirmed.

---

## 1. Trigger & Detection

**Status: already live in production** (source: Evangelos, 2026-09-09) — confirm exact mechanism with Togias for documentation purposes, but do not treat this as new engineering scope.

**Original proposal (superseded)**: Automated, not agent-initiated. A scheduled job checks active subscriptions daily for bundles whose 12-month period is completing within N days (propose N=14, to allow time for the customer notification below to land before the first monthly charge).

- Field needed on the subscription/bundle record: `bundle_term_end_date` (derived from bundle start date + 12 months).
- When the job finds a bundle crossing this threshold, it:
  1. Flags the bundle row (Bundles tab) with a status, e.g. `Rolling to Monthly`.
  2. Kicks off the customer notification (Section 4).
  3. On the term end date, converts the bundle to a recurring monthly line item (Section 3) unless an opt-out was recorded (Section 5).

**Open decision**: should CS get visibility (e.g. a filtered view or a system-generated ticket) before rollover happens, so an agent can catch edge cases (e.g. customer already mid-conversation about cancelling)? Recommend yes — reuse the "Needs Approval"-style ticket pattern from [[instafleet-approval-mechanism]] as a **non-blocking heads-up** ticket, not a gate.

---

## 2. Payment Mechanism

**Status: already live in production** — bundle is charged monthly together with the car's monthly rent/lease payment (source: Evangelos, 2026-09-09). Confirm with Togias whether it's one combined line or two transactions, for documentation purposes only.

**Original proposal (superseded)**: Reuse the payment method already on file for the subscription's recurring monthly fee (Payment & Billing tab → **Recurring Payment Infos**: Payment Method / Bank / IBAN — see [[subscriptions]]). This avoids introducing a second billing rail (Viva link) for a charge that should feel invisible to the customer.

- If recurring payment method is a Viva-stored card: bundle amount added to the existing monthly billing run as one combined charge, itemized in the invoice.
- If recurring payment method is SEPA/direct debit: same — added to the existing debit amount for that cycle.
- Fallback: if no recurring payment method is on file (edge case), do not auto-charge — route to a manual CS follow-up ticket instead of failing silently.

**Open decision**: confirm with Finance/Togias whether the billing system can combine bundle + base monthly fee into a single line, or whether they must post as two separate transactions on the same date.

---

## 3. Silent Monthly Extension — Operational Mechanics

**Status: already live in production** (source: Evangelos, 2026-09-09) — the rollover to monthly billing already happens; remaining work is only the customer-facing layer (Sections 4-6).

**Original proposal (superseded)**:
- On the bundle's term-end date, the system adds a new recurring product line item to the subscription's **Products tab** (same list as [[subscriptions#Products Tab]]), named e.g. "Bundle — Monthly Extension", priced at the bundle's monthly-equivalent rate.
- This line item bills every cycle going forward alongside the base monthly fee, with no manual action required by CS.
- The **Bundles tab** status updates from `Rolling to Monthly` to `Monthly (Active)`.
- All of this is logged automatically in the subscription's **History → Changelog** tab, so there's an audit trail even though no agent touched it.

**Open decision**: is the monthly-equivalent rate a flat 1/12 of the original bundle price, or a different (likely higher) rate to price in the flexibility? This is a pricing decision, not a system one — needs Chris/Togias input.

---

## 4. Customer Notification

**This directly answers the original question: how does the customer find out?**

There is currently no customer-facing subscription dashboard — my.instacar.gr is a document-upload portal only (see [[instacar-offer]], [[customer-facing-platform]]), not a place customers can view active subscription/bundle state. So notification has to be push-based (email), not pull-based (in-app), until/unless a customer portal exists.

**Proposal — two touchpoints, both transactional email:**

1. **Advance notice** (sent when the job flags the bundle, ~14 days before term end): explains the 12-month bundle is ending, that it will continue as a monthly charge of [amount] starting [date] unless the customer opts out, and how to opt out (Section 5). This is the email that carries the legal wording Polina already drafted.
2. **Confirmation at first monthly charge**: a short receipt-style email confirming the new monthly line item and amount, same as any other billing confirmation.

Both emails should be logged automatically to the subscription's **History → Emails** tab in instafleet (this tracking already exists per [[subscriptions]], just needs to be wired to this new automated trigger) — so CS can see in one place whether a given customer was notified, without a manual step.

**Open decision**: SMS as a second channel for the advance notice, given how commercially sensitive a "silent" charge is? Recommend yes as a nudge, especially since a customer objecting after the fact is a support/trust cost. Needs confirmation this is acceptable given the "silent unless opt-out" framing from CGO — an SMS nudge does not contradict silence, it just reduces surprise-charge complaints.

---

## 5. Customer Opt-Out

**Proposal**: since there's no self-service portal, opt-out has to be either reply-to-email or contact-CS.

- Advance notice email includes a clear opt-out method: reply to the email, or call/message CS, within the 14-day window.
- CS records opt-out by changing the Bundles tab status to `Opted Out` before the term-end date — this suppresses the auto-conversion job in Section 1.
- If opt-out arrives after the monthly charge has already started: falls under the termination rules in Section 6, not a simple opt-out.

**Open decision**: is a reply-to-email opt-out legally sufficient, or does Polina's wording require a more explicit action (e.g. a signed form, a portal click)? Needs legal confirmation.

---

## 6. Termination Enforcement (post-rollover)

Per the original business rule:
- If the customer has used their annual **apalagi**: termination not allowed until the second 12-month cycle completes.
- If not: termination is immediate, customer forfeits the additional kilometers included in the bundle.

**Proposal**: this needs a boolean flag on the subscription (`apalagi_used_this_cycle`) that CS/system already tracks somewhere (needs confirmation where — possibly already exists as a subscription field, needs a data audit). Termination requests on a `Monthly (Active)` bundle should check this flag:
- If true → block termination in instafleet, surface the second-cycle-completion date to the agent.
- If false → allow termination, auto-remove the extra-km allowance from the subscription's products.

**Open decision**: is `apalagi` usage already tracked as a discrete field anywhere in instafleet today, or does this need to be added as new data model work? This is a prerequisite blocker for enforcement — needs a data audit before scoping.

---

## Summary of Open Decisions Needing Sign-off

| # | Decision | Owner |
|---|----------|-------|
| 1 | CS heads-up ticket before rollover — needed? | Product/CS |
| 2 | Can billing system combine bundle + base fee into one charge? | Togias/Finance |
| 3 | Monthly-equivalent rate: flat 1/12 or premium? | Chris/Togias (pricing) |
| 4 | SMS nudge in addition to email? | Chris (commercial risk) |
| 5 | Is reply-to-email opt-out legally sufficient? | Polina (legal) |
| 6 | Is apalagi usage already a tracked field? | Togias (data audit) |

---

## Related pages
- [[bundle-sales-spec]]
- [[instafleet-approval-mechanism]]
- [[subscriptions]]
- [[instacar-offer]]
- [[customer-facing-platform]]
