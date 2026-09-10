# Description
Draft spec proposal for Component 2 of the bundle sales initiative from CGO (Chris): once a customer's 12-month instacar premium bundle (sold upfront at booking) completes its term, it should roll into a silent monthly extension unless the customer opts out — this is the mechanism to lift MRR on the existing customer base without new acquisition.

This ticket is the full spec proposal (trigger detection, payment mechanism, customer notification, opt-out, termination enforcement), based on `wiki/bundle-monthly-charging-spec.md`. **Status: draft proposal — not yet validated with Chris (CGO), Togias, Zoi, or Polina.** Nothing here should go to engineering until sign-off on the open decisions below.

# What we currently do
A 12-month bundle sold at booking creation (Component 1) eventually completes its term. Per CGO alignment, once it completes it should "silently" continue as a monthly charge unless the customer opts out. Today nothing in instafleet detects this, charges it, or tells the customer it happened. There is no customer-facing subscription dashboard — my.instacar.gr is a document-upload portal only.

# What to do

**1. Trigger & Detection**
Automated, not agent-initiated. A scheduled job checks active subscriptions daily for bundles whose 12-month period is completing within N days (propose N=14, to give the customer notification time to land before the first monthly charge). Needs a `bundle_term_end_date` field (bundle start + 12 months). On crossing the threshold: flag the bundle row (Bundles tab) as `Rolling to Monthly`, kick off customer notification, and on the term-end date convert to a recurring monthly line item unless opted out.
Open decision: should CS get a non-blocking heads-up ticket before rollover (reusing the "Needs Approval"-style pattern) to catch edge cases? Recommend yes.

**2. Payment Mechanism**
Reuse the payment method already on file for the subscription's recurring monthly fee (Payment & Billing tab → Recurring Payment Infos), rather than a second billing rail (Viva link). Bundle amount added to the existing monthly billing run as one combined charge, itemized in the invoice. Fallback: if no recurring payment method is on file, route to a manual CS follow-up ticket instead of failing silently.
Open decision: can the billing system combine bundle + base monthly fee into a single line, or must they post as two separate transactions on the same date? (Togias/Finance)

**3. Silent Monthly Extension — Operational Mechanics**
On the bundle's term-end date, add a new recurring product line item to the subscription's Products tab (e.g. "Bundle — Monthly Extension") priced at the bundle's monthly-equivalent rate, billing every cycle with no manual CS action. Bundles tab status updates from `Rolling to Monthly` to `Monthly (Active)`. Logged automatically in History → Changelog.
Open decision: is the monthly-equivalent rate a flat 1/12 of the original bundle price, or a premium rate for the flexibility? (Chris/Togias — pricing)

**4. Customer Notification** — *directly answers "how does the customer find out"*
No customer-facing subscription dashboard exists, so notification is push-based (email), not pull-based (in-app). Two touchpoints, both transactional email:
- Advance notice (~14 days before term end): explains the bundle is ending, will continue as a monthly charge of [amount] starting [date] unless the customer opts out, carries Polina's legal wording, and explains how to opt out.
- Confirmation at first monthly charge: short receipt-style email confirming the new monthly line item and amount.
Both logged automatically to the subscription's History → Emails tab.
Open decision: add SMS as a second channel for the advance notice, given the commercial sensitivity of a "silent" charge? Recommend yes as a nudge. (Chris — commercial risk)

**5. Customer Opt-Out**
No self-service portal exists, so opt-out is reply-to-email or contact-CS within the 14-day window. CS records opt-out by setting Bundles tab status to `Opted Out`, which suppresses the auto-conversion job. Opt-out arriving after the monthly charge has already started falls under Section 6 (termination), not a simple opt-out.
Open decision: is a reply-to-email opt-out legally sufficient, or does it need a more explicit action (signed form, portal click)? (Polina — legal)

**6. Termination Enforcement (post-rollover)**
Business rule: if the customer has used their annual **apalagi** (insurance excess/deductible waiver — see `docs/index.html` / offer pages for the €500+VAT deductible this waives), termination is not allowed until the second 12-month cycle completes; if not used, termination is immediate and the customer forfeits the bundle's extra kilometers. Needs a boolean flag on the subscription (`apalagi_used_this_cycle`). On termination request against a `Monthly (Active)` bundle: if true, block and surface the second-cycle-completion date to the agent; if false, allow and auto-remove the extra-km allowance.
Open decision: is `apalagi` usage already tracked as a discrete field anywhere in instafleet, or does this need new data model work? This is a prerequisite blocker for enforcement — needs a data audit before scoping. (Togias)

# Acceptance Criteria
**Given** a subscription has an active 12-month bundle approaching its term end
**When** the system detects it is within the notice window (~14 days)
**Then** it flags the bundle as `Rolling to Monthly` and sends the customer an advance-notice email.

**Given** a bundle's 12-month term completes and no opt-out was recorded
**When** the next billing cycle runs
**Then** the bundle is added as a recurring monthly line item, charged via the customer's existing recurring payment method, status set to `Monthly (Active)`, and a confirmation email is sent.

**Given** a customer replies to the advance-notice email or contacts CS to opt out within the notice window
**When** CS marks the bundle as `Opted Out`
**Then** the bundle does not convert to monthly billing.

**Given** a bundle is `Monthly (Active)` and the customer requests termination
**When** the system checks the `apalagi_used_this_cycle` flag
**Then** termination is blocked until the second 12-month cycle completes (if used) or allowed immediately with extra-km removed (if not).

**Given** any customer-facing email in this flow is sent
**Then** it is automatically logged in the subscription's History → Emails tab.

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
- **Assignee**: Evangelos (me)
- **Team**: product
- **Status**: Spec Phase — draft proposal, not ready for engineering sizing until the open decisions above get sign-off from Chris, Togias, Zoi, and Polina.
- Full design writeup: `wiki/bundle-monthly-charging-spec.md`
- Related: `bundle-sales-spec.md`, `instafleet-approval-mechanism.md` (reusable approval/heads-up ticket pattern), `subscriptions.md`
