# Description

The booking pipeline has a **"Docs Uploaded" stage (status 3)** that is currently only reachable via the n8n email automation workflow. There is no direct API surface for the mobile app to:

1. Fetch the user's existing financial documents (already stored against their profile)
2. Allow the user to upload new financial documents from their device
3. Tag/associate one or more of those user-level documents against a specific booking

Documents in the instacar system are **owned by the user, not by a booking**. A booking merely references which of the user's documents are relevant to it. Once all required documents are associated, the booking status must be advanced to `3` ("Docs Uploaded") and instafleet agents must be notified.

This ticket specifies the backend endpoints required to support the **"Docs Uploaded" screen** in the mobile booking flow.

---

# What we currently do

- The only path to booking status `3` is through the n8n automation: a customer emails attachments to `drive@instacar.gr`, n8n identifies the booking, uploads the docs via `POST /api/v1/integrations/bookings/{bookingId}/documents`, and patches the booking status to `3`.
- The mobile app has **no endpoints** to:
  - List documents already stored under a user's profile
  - Upload a new document directly (bypassing email)
  - Link an existing user document to a specific booking
- The integration endpoint `POST /api/v1/integrations/bookings/{ID}/documents` is n8n-only and not authenticated for app users (uses `x-api-token`, not BearerAuth).

---

# What to do

Implement the following three backend capabilities under the authenticated user API (`/v3/` prefix, `BearerAuth`).

---

## Endpoint 1 -- List user's financial documents

```
GET /v3/me/documents
```

Returns all financial documents stored against the authenticated user's profile.

**Query parameters:**
| Param | Type | Description |
|---|---|---|
| `type` | integer (optional) | Filter by document type (1-12, see mapping below) |
| `booking_id` | string (optional) | If passed, flag which documents are already tagged to that booking |

**Response body (200):**
```json
{
  "data": [
    {
      "id": "doc_abc123",
      "type": 1,
      "type_label": "Τελευταίο Εκκαθαριστικό",
      "filename": "ekkatharistiko_2024.pdf",
      "uploaded_at": "2024-02-25T00:00:00Z",
      "size_bytes": 204800,
      "mime_type": "application/pdf",
      "tagged_to_booking": false
    }
  ]
}
```

**Notes:**
- `tagged_to_booking` is `true` when the document is already linked to the `booking_id` passed in the query param
- Documents are sorted by `uploaded_at` DESC (newest first)
- This is the user's document library -- it is not booking-scoped. The same document can be tagged to multiple bookings.

---

## Endpoint 2 -- Upload a new financial document to user profile

```
POST /v3/me/documents
```

Allows the authenticated user to upload a new document to their profile. Storage is handled by the backend (S3). The document is **not automatically tagged to any booking**.

**Request:** `multipart/form-data`
| Field | Type | Required | Description |
|---|---|---|---|
| `file` | binary | Yes | The document file |
| `type` | integer | Yes | Document type integer (1-12) |

**Response body (201):**
```json
{
  "data": {
    "id": "doc_xyz789",
    "type": 1,
    "type_label": "Τελευταίο Εκκαθαριστικό",
    "filename": "ekkatharistiko_2024.pdf",
    "uploaded_at": "2026-08-05T13:00:00Z",
    "size_bytes": 204800,
    "mime_type": "application/pdf"
  }
}
```

**Validation rules:**
- Accepted MIME types: `application/pdf`, `image/jpeg`, `image/png`, `image/heic`
- Max file size: 20 MB
- `type` must be a valid integer between 1 and 12

---

## Endpoint 3 -- Tag documents to a booking

```
POST /v3/bookings/{bookingId}/documents/tag
```

Associates one or more of the authenticated user's documents with a specific booking. This does **not** move or copy the document -- it creates a reference. Documents remain under the user's profile.

**Request body (application/json):**
```json
{
  "document_ids": ["doc_abc123", "doc_xyz789"]
}
```

**Behaviour:**
- Only documents owned by the authenticated user (`me`) can be tagged
- Attempting to tag a document owned by a different user returns `403 Forbidden`
- Tagging a document that is already tagged to the booking is idempotent (no error, no duplicate)
- After tagging, if the booking status is `< 3` (i.e., not yet "Docs Uploaded"), **automatically advance booking status to `3`**
- Fire the same instafleet Slack notification as the n8n flow: customer name + booking ID + document count + link to instafleet profile

**Response body (200):**
```json
{
  "booking_id": "JNEDNKI8YJ",
  "tagged_document_ids": ["doc_abc123", "doc_xyz789"],
  "booking_status": 3
}
```

---

## Endpoint 4 -- Remove a document tag from a booking (v2, optional)

```
DELETE /v3/bookings/{bookingId}/documents/{documentId}/tag
```

Removes the association between a document and a booking. Does not delete the document from the user's profile.

**Behaviour:**
- Only the document owner can remove a tag
- If the removed document was the last one tagged, confirm with product whether to revert booking status back below `3`

---

## Document Type Integer Mapping

| Integer | Document Type | Required For |
|---|---|---|
| 1 | Τελευταίο Εκκαθαριστικό | Individual |
| 2 | Μισθοδοσία | Individual |
| 3 | Α3 | -- |
| 4 | Εκκαθαριστικό | Individual |
| 5 | 2 ετών δημοσιευμένος ισολογισμός | Company |
| 6 | Ε3 | Individual + Company |
| 7 | Ε5 | -- |
| 8 | 2 ετών επικυρωμένος ισολογισμός | Company |
| 9 | Επικυρωμένος ισολογισμός | Company |
| 10 | Λογαριασμός ΔΕΚΟ | -- |
| 11 | Περιοδικές Δηλώσεις ΦΠΑ | Individual + Company |
| 12 | Φόρμα Ν | Company |

**Required documents per customer type:**
- **Individual (Ιδιώτης):** type 1 (Εκκαθαριστικό), type 6 (Ε3), type 11 (ΦΠΑ)
- **Company (ΑΕ, ΙΚΕ, ΟΕ, ΕΕ, ΕΠΕ, etc.):** type 6 (Ε3), type 11 (ΦΠΑ), type 12 (Φόρμα Ν)

The app derives the required document set from `customer_type` in the `GET /v3/me` response.

---

## instafleet Side

- The booking's **Documents tab** in instafleet must display all tagged documents for that booking. Confirm the existing UI reads from the booking-document join table (not a booking-scoped storage folder).
- The `booking_status = 3` change must appear in the booking's **History/Changelog tab**.

---

# Acceptance Criteria

**Given** an authenticated user with an active booking
**When** they call `GET /v3/me/documents?booking_id={id}`
**Then** they receive their full document library with `tagged_to_booking: true/false` per document

**Given** an authenticated user
**When** they call `POST /v3/me/documents` with a valid file (PDF/JPG/PNG/HEIC, max 20 MB) and a valid `type` integer
**Then** the document is stored in S3 under the user's profile and returned with a new document `id`

**Given** a user has one or more documents in their profile
**When** they call `POST /v3/bookings/{bookingId}/documents/tag` with valid document IDs
**Then** those documents are associated with the booking and the booking status advances to `3`

**Given** the booking status has just advanced to `3`
**When** the status change is persisted
**Then** a Slack notification fires to the agents channel with: customer name, booking ID, document count, and instafleet booking link

**Given** a user tries to tag a document that belongs to a different user
**When** the tag request is made
**Then** the API returns `403 Forbidden`

**Given** a document is already tagged to a booking
**When** the user tags the same document again
**Then** the API returns `200 OK` with no duplicate entry

---

# Figjam

[_Flowchart to be added_]

# Figma

**Desktop**: N/A (instafleet documents tab -- confirm existing UI handles tagged docs display)
**Mobile**: Design screens shared -- "Επιλογή εγγράφου" modal and full booking flow with document selection states

# Metrics

- % of bookings reaching "Docs Uploaded" via the app vs. email/n8n automation
- Time from booking creation to docs uploaded (target: decrease significantly)
- Document upload success rate (API error rate)
- Number of unique document types uploaded per booking

## Notes

- **Assignee:** Evangelos
- **Team:** product
- **Status:** Ready for Tech
- Documents are user-scoped, not booking-scoped. The booking-document link is a join table reference only.
- This is the app-side counterpart to the n8n email automation. Both paths must write to the same data model (same documents table, same status field). Do not deprecate `POST /api/v1/integrations/bookings/{ID}/documents`.
- Phase 2: allow users to delete a document from their profile (`DELETE /v3/me/documents/{id}`), with a guard that rejects deletion if the doc is currently tagged to any active booking.
