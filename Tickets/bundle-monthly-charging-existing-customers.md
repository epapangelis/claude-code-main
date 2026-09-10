# Description
Once a customer's 12-month instacar premium bundle (sold upfront at booking) completes its term, it should roll into a silent monthly extension unless the customer opts out — this is the mechanism to lift MRR on the existing customer base without new acquisition. This ticket covers the full design: automated trigger detection, payment mechanism, customer notification, opt-out, and termination enforcement (apalagi rule).

This is Component 2 of the broader bundle sales initiative from CGO (Chris). See `bundle-sales-spec.md` and `bundle-monthly-charging-spec.md` in the wiki for full context.

# What we currently do
Bundles are currently only sold as a 12-month upfront payment (via a separate Viva payment link triggered on delivery, or increasingly at booking creation per Component 1). There is no mechanism today to detect when a bundle's 12-month term is ending, no automated monthly charging, and no customer notification of any kind when a bundle transitions to ongoing monthly billing. Customers also have no self-service subscription portal — my.instacar.gr is a document-upload tool only.

# What to do
1. **Trigger & detection**: automated scheduled job detects bundles approaching their 12-month term end (propose ~14 days lead time) and flags them in the subscription's Bundles tab (e.g. status `Rolling to Monthly`).
2. **Payment mechanism**: reuse the payment method already on file for the subscription's recurring monthly fee (Payment & Billing tab) rather than introducing a second billing rail. Add the bundle as a new recurring product line item on the subscription once the term completes.
3. **Customer notification**: since there is no customer-facing subscription dashboard, notify by transactional email at two points — (a) advance notice ~14 days before rollover, including the legal wording already drafted by Polina and how to opt out, and (b) a confirmation email at the first monthly charge. Both logged automatically to the subscription's History → Emails tab.
4. **Opt-out**: customer can opt out via reply-to-email or by contacting CS within the notice window; CS marks the bundle `Opted Out` in the Bundles tab, which suppresses the auto-conversion.
5. **Termination enforcement**: once a bundle is in `Monthly (Active)` status, check the `apalagi` usage flag before allowing termination — if used, block until the second 12-month cycle completes; if not used, allow immediate termination and remove the extra-km allowance.
6. **CS visibility**: non-blocking heads-up ticket to CS before rollover (reusing the "Needs Approval"-style ticket pattern), so an agent can catch edge cases before the silent charge happens.

**Full design detail**: see `wiki/bundle-monthly-charging-spec.md`.

**Open decisions requiring sign-off before this can be sized**:
- Can billing combine bundle + base monthly fee into a single charge, or must they post separately? (Togias/Finance)
- Monthly-equivalent rate: flat 1/12 of bundle price, or a premium for flexibility? (Chris/Togias — pricing)
- SMS nudge in addition to email advance notice? (Chris — commercial risk)
- Is reply-to-email sufficient for opt-out, or does it need a more explicit action? (Polina — legal)
- Is `apalagi` usage already tracked as a discrete field in instafleet, or does it need to be added? (Togias — data audit)

# Acceptance Criteria
**Given** a subscription has an active 12-month bundle approaching its term end
**When** the system detects it is within the notice window
**Then** it flags the bundle as `Rolling to Monthly` and sends the customer an advance-notice email.

**Given** a bundle's 12-month term completes and no opt-out was recorded
**When** the next billing cycle runs
**Then** the bundle is added as a recurring monthly line item, charged via the customer's existing recurring payment method, and a confirmation email is sent.

**Given** a customer replies to the advance-notice email or contacts CS to opt out within the notice window
**When** CS marks the bundle as `Opted Out`
**Then** the bundle does not convert to monthly billing.

**Given** a bundle is in `Monthly (Active)` status and the customer requests termination
**When** the system checks the `apalagi` usage flag
**Then** termination is blocked until the second 12-month cycle completes (if apalagi was used) or allowed immediately with extra-km removed (if not).

**Given** any of the above customer-facing emails are sent
**Then** they are automatically logged in the subscription's History → Emails tab.

# Figjam
[Flow to be added — trigger detection → notification → opt-out window → conversion/termination]

# Figma
**Desktop**: N/A (backend/system flow — email templates only)
**Mobile**: N/A

# Metrics
- % of eligible bundles that convert to monthly vs. opt out
- MRR lift from converted bundles
- Support/complaint volume tied to "surprise" monthly charges
- Opt-out response time relative to notice window

## Notes
- **Assignee:** Evangelos (me)
- **Team:** product
- **Status:** Backlog
- This ticket is not ready for engineering sizing — the open decisions above need sign-off from Chris, Togias, Zoi, and Polina first (see `wiki/bundle-monthly-charging-spec.md`).
- Related: `bundle-sales-spec.md`, `instafleet-approval-mechanism.md` (reusable approval/heads-up ticket pattern).
