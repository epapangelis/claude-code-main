# Description

Customers need to be able to preview their invoices directly within the instacar mobile app (Android & iOS). Currently, invoice access likely requires navigating outside the app or through web views, creating friction.

The head of product noted: _"νομίζω υπάρχει ένα service της softOne που λέγεται webservice το οποίο πρέπει να τα περιλαμβάνει"_ — suggesting that a SoftOne webservice may already expose the invoice data needed for this feature. This should be the first technical avenue to explore.

# What we currently do

No native invoice preview exists in the Android or iOS apps. Customers cannot view their invoices from within the app.

# What to do

1. **Investigate SoftOne webservice** — confirm whether the SoftOne webservice exposes invoice data (PDF or structured data) and document the available endpoints.
2. **Backend** — create or expose an API endpoint that fetches invoice data/PDF from SoftOne and serves it to the mobile clients securely.
3. **Android & iOS** — implement an in-app invoice list and PDF preview screen within the customer app.
4. **UX** — design the invoice list and preview flow following the instacar design system.
5. **Permissions** — ensure customers can only access their own invoices.

# Acceptance Criteria

**Given** a logged-in customer opens the app
**When** they navigate to their invoices section
**Then** they see a list of their invoices fetched from SoftOne

**Given** a customer taps an invoice
**When** the invoice detail/preview opens
**Then** they can view the full invoice (PDF or structured view) without leaving the app

**Given** the SoftOne webservice is unavailable
**When** the app tries to fetch invoices
**Then** the user sees a clear error state with a retry option

# Figjam
[_Flowchart link/placeholder_]

# Figma
**Mobile**: [_Link_]

# Metrics
- % of customers who view at least one invoice in-app post-launch.
- Reduction in invoice-related support requests.
- SoftOne webservice uptime / error rate.

## Notes
- **Linear:** [PRO-3283](https://linear.app/instacar/issue/PRO-3283/invoice-preview-on-android-and-ios)
- **Assignee:** Evangelos
- **Team:** product
- **Status:** Backlog
- **Dependency:** SoftOne API / webservice access and documentation. First step is a tech spike to validate the webservice capability.
