# Bundle Sales Spec

**Summary**: Spec for the instacar premium bundle offering — three delivery components: upfront bundle at booking, monthly charging for existing customers, and commercial override controls.
**Context**: [instacar]
**Sources**: raw/instacar/Premium Changes in Pricing.md, raw/instacar/chris-noulis-instafleet-projects-2026-04-20.md
**Last updated**: 2026-09-09

---

## Business Goal

Lift MRR on the existing customer base without new acquisition. Bundle sales is the lever. Delays cost acquisition months with suboptimal conversion. (source: Premium Changes in Pricing.md)

---

## Component 1: Bundle Upfront at Booking Creation

**What**: The 12-month bundle appears as a single payment in the offer email, paid upfront alongside sign-up fee and instastart.

**Current state**: Bundle sits as a separate Viva payment link triggered on delivery — creates a disconnect, not trackable at won deal level.

**Target state**: Bundle selectable in booking creation flow, included in total upfront costs. Viva payment link remains for existing subscribers and upsell scenarios where bundle is not part of the initial transaction.

**Status**: In progress with tech team (as of 2026-04-17). Timeline to confirm with Togias.

---

## Component 2: Monthly Charging for Existing Customers

**Update (2026-09-09, source: Evangelos)**: monthly bundle charging is already live in production — the bundle is charged every month together with the car's monthly rent/lease payment. The remaining gap is narrower than originally scoped: customer notification, opt-out, and apalagi-based termination enforcement. See [[bundle-monthly-charging-spec]] for the full breakdown.

**What**: Upsell bundle via contract renewal when remaining duration is below 12 months. Once the 12-month bundle period completes, it rolls into a silent monthly extension unless customer opts out.

**Termination rules**:
- If customer has used their annual apalagi: termination not allowed until second 12-month cycle is completed
- If not: termination is immediate; customer forfeits the additional kilometers included in the bundle

**Legal**: Polina has prepared the relevant legal wording. (source: Premium Changes in Pricing.md)

**Status**: Billing mechanism already live in production. Draft spec written for the remaining gap — see [[bundle-monthly-charging-spec]] (customer notification, opt-out, termination enforcement). Not yet validated with Chris, Togias, Zoi, or Polina.

**Blocker**: Requires alignment with Togias on capacity alongside Kill Pipedrive, UK, CarSwaps, mobile releases, and Overview screens.

---

## Component 3: Commercial Overrides & Approval Routing

**What**: Sales agents should not freely reduce monthly guarantees or subscription pricing. Commercial logic is to trade one month of guarantee (24m and 36m contracts) in exchange for bundle attachment. Override capability currently lives in Pipedrive — must be restricted and routed through Zoi.

**Design constraint**: Approval must be async-friendly. Booking creation must never be blocked. Salesperson creates and sends offer as normal; override request runs in parallel. Zoi acts on it after the fact at a defined checkpoint.

**Implementation**: See [[instafleet-approval-mechanism]] for the approval ticket pattern.

---

## Prioritization Context

| Component | Effort | Status | Blocker |
|-----------|--------|--------|---------|
| Upfront bundle at booking | ~1-2 weeks | In progress | None (confirm with Togias) |
| Monthly charging for existing | Billing: done. Notification/opt-out/enforcement: TBD | Billing live; notification layer pending sign-off | Customer notification, opt-out, and apalagi enforcement design |
| Commercial overrides | Part of approval mechanism | Pending spec | Async approval design |

---

## Related pages
- [[roadmap]]
- [[bundle-monthly-charging-spec]]
- [[instafleet-approval-mechanism]]
- [[kill-pipedrive]]
- [[instafleet]]
