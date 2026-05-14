# Roadmap

**Summary**: Centralized tracker of all feature requests and work items, organized by feature with date requested.
**Context**: [instacar], [personal]
**Last updated**: 2026-04-28

---

## Quick View

| Feature | Context | Date Requested | Estimate | Status |
|---------|---------|---------------|----------|--------|
| Merge persons & organisations in instafleet | [instacar] | 2026-04-23 | TBD | Pending spec — architecture decision |
| soft1 integration with RF & dunning | [instacar] | 2026-04-23 | TBD | Pending spec |
| Credit limit in bulk | [instacar] | 2026-04-23 | TBD | Pending spec |
| Dunning credit | [instacar] | 2026-04-23 | TBD | Spec exists — ready for prioritization |
| Bundle sales with monthly fee | [instacar] | 2026-04-20 | ~1-2 weeks | Pending prioritization |
| Procurement book | [instacar] | 2026-04-20 | ~2-3 weeks | Pending prioritization |
| Dealer system access | [instacar] | 2026-04-20 | ~3-4 weeks | Pending prioritization |
| instacar+ pilot on SV cars | [instacar] | 2026-04-20 | TBD | Blocked — needs sync with Togias |
| instacar UK — Phase 1 launch | [instacar] | 2026-04-15 | TBD | Planning / Kickoff |
| Car swap & subscription linking | [instacar] | 2026-04-15 | TBD | Blocked — awaiting Finance validation |

---

## Features

---

### Merge persons & organisations in instafleet

| Field | Value |
|-------|-------|
| **Date requested** | 2026-04-23 |
| **Requested by** | Dimos |
| **Context** | [instacar] |
| **Status** | Pending spec — architecture decision |
| **Estimate** | TBD |

**What**: Consolidate and merge duplicate persons in instafleet. Currently no organisation entity exists; need to define data model and merge strategy.

**Why**: Data quality issue causing duplicate customer records and operational friction. Organisation entity needed for B2B fleet management.

**Open questions**:
- Merge rules for duplicate persons (how to identify duplicates, which fields win on merge)
- Organisation entity design (hierarchy, permissions, contract inheritance)
- Existing duplicate count and merge backlog

**Notes**: Foundational data model work. Affects customer-facing platform, CS workflows, and B2B subscription management.

---

### soft1 integration with RF & dunning

| Field | Value |
|-------|-------|
| **Date requested** | 2026-04-23 |
| **Requested by** | Dimos |
| **Context** | [instacar] |
| **Status** | Pending spec |
| **Estimate** | TBD |

**What**: Integrate soft1 platform with Referral Finance (RF) for automated dunning (payment recovery).

**Why**: Streamline payment collection workflow and improve cash recovery on subscriptions.

**Open questions**:
- soft1 API capabilities and authentication
- Dunning workflow triggers (failed payment, retry schedule, escalation)
- Reconciliation with existing RF setup

**Notes**: Integration project. Coordinate with Finance/ARM teams on dunning policies.

---

### Credit limit in bulk

| Field | Value |
|-------|-------|
| **Date requested** | 2026-04-23 |
| **Requested by** | Dimos |
| **Context** | [instacar] |
| **Status** | Pending spec |
| **Estimate** | TBD |

**What**: Implement per-user approved booking credit limits. Each user gets an approved limit of bookings they can create without additional verification.

**Why**: Reduce operational overhead. CS team currently verifies booking eligibility per-request; approved limits allow self-serve booking within pre-approved boundaries.

**Scope**:
- User credit limit entity (approved count or amount)
- Booking creation validation (check remaining balance before allowing new booking)
- Admin dashboard for setting/adjusting limits per user
- Reporting on limit utilization

**Open questions**:
- Credit limit definition (by booking count? by contract value?)
- Who approves initial limits (Sales, CS, Finance?)
- Expiry/refresh rules (per month? per contract?)

**Notes**: Efficiency improvement. Likely small scope once credit model is defined.

---

### Dunning credit

| Field | Value |
|-------|-------|
| **Date requested** | 2026-04-23 |
| **Requested by** | Dimos |
| **Context** | [instacar] |
| **Status** | Spec exists — ready for prioritization |
| **Estimate** | TBD |

**What**: Implement dunning credit system to automate payment recovery flows.

**Why**: Reduce manual collection work. Improve cash flow on failed payments.

**Notes**: Spec already exists in system. Does not need design spec work. Ready for engineering prioritization once soft1 integration is clarified.

---

### Bundle sales with monthly fee

| Field | Value |
|-------|-------|
| **Date requested** | 2026-04-20 |
| **Requested by** | Chris Noulis |
| **Context** | [instacar] |
| **Status** | Pending prioritization |
| **Estimate** | ~1-2 weeks |
| **Source** | [[chris-noulis-instafleet-projects-2026-04-20.md]] |

**What**: Add a bundle pricing option with a monthly fee to lift MRR on the existing customer base.

**Why**: Currently a BGT shortfall. Bundle sales is a lever to increase MRR without new customer acquisition.

**Notes**: Straightforward; no complex dependencies flagged. Estimate will firm up after spec.

---

### Procurement book

| Field | Value |
|-------|-------|
| **Date requested** | 2026-04-20 |
| **Requested by** | Chris Noulis |
| **Context** | [instacar] |
| **Status** | Pending prioritization |
| **Estimate** | ~2-3 weeks |
| **Source** | [[chris-noulis-instafleet-projects-2026-04-20.md]] |

**What**: Build procurement reports that track budget deltas on purchase decisions, pulling from instafleet instead of Excel.

**Why**: Current state is 80% Excel + 20% instafleet, creating lack of visibility on committed vs flexible orders and procurement budget performance.

**Two requirements**:
1. New dropdown field on order creation: "Commitment" vs "Flexible" classification
2. New "Customs" stage in delivery flow before "Payment process" — with automatic ERFUDD +30-day rolling logic

**Complexity drivers**: Customs + ERFUDD logic; unclear split between what lives in instafleet vs Excel.

**Notes**: Spec clarity required before locking estimate. Recommend process mapping session with procurement team.

---

### Dealer system access

| Field | Value |
|-------|-------|
| **Date requested** | 2026-04-20 |
| **Requested by** | Chris Noulis |
| **Context** | [instacar] |
| **Status** | Pending prioritization |
| **Estimate** | ~3-4 weeks |
| **Source** | [[chris-noulis-instafleet-projects-2026-04-20.md]] |

**What**: Give dealer partners a richer dashboard with vehicle inventory info, booking management, subscription view, and ticketing — aligned with what the inhouse team sees in instafleet.

**Why**: Dealers currently have limited visibility and productivity tools. Goal is to improve lead management and conversion.

**Three separate features** (recommend shipping in phases):
1. **Vehicle inventory view** — status, website link, availability, category, pricing, ERFUDD; filters as inhouse
2. **Bookings dashboard** — create bookings, view own deals only, auto-link to referral ID, offer PDF with partner template, upload link, approval path on edits, pre-set km packages, history view
3. **Subscription & ticketing** — read-only subscription view (own deals), generic ticket creation (own tickets only)

**Notes**: Recommend shipping Bookings & Ticketing 1st for highest ROI, then Subscriptions. Iterative chunks preferred over monolithic release.

---

### instacar+ pilot on SV cars

| Field | Value |
|-------|-------|
| **Date requested** | 2026-04-20 |
| **Requested by** | Chris Noulis |
| **Context** | [instacar] |
| **Status** | Blocked — needs sync with Togias |
| **Estimate** | TBD |
| **Source** | [[chris-noulis-instafleet-projects-2026-04-20.md]] |

**What**: Run a controlled instacar+ pilot on SV cars with open subscription, ~500 customers, limited functionality and manual support. Include in instadriver app.

**Why**: Differentiate proposition and test operations in a controlled environment before full rollout.

**Blockers**:
- Current project state unknown — need sync with Togias
- Which services are included in the pilot? (ELTREKA not fully implemented)
- App roadmap is currently full — what feature gets deprioritized?

**Notes**: This is a strategy question as much as an engineering question. Estimate (2-3 weeks) only possible once scope and app capacity are resolved.

---

### instacar UK — Phase 1 launch

| Field | Value |
|-------|-------|
| **Date requested** | 2026-04-15 |
| **Requested by** | Company initiative |
| **Project lead** | Alexandros Chatzisavvas |
| **Context** | [instacar] |
| **Status** | Planning / Kickoff |
| **Estimate** | TBD |
| **Source** | [[instacar-uk-launch-spec.md]] |

**What**: Launch instacar.uk as a separate market with Phase 1 covering two verticals only: /buy (used car marketplace) and /instatrade (sell-to-us).

**Scope**:
- /buy: vehicle listing + vehicle detail (GBP/miles, 100-pt inspection, HPI, WhatsApp)
- /instatrade: landing page + UK plate lookup + lead capture
- Static pages: About, FAQs, Terms, Privacy, Contact
- Instacar Promise (10 guarantees) across all key pages
- Separate instafleet workspace (UK), same frontend/backend pattern

**Pending / open items**:
- Marketing copy (USPs) — urgent, blocks multiple frontend tickets
- Cookie consent (Cookiebot) — required before go-live (UK GDPR + PECR)
- WhatsApp routing decision (UK-17)
- Contact email decision: drive@ vs hello@instacar.uk (UK-18)
- instacar.uk domain confirmation (pending with Togias)

**Out of scope for Phase 1**: new cars, PreLeads, pre-book payments, CarFinance.

**Notes**: For live ticket status see Linear project **instacar-uk**.

---

### Car swap & subscription linking

| Field | Value |
|-------|-------|
| **Date requested** | 2026-04-15 |
| **Requested by** | TBD |
| **Context** | [instacar] |
| **Status** | Blocked — awaiting Finance validation on deposit scenarios |
| **Estimate** | TBD |
| **Source** | [[car-swap-discussion.md]] |

**What**: Enable CS agents to manage vehicle swaps as a first-class operation inside instafleet, replacing manual Pipedrive notes. Part of the Kill Pipedrive initiative.

**Scope** (PRD-SWAP-001 v1.0):
- Swap entitlement rules by contract type (M2M: unlimited, 12M: 1 swap, 24M/36M: 2 swaps)
- Booking label enum: New / Car Swap Same Contract / Renewal No Swap / Renewal With Swap / Temp / Predel
- Bidirectional subscription linking (full chain navigation for CS agents)
- Pricing delta indicators (upsale / downsale badges)
- Deposit / Instastart carry-forward logic

**Three hard engineering problems**:
1. Multi-booking race pattern — first booking to reach "For Delivery" wins; others auto-cancelled
2. Deposit proration math — remaining deposit carries forward proportionally
3. Bidirectional subscription linking — doubly linked list at data layer

**Linear project**: `linear.app/instacar/project/car-swaps-instafleet-process-15d6a362f76b` — empty shell at time of writing.

**Blockers**:
- Finance must validate 8-10 deposit calculation scenarios before engineering begins
- Linear project needs populating with issues and milestones after Finance sign-off

---

## How to add to this roadmap

When you add a new source to `raw/` and say "add to the roadmap", Claude will:
1. Extract each feature/request from the file
2. Add a row to the Quick View table
3. Create a detailed section under Features
4. Update `wiki/log.md`

To query: "What was requested on [date]?", "Show me all [context] items", "What's blocked?"

---

## Related pages
- [[instafleet]] — main product being extended
- [[instacar]] — company context
