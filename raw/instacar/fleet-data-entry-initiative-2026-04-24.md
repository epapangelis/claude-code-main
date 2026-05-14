# Fleet Data Entry Initiative - Session Notes
**Date**: 2026-04-24  
**Participants**: Dimos (Head of Product), CFO (request), Dimitris Fragoulis & Nikos Maistrelis (execution leads)

---

## Problem Statement

Sourcing team maintains fleet data in a Google Sheet that is hitting capacity limits. This is a known blocker across the org but has been deprioritized until now. CFO mandated action to move this workflow into instafleet immediately.

**Key constraint**: Waiting for it to "blow up in our face" is no longer acceptable. High priority.

---

## Initial Spec (from CFO)

Three requirements to migrate fleet data entry from Google Sheets to instafleet:

1. **Make fields editable in instafleet** - Sourcing team cannot currently edit certain fleet/sourcing data fields. Need UI to become editable.
2. **Mass import / backfill** - Historical data lives only in Google Sheet. Need bulk import tool to populate new fields for all past records. Sourcing team will provide CSV with field values + Car IDs.
3. **Expose fields in fleet export** - Fleet export feature must include these new fields so downstream systems can consume them (reports, dashboards, integrations).

---

## Discovery: Permission Issue, Not Feature Gap

During implementation planning, discovered that:

- Invoice detail fields **already exist and are editable in the UI**
- The issue is **permission-based**: sourcing team lacks edit access
- Only product/admin accounts (e.g., Dimos) can currently modify these fields
- Engineering doesn't need to build editable fields; just grant permissions

**Invoice detail fields identified**:
- Invoice Number
- Net Price
- Registration Tax
- Vat
- Transfer Fee
- PlateRelease Fee

---

## Linear Tickets Created

**Parent Ticket**: PRO-3014 - Fleet Data Entry - Migrate from Google Sheets to instafleet
- Status: Ready for Tech
- Priority: High
- Assigned to: Dimos

**Child Tickets**:

1. **PRO-3015** - Grant sourcing team permission to edit invoice details in instafleet
   - Clarified scope: permission grant, not feature build
   - Status: Ready for Tech
   - Priority: High
   - Owner: Dimitris Togias (execution)

2. **PRO-3016** - Mass import fleet sourcing data (backfill)
   - Build admin bulk import tool for CSV → instafleet
   - Validate Car IDs, upsert data, report results
   - Status: Ready for Tech
   - Priority: High
   - Owner: Dimitris Togias (execution)

3. **PRO-3017** - Expose fleet sourcing fields in fleet export
   - Identify export formats in use (CSV/JSON/API)
   - Add new fields to each export format
   - Status: Ready for Tech
   - Priority: High
   - Owner: Dimitris Togias (execution)

---

## Next Steps

1. PRO-3015 can proceed immediately (permission grant)
2. PRO-3016 & PRO-3017 depend on final confirmation from sourcing team on backfill timing and export scope
3. All tickets ready for engineering to pick up

---

## Context

- **Business impact**: Removes manual Google Sheet workaround that's hitting limits
- **Urgency**: CFO mandate, high priority
- **Team alignment**: Sourcing, Finance, Product, Engineering all involved
- **Timeline**: Not specified, but implied "ASAP" given CFO escalation
