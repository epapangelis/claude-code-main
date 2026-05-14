# n8n Workflow Automation

**Summary**: n8n-only automation for financial document collection at instacar.gr -- customers email documents to drive@instacar.gr and n8n handles identification, upload, status update, and agent notification automatically.
**Context**: [instacar]
**Sources**: PRD_n8n_Workflow_Automation_instacar_v2.pdf, PRD_ n8n-Only Workflow Automation for instacar - Financial Docs.pdf
**Last updated**: 2026-04-15

---

## Problem Being Solved

Agents currently manually download customer financial documents from email and upload them to [[instafleet]]. This is the automation that removes that entirely.

**Target**: eliminate 100% of manual document handling, reduce processing time from hours/days to under 2 minutes, scale to 50-100+ emails/day.

---

## How It Works (End-to-End)

### 1. Email Monitoring

n8n monitors only replies to booking confirmation emails at drive@instacar.gr (not all inbox email). An email is processed only if:
- It is a reply (part of existing thread)
- Subject contains a booking ID (e.g. JNEDNKI8YJ) -- embedded in subject by design
- Has attachments

Ignored: new emails not in booking thread, replies without attachments, all other inbox email.

### 2. Customer and Booking Identification

- Extract booking_id from subject line (fallback: scan body)
- Call `POST /api/v1/integrations/users` with sender email to look up user_id and customer_name
- If user not found: trigger Unknown User flow (see Error Handling)

### 3. Attachment Processing

All attachments processed and uploaded without filtering in Phase 1.
- For each attachment: extract filename, size, type
- Determine document type integer (see mapping below)
- Call `POST /api/v1/integrations/bookings/{bookingId}/documents` with file + type
- Exclude email signatures (small JPG/PNG files)

No filtering rules in Phase 1: no file type restrictions, no size limits, no filename exclusions. Filtering logic added in Phase 2 based on real-world patterns.

### 4. Document Storage

Handled entirely by instacar backend. n8n passes file + booking ID. Backend manages all S3 paths, folder structure, metadata.

### 5. Booking Status Update

After all documents uploaded:
```
PATCH /api/v1/integrations/bookings/{bookingId}
Body: { "status": 3 }
```
Status 3 = "documents uploaded".

### 6. Agent Notification

Slack channel: #n8n (Channel ID: C0AHEQ1GCLR -- configurable, may change before go-live)

Normal notification includes: customer name, booking ID, number of documents uploaded, link to customer profile in instafleet.

No customer notifications are sent by design.

---

## Error Handling

| Scenario | Action |
|----------|--------|
| Unknown sender (email not in DB) | Slack alert "Manual Action Required" with sender email + attachment count + possible booking_id. Do NOT upload. Agent manually investigates. |
| No attachments in reply | Ignore completely. No notification. |
| General API failure | Send error to dedicated Slack error channel (TBD, configurable env variable). Include error type, booking_id, sender email, timestamp. |

---

## API Reference

**Staging host**: hq-api.staging.instacar.dev
**Auth**: `x-api-token` header (see n8n environment config)

| Method | Endpoint | Purpose |
|--------|----------|---------|
| POST | /api/v1/integrations/users | Look up user by email, validate booking IDs |
| POST | /api/v1/integrations/bookings/{ID}/documents | Upload document (file + type integer) |
| PATCH | /api/v1/integrations/bookings/{ID} | Update booking status (send status: 3) |

---

## Document Type Integer Mapping

| Integer | Document Type |
|---------|---------------|
| 1 | Τελευταιο Εκκαθαριστικο |
| 2 | Μισθοδοσια |
| 3 | Α3 |
| 4 | Εκκαθαριστικο |
| 5 | 2 ετων δημοσιευμενος ισολογισμος |
| 6 | Ε3 |
| 7 | Ε5 |
| 8 | 2 ετων επικυρωμενος ισολογισμος |
| 9 | Επικυρωμενος ισολογισμος |
| 10 | Λογαριασμος ΔΕΚΟ |
| 11 | Περιοδικες Δηλωσεις ΦΠΑ |
| 12 | Φορμα Ν |

**Required documents per customer category:**

| Category | Required |
|----------|---------|
| Individual (Ιδιωτης) | 1 (Εκκαθαριστικο), 6 (Ε3), 11 (ΦΠΑ) |
| Companies (ΑΕ, ΙΚΕ, ΟΕ, ΕΕ, ΕΠΕ, etc.) | 6 (Ε3), 11 (ΦΠΑ), 12 (Φορμα Ν) |

---

## Open Items

| Item | Status |
|------|--------|
| OCR / field extraction for billing details | In discussion. Design must allow adding later. |
| Error Slack channel | TBD. Build as configurable env variable. |
| Agent notification Slack channel | Currently #n8n. May change before go-live. |
| Customer type inference | Confirm how Ιδιωτης vs Εταιρειες is determined from users API response. |
| Test documents for staging | Sample PDF, PNG, DOCX files needed. |

---

## User Journey Summary

**Customer**: receives booking email with booking_id in subject -> replies with attachments -> receives no confirmation (by design).

**Agent**: receives Slack notification with customer name + booking ID + document count -> clicks link to instafleet profile -> reviews docs and proceeds with credit check (or investigates if unknown sender).

---

## Non-Goals (Phase 1)

- No customer notifications (no receipt confirmation, no error messages)
- No document quality checks (blur detection, completeness)
- No Gemini AI document categorisation
- No integration with credit check systems beyond storage
- No customer portal for document status

---

## Related pages
- [[instafleet]]
- [[instacar-api]]
- [[kill-pipedrive]]
