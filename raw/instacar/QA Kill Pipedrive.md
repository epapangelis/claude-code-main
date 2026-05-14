# QA Kill Pipedrive - Session 1 (16/04/2026)

---

## Slack Summary (GR)

Κάναμε την πρώτη συνεδρία QA για το Kill Pipedrive. Πήγαμε μέχρι το στάδιο Docs Received και Credit Check.

Εντοπίσαμε αρκετά θέματα που χρειάζονται δουλειά πριν το rollout:
- Το booking creation modal χρειάζεται βελτιώσεις (φίλτρα, labels, total amount, extra KMS από SKU, preview PDF)
- Υπάρχουν gaps στο sync με Pipedrive (Origin, Company, Referral ID, Billing detail)
- Τα auto emails/SMS δεν καταγράφονται στο History
- Το instastart χρειάζεται απενεργοποίηση του πεδίου Months
- Διάφορα θέματα στο offer/PDF flow (discrepancy με products, preview πριν submit, discounts)

Συνεχίζουμε την Τρίτη για το υπόλοιπο QA (Credit & Validation, User Management, Pending items).

---

**Status**: Incomplete - got to Docs Received and Credit Check stage
**Next session**: Tuesday (continue from Credit & Validation onwards)

---

## Booking Creation Modal

- Add filters and sorting to Bookings list (owner, stage, labels)
- Add total amount field to booking creation modal
- Prefill labels with defaults
- Extra KMS: auto-populate dropdown and price from SKU
- Fetch campaign from SKU at booking creation
- Replace 12ος/24ος month options with 1/2/3
- Fix missing 12th and 14th month options from dropdown
- instastart: disable or remove the Months field

---

## Offer & PDF

- PDF preview before submitting (replace Add+Submit with preview flow)
- Fix discrepancy between products in booking and what appears in offer.pdf
- Counter-offer: credit team can edit and regenerate PDF independently
- Prefill consents (both)
- Allow discounts in booking products
- Allow custom extra KMS values

---

## Booking-Pipedrive Field Sync

- Sync Origin / Holding Company field
- Sync Company field
- Sync Referral ID (synergatis)
- Billing detail: show explicitly selected option in booking

---

## Communication & History

- Auto emails/SMS triggered by stage must log in booking History
- Tel Contact 1 stage change must cancel pending +2/3/5 day reminder
- "Communication failure" stage: remove auto-BCC to drive@
- Magic link / deep link in Send Offer (authorized link opens app directly)
- Communication templates for SMS/mail

---

## Credit & Validation

- VALIDATION: if product price delta exceeds threshold, show popup "Offer needs credit check again, back to Docs Received"
- Credit comments visible in instafleet booking
- Car ID change: determine if new credit check is required and refresh products/offer accordingly

---

## User & Data Management

- Merge duplicate users/emails
- Duplicate booking detection
- Delete booking - define permissions
- AFM filter in Subscriptions (align with Galanis)
- Users > Subscriptions: show company identifier (AFM/organization)

---

## Pending / TBD

- When to capture AFM in booking flow
- Eleni proplirosi (clarify what this means)
- Ping Polymenakos on post-Easter todo item
- Filters + Views MVP scoping
