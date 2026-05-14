# Fleet Data Entry - Migrate from Google Sheets to instafleet

**Summary**: Sourcing team maintains fleet data in a Google Sheet hitting capacity limits. Initiative moves fleet data entry fully into instafleet with three coordinated workstreams: grant sourcing team permission to edit invoice details, build bulk import tool for historical backfill, and expose fields in fleet export.

**Context**: [instacar]

**Sources**: fleet-data-entry-initiative-2026-04-24.md

**Last updated**: 2026-04-24

**Status**: Ready for Tech (all tickets)

**Priority**: High (CFO mandate)

**Owner**: Dimos (Product)

**Execution leads**: Dimitris Fragoulis, Nikos Maistrelis

---

## The Problem

Sourcing team currently enters fleet data (invoice details, sourcing metadata) into a Google Sheet, which:
- Is hitting capacity limits
- Is a known blocker across the organization
- Creates data drift and manual workarounds
- Has been deprioritized until now

CFO mandate: move this workflow into instafleet immediately. Waiting for it to "blow up" is no longer acceptable.

---

## Key Discovery: Permission Issue, Not Feature Gap

Initial assumption was that invoice detail fields needed to be built and made editable. Discovery revealed:

**Fields already exist and are editable in the UI.** The issue is permission-based.

**Current state:**
- Invoice detail fields exist in instafleet: Invoice Number, Net Price, Registration Tax, Vat, Transfer Fee, PlateRelease Fee
- Only product/admin accounts (e.g., Dimos) can edit these fields
- Sourcing team has no permission to modify them
- Workaround: manually request edits from product/admin

**Solution scope shifted from feature build to permission grant.**

---

## Three Workstreams

### 1. Grant Sourcing Team Permission (PRO-3015)

**Status**: Ready for Tech

**What to do**:
- Identify the permission model in instafleet for invoice detail editing
- Grant sourcing team role/permission to edit all invoice detail fields
- Verify sourcing team can edit independently
- Document the permission change for future team onboarding

**Acceptance Criteria**:
- Sourcing team members can view and edit all invoice fields without product/admin intervention
- Changes persist and are auditable

**Fields affected**:
- Invoice Number
- Net Price
- Registration Tax
- Vat
- Transfer Fee
- PlateRelease Fee

**Owner**: Dimitris Togias (execution)

---

### 2. Mass Import Fleet Sourcing Data (PRO-3016)

**Status**: Ready for Tech

**What to do**:
- Define import file format with sourcing team (CSV: Car ID + field values)
- Build admin/bulk import tool that:
  - Accepts CSV upload
  - Validates Car IDs exist in instafleet
  - Upserts data into invoice detail fields
  - Reports success/failure per row
- Run import once sourcing team provides backfill file

**Acceptance Criteria**:
- All rows in CSV matched to existing vehicles
- Fields populated correctly
- 100% of historical fleet records populated (success rate)

**Timing**: One-time import, non-recurring

**Owner**: Dimitris Togias (execution)

**Depends on**: PRO-3015 (editable fields with permissions)

---

### 3. Expose Fleet Sourcing Fields in Fleet Export (PRO-3017)

**Status**: Ready for Tech

**What to do**:
- Identify which export formats are in use (CSV, JSON, API, etc.)
- Add newly editable fields to each export format
- Ensure field naming is consistent between instafleet and export
- Update any downstream consumers if needed (reports, dashboards, integrations)

**Acceptance Criteria**:
- All sourcing fields from PRO-3015 included in export
- Export values match instafleet values
- No missing data gaps downstream

**Owner**: Dimitris Togias (execution)

**Depends on**: PRO-3015 (editable fields)

---

## Linear Tickets

| Ticket | Title | Status | Priority | Owner |
|--------|-------|--------|----------|-------|
| PRO-3014 | Fleet Data Entry - Migrate from Google Sheets to instafleet (parent) | Ready for Tech | High | Dimos |
| PRO-3015 | Grant sourcing team permission to edit invoice details in instafleet | Ready for Tech | High | Dimos (Exec: Togias) |
| PRO-3016 | Mass import fleet sourcing data (backfill) | Ready for Tech | High | Dimos (Exec: Togias) |
| PRO-3017 | Expose fleet sourcing fields in fleet export | Ready for Tech | High | Dimos (Exec: Togias) |

---

## Success Metrics

- **PRO-3015**: Sourcing team can independently edit 100% of invoice fields (no manual workarounds)
- **PRO-3016**: 100% of historical fleet records populated via bulk import
- **PRO-3017**: Fleet export includes all sourcing fields; no missing data gaps downstream
- **Overall**: Google Sheet fully replaced as source of truth for fleet sourcing data

---

## Notes

- All three workstreams are Ready for Tech and can proceed in parallel
- PRO-3015 is the quickest win (permission grant, not feature build)
- PRO-3016 depends on sourcing team providing the backfill CSV file
- PRO-3017 depends on clarity on which systems consume fleet export
- Timeline not specified, but implied "ASAP" given CFO escalation
- Team alignment: Sourcing, Finance, Product, Engineering all involved

---

## Related pages

- [[instafleet]] -- main product overview
- [[instafleet-subscriptions]] -- CS team subscription module (invoice details are subscription-level)
- [[kill-pipedrive]] -- broader effort to migrate operations into instafleet
