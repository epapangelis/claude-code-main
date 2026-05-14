# instacar API

**Summary**: instacar API v1.0 (swagger), covering bookings, subscriptions, sales, leasing, users, and integrations endpoints.
**Context**: [instacar]
**Sources**: swagger.json
**Last updated**: 2026-04-15

---

## Overview

The instacar API serves both the web and mobile customer-facing platform. Version 1.0 (swagger). Auth uses BearerAuth for standard endpoints; integration endpoints use `x-api-token` header.

---

## Main Endpoint Groups

### Bookings
- `GET /v3/bookings` -- get all bookings (paginated, sortable)
- `GET /v3/bookings/{id}` -- get booking detail
- Integration: `POST /api/v1/integrations/bookings/{ID}/documents` -- upload document
- Integration: `PATCH /api/v1/integrations/bookings/{ID}` -- update booking status

### Subscriptions
- `GET /v3/subscriptions` -- list subscriptions
- `GET /v3/subscriptions/{id}` -- subscription detail
- `GET /v3/subscriptions/{ID}/delivery` -- delivery info
- `GET /v3/subscriptions/{ID}/documents` -- subscription documents
- `GET /v3/subscriptions/{ID}/drivers` -- drivers on subscription
- `GET /v3/subscriptions/{ID}/services` -- services linked to subscription
- `GET /v3/subscriptions/{ID}/handover/{type}/form` and `/info` -- handover form/info
- `/v4/subscriptions` -- v4 endpoint (newer version)

### Sales (Used Cars)
- `GET /v3/sales` -- list vehicles for sale
- `GET /v3/sales/{ID}` -- vehicle detail
- `GET /v3/sales/{ID}/loans/calculate` -- loan calculation
- `GET /v3/sales/{ID}/loans/santander/calculate` -- Santander loan calculation

### Leasing
- `GET /v3/leasing` -- leasing listings
- `GET /v3/leasing/{ID}` -- leasing detail
- `GET /v3/leasing/downpayment` -- downpayment options
- `GET /v3/leasing/ebikes` / `/{ID}` -- ebike leasing

### Users and Auth
- `POST /v3/login`
- `POST /v3/register`
- `POST /v3/social` -- social login
- `GET /v3/me` -- current user
- `POST /v3/password/forgot` and `/reset`
- `POST /v3/verifyCode` / `resendCode`
- Integration: `POST /api/v1/integrations/users` -- look up user by email (n8n workflow)

### Drivers
- `GET /v3/drivers` / `/{ID}`
- `GET /v3/drivers/{ID}/documents` / `/{docID}`

### Documents
- `GET /v3/documents` / `/{docID}`

### Other
- `GET /v3/brands` / `/{id}` -- car brands
- `GET /v3/notifications` -- user notifications
- `GET /v3/maps/geocode` and `/query` -- maps/location
- `GET /v3/deliveries/options` and `/boxnow/locations` -- delivery options
- `GET /v3/invitations` / `/{id}` / `/{id}/status` -- invitation management

---

## Integration API (n8n / Automation)

Used by [[n8n-workflow-automation]] and other integrations. Separate from the main v3 API.

**Staging host**: hq-api.staging.instacar.dev
**Auth**: `x-api-token` header

See [[n8n-workflow-automation]] for full details on these endpoints.

---

## Language Support

Endpoints support `lang` query parameter: `el` (Greek) or `en` (English).

---

## Related pages
- [[n8n-workflow-automation]]
- [[subscriptions-data-model]]
- [[instafleet]]
- [[customer-facing-platform]]
