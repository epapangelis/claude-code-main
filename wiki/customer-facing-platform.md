# customer-facing-platform

**Summary**: The main instacar product where buyers browse, evaluate, and purchase or lease vehicles — the primary B2C and B2B customer touchpoint.
**Context**: [instacar]
**Sources**: instacar_claude_project_instructions.md
**Last updated**: 2026-04-15

---

## Overview

The customer-facing platform is where [[users-b2c]] and [[users-b2b]] interact with instacar. It covers the full funnel from discovery to conversion.

Key areas:
- **Search and discovery** — browse available vehicles, filter by type, price, specs
- **Vehicle detail pages** — condition reports, photos, pricing, trust signals
- **Conversion funnel** — lead capture, offer generation, booking
- **Financing / leasing flow** — presenting subscription terms, offer acceptance
- **Trust signals** — inspection reports, warranties, HPI badges (see [[instacar-uk-launch-spec]] for UK-specific trust elements)

## Offer experience

When a customer is close to converting, they receive a personalised offer (see [[instacar-offer]]). The offer is sent by email and links to the customer's document portal (my.instacar.gr) where they upload financial documents.

## Document submission

Customers can submit financial documents in two ways:
1. Upload via my.instacar.gr portal
2. Reply to their booking confirmation email with attachments (automated via [[n8n-workflow-automation]])

## Active initiatives

- **Booking Flow Redesign** — improving the booking flow and specific screens on mobile and web; scope TBD
- [[instacar-uk-launch-spec]] — UK expansion of the platform (Phase 1: /buy + sell verticals)

## Related pages
- [[users-b2c]]
- [[users-b2b]]
- [[instacar-offer]] (no page yet -- offer email flow, personalised offer sent before contract signing)
- [[n8n-workflow-automation]]
- [[instacar-uk-launch-spec]]
