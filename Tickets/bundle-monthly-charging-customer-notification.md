# Description
Define and build the customer notification flow for when a premium bundle rolls into (or is added as) a monthly charge on an existing customer's subscription. Monthly bundle billing itself already exists in production (charged together with the car's monthly rent), but there is currently no mechanism to tell the customer this is happening. This ticket specs a multi-channel notification plan using instacar's existing communication channels, rather than email-only.


# What we currently do
Monthly bundle charging already happens automatically, combined with the car's monthly rent payment. No customer notification of any kind is sent when this happens — no email, no SMS, no in-app signal. Customers have no self-service subscription portal (my.instacar.gr is document-upload only), but the main customer-facing API does already expose `GET /v3/notifications` (web + mobile), and a separate initiative (PRO-3533, Premium Bundle Badge on mobile) is already specified including a "Bundle Details" screen on iOS/Android.

# What to do
Multi-channel notification plan, prioritized by reliability and legal weight:

1. **Email (primary/authoritative)**: advance notice sent ~14 days before the bundle rolls into monthly billing (or immediately, if it's already live and this is a retroactive gap), carrying Polina's legal wording and opt-out instructions. Confirmation email at first monthly charge. Built via existing Unified View template system (GR/EN). Logged automatically to Subscription History → Emails.
2. **In-app / push notification (secondary)**: use the existing `GET /v3/notifications` endpoint to surface a notification in the customer-facing app, deep-linking into the Bundle Details screen being built under PRO-3533. This is the channel most customers will actually see first.
3. **SMS (nudge, advance notice only)**: short SMS pointing to the email / in-app notification, specifically to reduce "surprise charge" complaints given this is a commercially sensitive, silent-by-default flow. Logged to Subscription History → SMS.
4. **CS heads-up (internal, non-blocking)**: system-generated ticket to CS before rollover so an agent can catch edge cases (e.g. customer already mid-conversation about cancelling) — reuses the "Needs Approval"-style ticket pattern.

**Dependency**: coordinate with PRO-3533 (Premium Bundle Badge / Bundle Details screen) so the in-app notification has somewhere to deep-link to.

**Open decisions requiring sign-off before this can be sized**:
- Is SMS acceptable alongside the "silent unless opt-out" framing, or does Chris consider it contradictory? (Chris)
- Is reply-to-email / in-app opt-out legally sufficient, or does it need a more explicit action? (Polina)
- Timing: does PRO-3533's Bundle Details screen need to ship first, or can the in-app notification launch without a destination screen (fallback: link to email/CS)?
- Retroactive scope: does this notification flow need to cover bundles that already silently rolled over before this ships, or only new rollovers going forward? (Chris/Togias)

# Acceptance Criteria
**Given** a subscription's bundle is rolling into (or already on) monthly billing
**When** the notification flow triggers
**Then** the customer receives an email and an in-app notification, and an SMS nudge for the advance-notice step.

**Given** the customer taps the in-app notification
**Then** they are deep-linked to the Bundle Details screen (PRO-3533) showing the new monthly charge.

**Given** any notification is sent (email, SMS, or in-app)
**Then** it is logged automatically to the subscription's History tab (Emails/SMS sub-tabs).

**Given** the in-app notification API or destination screen is not yet available
**Then** the flow degrades gracefully to email + SMS only, without blocking the rollover.

# Metrics
- % of customers notified via each channel who open/interact with it (email open rate, in-app tap-through, SMS click-through if trackable)
- Support/complaint volume tied to "surprise" monthly charges, before vs. after this ships
- Opt-out rate and response time relative to the notice window