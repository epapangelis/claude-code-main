# Description
Customers need an e-pass (toll transponder) for their subscribed vehicles. Since they are not the legal owners, they cannot request it directly. This ticket tracks the implementation of a workflow where customers request an e-pass via app/web, generating a ticket for instafleet agents to process manually. The delivery of the e-pass will be handled via Box Now integration.

# What we currently do
Currently, there is no automated internal flow for customers to request an e-pass. Requests likely happen ad-hoc via customer support, lacking standardized tracking or visibility for the customer. Delivery is handled manually without Box Now automation.

# What to do
1. Add a "Request E-Pass" button/flow on the active subscription details in App & Web.
2. Integrate the Box Now widget/flow to prompt the user to select their preferred Box Now locker for delivery.
3. Backend: Register request (`POST /subscriptions/{id}/epass-requests`), including the Box Now locker ID, and generate an actionable ticket in instafleet.
4. Backend: Integrate with Box Now API to automatically generate a shipping voucher when the e-pass is ready.
5. instafleet: Create a new ticket category for "E-Pass Requests".
6. instafleet: Display Customer Name, Box Now Locker Details, Vehicle License Plate/Model, Linked Subscription ID, and the generated Box Now shipping voucher.
7. Provide status updates (`Requested`, `Processing`, `Shipped` via Box Now tracking, `Completed`, `Rejected`) that sync back to the customer's app/web view via Box Now webhook statuses.

# Acceptance Criteria
**Given** a customer is viewing an active subscription
**When** they click "Request E-Pass"
**Then** they are prompted to select a Box Now locker for delivery via the Box Now widget

**Given** a customer completes the Box Now locker selection
**When** the request is submitted
**Then** an e-pass request ticket is generated in the instafleet dashboard with the selected locker details

**Given** an instafleet agent marks the e-pass as ready to ship
**When** the status is updated
**Then** the system automatically generates a Box Now shipping voucher and updates the status to `Shipped`

**Given** the Box Now API updates the delivery status to delivered
**When** the e-pass is collected
**Then** the customer receives a notification and sees the status update to `Completed` on their dashboard

**Given** a customer has already requested an e-pass for a specific vehicle
**When** they attempt to request another one
**Then** the system prevents duplicate active requests

# Figjam
[_Flowchart link/placeholder_]

# Figma
**Desktop**: [_Link_] **Mobile**: [_Link_]

# Metrics
- Number of e-pass requests processed through the new flow.
- Time taken from request to `Completed` state.
- Reduction in manual customer support tickets regarding e-passes.
- Box Now voucher generation success rate.

## Notes
- **Assignee:** Evangelos
- **Team:** product
- **Status:** Ready for Tech
- Out of scope: Direct API integration with toll authority portals.
- Dependency: Box Now API credentials and widget integration docs.