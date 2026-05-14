# Kill Pipedrive

**Summary**: Initiative to migrate the Sales team fully off Pipedrive into instafleet, eliminating the parallel tool usage that creates friction and data fragmentation.
**Context**: [instacar]
**Sources**: instacar_claude_project_instructions.md, instafleet_team_usage.md
**Last updated**: 2026-04-23

---

## Problem

Sales currently uses [[instafleet]] and Pipedrive in parallel. Booking/deal detail data lives in Pipedrive while availability and booking lists are in instafleet. Reps must switch between both tools to work any deal.

---

## Goal

Consolidate all Sales workflows inside instafleet so Sales operates from a single tool. Pipedrive is decommissioned once all workflows are replicated.

---

## Approach

v1 does not kill Pipedrive outright. instafleet becomes the source of truth for stage management, but Pipedrive stays in sync during the transition. Pipedrive automations are disabled one by one as instafleet takes over each responsibility.

---

## v1 Features

Core capabilities moved from Pipedrive to instafleet:
- Booking stage management (instafleet as source of truth)
- 2-way stage sync between instafleet and Pipedrive
- Email and SMS sending from booking tickets
- Full booking communication history
- Automated No Answer email + SMS
- Customer Type field in bookings
- Car ID and Promised Delivery Date sync
- Payment details (initial + recurring method split)
- Sales view in availability module
- Vehicle plate + insurance display on Car ID entry
- Stage change validation
- Auto-create subscription when booking reaches "Buy the Car"
- Edit booking products (deposit, extra months, guarantee)
- Predel/Temp subscription creation decoupled from Pipedrive

For live ticket status, see Linear project: **Sales Pipeline -> instafleet**.

---

## v2 Scope

- Bookings filter and saved views
- Won time and lost tracking
- Labels management
- PDD sync across Bookings, Subs, and Pipedrive

---

## Affected Teams

- **Sales** -- primary team affected, main beneficiary
- **Product and Engineering** -- building instafleet capabilities
- **Data Engineering** -- parallel track: recreating Pipedrive Insights reports in Power BI via Neon (DAT-62)

---

## Notes

- Subscriptions still carry a `PipedriveID` field as a reference during the transition period. (source: subs export.csv)

---

## QA Session 1 — Findings (2026-04-17)

First QA session completed. Got to Docs Received and Credit Check stage. Session 2 scheduled for Tuesday to cover Credit & Validation, User Management, and Pending items.

(source: QA Kill Pipedrive.md, QA Kill Pipedrive Slack.md)

### Blockers (must resolve before rollout)

1. **Filters & Views** — Bookings list needs filters by owner, stage, labels. Can work temporarily with existing filters but must be built before rollout.
2. **Credit & Validation Process** — QA not completed on this section. Validation rules, credit comments, counter-offer flow, and car ID change logic all need full review in Session 2.

### Non-blockers (improvements, not blocking rollout)

**Booking Creation Modal**
- Add total amount field
- Auto-populate Extra KMS dropdown and price from SKU
- Fetch campaign from SKU at creation
- Prefill labels with defaults
- Replace 12ος/24ος month options with 1/2/3
- Fix missing 12th and 14th month options from dropdown
- instastart: disable or remove the Months field

**Offer & PDF**
- PDF preview before submitting (replace Add+Submit with preview flow)
- Fix discrepancy between booking products and offer.pdf
- Counter-offer: credit team can edit and regenerate PDF independently
- Prefill consents (both)
- Allow discounts in booking products
- Allow custom Extra KMS values

**Booking–Pipedrive Field Sync**
- Sync Origin / Holding Company field
- Sync Company field
- Sync Referral ID (synergatis)
- Billing detail: show explicitly selected option in booking

**Communication & History**
- Auto emails/SMS triggered by stage must log in booking History
- Tel Contact 1 stage change must cancel pending +2/3/5 day reminder
- "Communication failure" stage: remove auto-BCC to drive@
- Magic link / deep link in Send Offer (authorized link opens app directly)
- Communication templates for SMS/mail

**User & Data Management**
- Merge duplicate users/emails
- Duplicate booking detection
- Delete booking — define permissions
- AFM filter in Subscriptions (align with Galanis)
- Users > Subscriptions: show company identifier (AFM/organization)

---

## Related pages
- [[instafleet]]
- [[instafleet-subscriptions]]
- [[subscriptions-data-model]]
- [[instafleet-approval-mechanism]]
