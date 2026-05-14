# CTO Call Brief: instafleet UK Pages & DB Requirements

**Date**: 2026-04-23  
**Context**: instacar UK Phase 1 launch discussion (not a finished ticket)  
**Prepared for**: CTO call on instafleet UK technical scope

---

## instafleet Pages Needed (Phase 1)

### Sales Team Only

- **Availability screen** — check car status
- **Bookings list + detail** — view/manage bookings
- **Booking creation modal** — create new bookings
- **Lead capture modal for Instatrade** — reg plate lookup → valuation → personal details → create lead/booking

*Note: CS subscription tabs, ARM, and subscription detail screens postponed to Phase 2 (when app launches)*

---

## Database Scope

### Localization Layer

- Currency: GBP (not EUR)
- Distance unit: miles (not km)
- Phone format: UK numbers

### Instatrade Integration

- Lead record type (plate lookup → valuation via UK API → capture contact details)
- Create lead/booking in DB after validation

### HPI Integration

- Vehicle history badge/report data

### Delivery & Location

- Delivery radius config (Warrington-based, quoted beyond 30 miles)

---

## Open Tech Decisions (Discussion Points)

1. **Parallel build vs. schema-first**  
   Should instafleet UK be built in parallel with frontend, or finalize DB shape first?

2. **Single vs. separate DB instance**  
   Same database with workspace filtering, or separate UK instance?

3. **Kanban stages**  
   To be defined with Chatzisavvas later (not blocking initial DB setup)

---

## Notes

- No subscriptions for Phase 1 (later with the app)
- No CS team interface for Phase 1
- No ARM for Phase 1

---

## Prioritization Context for CEO Call

### Current Instacar Engineering Track

| Initiative | Status | Owner | Est. Effort | Blocker | Notes |
|-----------|--------|-------|-------------|---------|-------|
| **Kill Pipedrive v1** | In QA (April 2026) | Sales team | ~Complete | None | 13 features shipped; v2 scope TBD |
| **Carswaps** | Blocked | Finance validation | TBD | Finance sign-off | 3 hard engineering problems; deposit proration math critical |
| **n8n automation** | Active | Product/Data | ~Complete | None | 50-100+ emails/day target; live in system |
| **instacar UK Phase 1** | Planning/Kickoff | Alexandros C. | TBD | Tech decisions | Separate workspace, 2 verticals, instafleet-lite (Sales only) |
| **Bundle sales monthly fee** | Pending prioritization | Chris Noulis | ~1-2 weeks | MRR shortfall | Straightforward; no blockers |
| **Procurement book** | Pending prioritization | Chris Noulis | ~2-3 weeks | Spec clarity | Customs + ERFUDD logic; process mapping needed |
| **Dealer system access** | Pending prioritization | Chris Noulis | ~3-4 weeks (iterative) | None | 3 separate features; recommend: Bookings & Ticketing first |
| **instacar+ pilot** | Pending prioritization | Chris Noulis | TBD | Togias sync | App roadmap capacity question; ELTREKA scope unclear |

### Key Prioritization Questions for CEO

1. **Sequencing vs. Parallel**: 
   - Is UK Phase 1 a separate engineering track (parallel to kill-pipedrive/carswaps/Chris's 4 projects)?
   - Or does it sequence *after* kill-pipedrive v1 ships (late April/early May)?

2. **Resource Constraint**:
   - How many engineers are available for UK launch?
   - Are they carved out from the core instafleet team, or shared with kill-pipedrive/carswaps?

3. **Market Urgency**:
   - What's the go-live target for UK Phase 1? (Affects parallelization decision)
   - Is this a Q2 2026 launch or Q3?

4. **Dependency Chain**:
   - Does UK need Pipedrive kill-off complete first (to avoid duplicate integrations)?
   - Does UK need carswaps logic before launch? (No, carswaps is Greece-only Phase 1)

### Recommended Priority (if forced to rank)

1. **Kill Pipedrive v1** — finish QA, ship (blocks carswaps, clears Sales pain)
2. **Carswaps** — unblock on Finance, ship (CS team enablement)
3. **instacar UK Phase 1** — DB schema finalization + initial setup (parallel with frontend, expected 4-6 weeks after schema locked)
4. **Chris's 4 projects** — sequence after UK kickoff (Bundle Sales → Procurement → Dealer System → instacar+)

Alternative: If UK is a hard April/May deadline, pull forward UK schema design + crew assignment now; everything else sequences after.
