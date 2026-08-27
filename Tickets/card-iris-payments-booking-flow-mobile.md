# Background

The Approved & Payment stage of the app booking details page (PRO-3495) already ships a payment method selector with three options: **Τραπεζική κατάθεση** (Bank deposit — enabled), **Πληρωμή με κάρτα** (Card — disabled, "coming soon"), and **Πληρωμή με IRIS** (IRIS — disabled, "coming soon"). Only bank deposit works today: the customer copies an IBAN from a bottom sheet, uploads a proof-of-deposit screenshot, and the booking advances to **Customer Paid** once the proof is received (manually verified).

This ticket is the follow-up: **implement the Card and IRIS options that are already designed and placed in the UI but disabled**, so customers can pay instantly in-app instead of doing a manual bank transfer + proof upload + manual verification. This is net-new payment processing capability for instacar mobile (Android/iOS) — no card or IRIS payment integration exists anywhere in the app today.

# Related tickets

- [APPS-709](https://linear.app/instacar/issue/APPS-709/apps-booking-details-page-structure-of-booking-page) — parent ticket, general booking details page structure
- [PRO-3494](https://linear.app/instacar/issue/PRO-3494/apps-booking-details-page-under-review-stage-page) — Under review stage (previous stage in the same flow)
- [PRO-3495](https://linear.app/instacar/issue/PRO-3495/apps-booking-details-page-approved-and-payment-stage) — Approved & Payment stage; **this ticket implements the two payment methods left disabled there**
- [PRO-3452](https://linear.app/instacar/issue/PRO-3452/backend-map-fleet-booking-stages-to-ui-end-user-stages) — Backend: maps fleet booking stages to UI end-user stages; the Customer Paid transition triggered by this ticket must plug into that mapping
- [[instafleet-billing-detail-selection]] (PRO-2996) / [[instafleet-billing-validation]] (PRO-2997) — billing detail selection/validation feeding the "Στοιχεία τιμολόγησης" section on the same screen

**Figma link (existing, PRO-3495)**: [payment method + billing](https://www.figma.com/design/MsFNqVyvmMGkP4XBUBAh2m/New-instacar-App?node-id=10076-159371) — the Card/IRIS radios and the target screen this ticket builds from are already in this file, just disabled.

**Figma link (new, this ticket)**: [_Card entry + IRIS flow screens — to be designed_]

# What we currently do

- The "Πληρωμή αρχικών εξόδων" (Payment of initial costs) screen (PRO-3495) shows Card and IRIS as radio options but they're disabled/not tappable — "coming soon" copy only, no underlying flow.
- Bank deposit is the only working path: bottom sheet with IBANs per bank (loaded from `payment_methods.bank_accounts`, never hardcoded), deposit amount (`initial_payment_amount`), a file-picker upload for proof of deposit, and a success screen. The booking only moves to **Customer Paid** after that manual proof is reviewed.
- Outside the app, the only other payment collection mechanism is a Viva Wallet payment link triggered manually (e.g. for bundle payments — see [[bundle-sales-spec]]), which is not tied to this in-app flow.
- No card tokenization, 3D Secure/SCA handling, or IRIS bank-redirect flow exists on Android or iOS. No PSP mobile SDK is integrated (assumed greenfield — needs confirmation from mobile eng on any prior spike).

# What to do

1. **PSP & IRIS setup**
   - Confirm PSP for card + IRIS. Viva Wallet already appears as one of the bank options in the existing bottom sheet (it's a real IBAN entry there), and is already used for the standalone payment-link flow (see [[bundle-sales-spec]]) — confirm whether it's also the intended PSP for native card/IRIS SDK integration, or whether a different provider is required for IRIS specifically.
   - Confirm merchant account is enabled for IRIS (DIAS instant payment scheme) and for card acquiring.
2. **Backend**
   - Payment intent endpoints: initiate, confirm, webhook/callback for async IRIS confirmation, status polling.
   - On confirmed payment (card auth success or IRIS callback), automatically transition the booking to **Customer Paid** — the same target state the bank-deposit proof-upload path reaches today — routed through the stage mapping in PRO-3452.
   - Persist PSP transaction ID, method, amount, and status against the booking so instafleet's Payment & Billing tab ([[booking]]) reflects mobile-originated payments without manual entry.
   - Idempotency for retries/webhook replays; reconciliation job for IRIS given its async confirmation.
3. **Android & iOS**
   - Enable the existing Card and IRIS radios on the Approved & Payment screen (remove "coming soon" disabled state) once their flows exist.
   - **Card**: PSP SDK integration, native card entry (PAN/expiry/CVV), 3DS/SCA challenge handling, result screens (success/failure/retry).
   - **IRIS**: bank selection or redirect/deep-link into the customer's banking app, pending-confirmation state, status polling or push update, handling app return after backgrounding.
   - Reuse the existing screen's static sections (Vehicle card, Στοιχεία τιμολόγησης, Αρχικά κόστη, Επιπλέον υπηρεσίες, Σύνολο) unchanged — only the payment-method branch changes.
   - New success/failure states should mirror the existing "proof received" success screen pattern (primary CTA "Δες την προσφορά σου", clear dismiss) for consistency.
4. **Content/UX** — New Greek/English copy needed for: card entry screen, IRIS flow screens (bank selection, pending, success, failure/timeout), and updated payment-method radio state (no longer "coming soon"). Draft with content design; do not invent Greek copy without their review — flagging as open item below.
5. **instafleet** — Confirm mobile-originated card/IRIS payments populate the Payment & Billing tab (Payment Method, Paid Amount) the same way bank-deposit proof does today, so agents see one consistent record regardless of method.
6. **QA** — Card success/decline/3DS-challenge; IRIS success/timeout/cancel; app killed/backgrounded mid-IRIS; retry and method-switch flows (e.g. card fails, customer falls back to bank deposit or IRIS).

# Button behaviour (new, extending PRO-3495)

*Πληρωμή αρχικών εξόδων (payment method screen)*
- "Πληρωμή με κάρτα" radio — becomes selectable; selecting it and tapping "Συνέχεια στην εξόφληση" opens the native card entry screen instead of the bank-deposit bottom sheet.
- "Πληρωμή με IRIS" radio — becomes selectable; selecting it and tapping "Συνέχεια στην εξόφληση" opens the IRIS flow instead of the bank-deposit bottom sheet.
- Bank deposit behaviour is unchanged (PRO-3495).

*Card entry screen (new)*
- Card fields — standard input/validation; CTA disabled until valid.
- Primary CTA ("Πληρωμή" / Pay) — submits payment via PSP SDK; may trigger a 3DS challenge webview before resolving.
- On success — booking advances to Customer Paid, success screen matching the existing pattern.
- On failure — error state with retry and an option to switch payment method.

*IRIS flow (new)*
- Primary CTA — hands off to bank selection/authorization (in-app or via banking app deep-link).
- Pending state — shown while awaiting IRIS confirmation; app must recover this state correctly if backgrounded/killed and reopened.
- On confirmed — booking advances to Customer Paid, same success screen pattern.
- On timeout/cancel — clear state with retry and method-switch option.

# Acceptance Criteria

**Given** a customer is on the Approved & Payment screen (PRO-3495)
**When** they select "Πληρωμή με κάρτα" and complete card entry (incl. any 3DS challenge)
**Then** the payment is confirmed, the booking moves to Customer Paid, and they see a success screen without leaving the app

**Given** a customer is on the Approved & Payment screen
**When** they select "Πληρωμή με IRIS" and authorize via their bank
**Then** the app reflects the final status (paid/failed/pending) once IRIS confirms, and on success the booking moves to Customer Paid

**Given** a payment is completed via card or IRIS
**When** an agent opens the booking in instafleet
**Then** the Payment & Billing tab shows payment method, amount, and status automatically, matching what the bank-deposit proof flow already records

**Given** a card payment fails or an IRIS payment times out/is cancelled
**When** the customer returns to the payment screen
**Then** they see a clear failure/pending state with retry, and can switch to bank deposit as a fallback

**Given** the app is backgrounded or killed while an IRIS payment is pending
**When** the customer reopens the app
**Then** the booking correctly reflects the latest payment status once available

# Figjam

[_Flowchart: payment method selection → card path (entry → 3DS → result) → IRIS path (bank auth → pending → result) → Customer Paid transition → instafleet sync, to be added_]

# Figma

**Desktop**: [_Link — instafleet Payment & Billing tab, if it needs changes to show mobile-originated payments_]

**Mobile**: [_Link — card entry + IRIS flow screens, extending the existing PRO-3495 Figma file linked above_]

# Metrics

- % of Approved & Payment bookings completed via card or IRIS vs. bank deposit.
- Payment success rate by method (card vs. IRIS vs. bank deposit).
- Time from "Approved" to "Customer Paid" — should drop sharply for card/IRIS vs. the manual bank-deposit + proof-review path.
- IRIS payment confirmation time (median, p95).
- Support tickets related to payment status confusion or manual proof-of-deposit errors (expected to decrease).

## Notes

- **Linear:** [PRO-3502](https://linear.app/instacar/issue/PRO-3502/apps-booking-details-page-card-and-iris-payments-approved-and-payment)
- **Assignee:** Evangelos
- **Team:** product
- **Status:** Backlog
- **Open questions**
  - Confirm PSP for card + IRIS — is it Viva Wallet (already present as a bank option and used for the standalone payment-link flow), or a different provider? Needs confirmation before backend/SDK work starts.
  - Content design needs to supply real Greek/English copy for the new card/IRIS screens — none exists yet; do not ship placeholder copy.
  - Does bank deposit stay available as a fallback/alternative once card and IRIS ship, or does this eventually replace it? Recommend keeping all three, since bank deposit has no dependency on card/PSP failures.
  - Saved cards for future/recurring payments — out of scope for this ticket, potential follow-up.
  - Any Greek regulatory requirement specific to IRIS beyond standard PSP compliance — needs legal/compliance check.
- **Dependency:** PSP contract/SDK access for mobile (Android + iOS), backend payment intent API + PRO-3452 stage-mapping integration, Figma designs for card/IRIS screens, content design copy.
