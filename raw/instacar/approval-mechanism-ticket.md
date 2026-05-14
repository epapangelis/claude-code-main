# Ticket: Generic Approval Mechanism - System Design

**Type:** Generic Ticket
**Assignee:** Dimos Avgeris
**Team:** Product
**Priority:** Medium
**Ticket Reason:** Product Design / Architecture
**Date:** 2026-04-16

---

## Description

Design and spec a reusable approval mechanism for instafleet that will be used across multiple use cases (instastart quantity, carswap eligibility, discount exceptions, and others TBD).

## Core pattern

- New Ticket Type: "Needs Approval" added to the existing ticket system
- Ticket Reason covers the specific use case (determines routing and auto-assignee)
- Tickets are system-triggered, not manually created by the requestor
- Approver actions the ticket with Approve / Reject (new UI needed on ticket detail)
- Requestor is notified via the same ticket when actioned
- First use case: instastart quantity lock in booking creation, approver role = Zoi Tivikeli

## Flow (instastart use case)

1. Salesperson fills booking including instastart (desired months/config)
2. Hits Add - booking is created as-is
3. System auto-creates a "Needs Approval" ticket tagged/assigned to Zoi, linked to the booking
4. Zoi approves or rejects inside the ticket
5. Salesperson notified via the same ticket to go back and update instastart in the booking
6. Salesperson can re-request as many times as needed (async)

## Open decisions to resolve before spec

1. Approve/Reject UI on ticket detail - explicit button or status change + comment?
2. What is the pending state called in ticket statuses?
3. Are routing rules hardcoded per Ticket Reason or configurable?
4. How is the requestor notification triggered (ticket comment, in-app, email)?

## First implementation target

instastart approval on booking creation modal (see Guarantee Agreement note).
