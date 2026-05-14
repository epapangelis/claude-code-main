# instafleet

**Summary**: instacar's proprietary internal fleet management tool -- CRM, fleet lifecycle, contracts, and ARM ticketing -- being built to replace Pipedrive and Trello across all internal teams.
**Context**: [instacar]
**Sources**: instacar_claude_project_instructions.md, instafleet_team_usage.md
**Last updated**: 2026-04-20

---

## What It Is

instafleet is instacar's internal operational backbone. It covers:
- CRM and lead management
- Fleet availability and lifecycle tracking
- Booking and contract management
- ARM (Accident, Repair, Maintenance) ticketing
- Customer subscription management

It is a multi-tenant tool with separate workspaces per business unit (instacar Greece, instaride/kineo, and instacar UK in planning).

---

## Teams and Usage

### Sales

- **Availability screen** -- check which cars are available and their current statuses
- **Bookings list** -- view all bookings, filter by status or criteria
- **Booking detail screen** -- view full details of a specific booking
- **Booking creation modal** -- create new bookings

Sales reps currently switch between instafleet and Pipedrive to get a complete picture of any booking. The [[kill-pipedrive]] initiative is eliminating this by consolidating all deal/booking data inside instafleet.

### CS (Customer Success)

CS manages all active subscriptions. The subscription detail screen has multiple tabs:

| Tab | Contents |
|-----|----------|
| Delivery & Return | Delivery and return details and dates |
| Communication | Direct communication with the customer |
| Status | Current subscription status |
| Drivers | Driver information linked to the subscription |
| Documents | Subscription-related documents |
| Changelog / History | Full history of changes to the subscription |

See [[instafleet-subscriptions]] for the full subscription data model.

### ARM (Accidents, Repairs, Maintenance)

ARM manages vehicle incidents and maintenance across the fleet:
- Accident claims and damage assessment
- Repair coordination
- Scheduled and unscheduled maintenance

ARM operates entirely within instafleet (no external tool dependency). Vehicles under ARM are flagged as "On Lease ARM" in the availability and subscriptions views used by Sales and CS.

---

## Key Active Workstreams

- **[[kill-pipedrive]]** -- migrate Sales fully off Pipedrive into instafleet
- **Kill Trello** -- migrate Trello usage into instafleet; scope not yet defined
- **[[n8n-workflow-automation]]** -- document upload automation feeding into instafleet
- **[[instacar-uk-launch-spec]]** -- UK workspace (separate workspace, same infrastructure)

---

## Workspace Structure

instafleet supports multiple workspaces visible in the top-right dropdown. Current workspaces:
- instacar (Greece main)
- instaride / kineo
- instacar UK (planned)

---

## Related pages
- [[instafleet-subscriptions]]
- [[kill-pipedrive]]
- [[subscriptions-data-model]]
- [[instacar-api]]
