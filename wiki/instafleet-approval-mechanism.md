# instafleet Approval Mechanism

**Summary**: Reusable system-triggered approval flow in instafleet for use cases that require human sign-off before a booking or subscription action is confirmed.
**Context**: [instacar]
**Sources**: raw/instacar/approval-mechanism-ticket.md, raw/instacar/Guarantee Aggrement.md
**Last updated**: 2026-04-23

---

## Problem

Multiple instafleet workflows need a gated approval step (instastart quantity, commercial overrides, car swap eligibility). Currently no standardized pattern exists — approvals are ad hoc, untraceable, and often done via Slack or verbal agreement.

---

## Design

A reusable "Needs Approval" ticket type layered on the existing instafleet ticket system.

- **Ticket Type**: "Needs Approval" (new, alongside existing types)
- **Ticket Reason**: covers the specific use case (instastart override, discount exception, car swap, etc.)
- **Routing**: Ticket Reason determines the auto-assignee (hardcoded per reason in v1)
- **Triggers**: System-generated on a specific user action — not manually created by the requestor
- **Approver actions**: Approve / Reject buttons on ticket detail (new UI)
- **Requestor notification**: Triggered via the same ticket when actioned
- **Async design**: Booking creation is never blocked — approval runs in parallel, corrections applied at a defined checkpoint

---

## First Use Case: instastart Quantity Lock

**Problem**: Sales agents can freely set instastart months in booking creation. This needs to be gated.

**Flow**:
1. Salesperson fills booking including instastart (desired months/config)
2. Hits Add — booking is created as-is
3. System auto-creates a "Needs Approval" ticket assigned to Zoi Tivikeli, linked to the booking
4. Zoi approves or rejects inside the ticket
5. Salesperson notified via the same ticket to update instastart in the booking
6. Salesperson can re-request as many times as needed (async)

**Approver**: Zoi Tivikeli (primary), Nena (secondary)

---

## Second Use Case: Change Vehicle Approval

**Problem**: When a Car ID change happens on a booking, it currently auto-moves to "Approved" state. It should instead go to Credit Board backlog so it can be resubmitted manually.

**Required behavior**: Change Vehicle action does not advance booking to "Approved" — sets it to Credit Board / Backlog status for resubmission.

---

## Third Use Case: Commercial Overrides (Bundle Sales)

**Problem**: Sales agents can freely reduce monthly guarantees or subscription pricing. This undermines bundle attachment commercial logic.

**Required behavior**: Override requests are system-triggered, routed to Zoi (or equivalent approver). Booking creation proceeds — offer can be sent. Override validation happens at a defined checkpoint, not as a gate.

See [[bundle-sales-spec]] for full context.

---

## Open Decisions (to resolve before final spec)

1. Approve/Reject UI on ticket detail — explicit button or status change + comment?
2. What is the pending state called in ticket statuses?
3. Are routing rules hardcoded per Ticket Reason or configurable?
4. How is the requestor notification triggered (ticket comment, in-app, email)?

---

## Related pages
- [[kill-pipedrive]]
- [[carswaps]]
- [[bundle-sales-spec]]
- [[instafleet]]
