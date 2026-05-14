# instacar

**Summary**: Greek automotive company operating in used car sales and leasing, serving both B2C individuals and B2B small companies.
**Context**: [instacar]
**Sources**: instacar_claude_project_instructions.md
**Last updated**: 2026-04-15

---

## What instacar does

instacar is a Greek automotive company with two core business lines:

- **Used car sales** — selling vehicles to B2C individuals and B2B small companies
- **Car leasing** — offering leasing/subscription products to B2C individuals and B2B small companies

**Market**: Greece. Key characteristics:
- Price sensitivity is high
- Trust signals matter a lot (Greeks are skeptical of online-only transactions)
- Cash and installment payments are common
- Seasonal demand patterns differ from Northern European markets
- Regulatory context is Greek/EU

**Stage**: Growth and scaling — actively expanding operations, user base, and internal tooling.

## Competitive landscape

| Competitor | Type |
|---|---|
| Flexcar | Car subscriptions/leasing |
| Spotawheel | Used car marketplace |
| Traditional leasing companies | Leasing |

## Leadership and team

- **Head of Product**: Dimos (Dimosthenis Avgeris)
- **CTO/CEO**: weekly syncs for status and strategy
- Day-to-day collaboration primarily with engineering team

## Products

| Product | Description |
|---|---|
| [[customer-facing-platform]] | Main buyer-facing platform for search, discovery, purchase, and lease |
| [[instafleet]] | Internal fleet management tool (CRM + lifecycle + contracts + ARM) |

## Active roadmap initiatives

| Initiative | Description |
|---|---|
| [[kill-pipedrive]] | Migrate Sales team fully off Pipedrive into instafleet |
| Kill Trello | Migrate Trello usage into instafleet -- scope TBD, see [[instafleet]] |
| [[defleet]] | Define fleet-end-of-life process and team handoffs |
| Booking Flow Redesign | Redesign booking flow in main app -- scope TBD, see [[customer-facing-platform]] |
| [[n8n-workflow-automation]] | Automate financial document collection via email |

## Tech stack

| Area | Tool |
|---|---|
| Project management | Linear |
| Analytics | Google Analytics |
| Session recording / heatmaps | Microsoft Clarity |
| Legacy CRM / pipeline | Pipedrive (being phased out) |
| Internal fleet management | instafleet (in development) |
| Workflow automation | n8n |

## Related pages
- [[users-b2c]]
- [[users-b2b]]
- [[customer-facing-platform]]
- [[instafleet]]
- [[instacar-uk-launch-spec]]
