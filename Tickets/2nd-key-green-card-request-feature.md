# Description
Customers need to be able to request a 2nd key and/or a green insurance card for their subscribed vehicles. This ticket tracks the implementation of a workflow where customers request these items via app/web, generating a ticket for instafleet agents to process manually. The delivery of these items will be handled via Box Now integration.

**Strategic Considerations & Limitations:**
- **B2B Customers:** Clarification is needed on whether the process differs for corporate accounts.
- **Defleet Limitations:** Customers should return the 2nd key upon vehicle return.

# What we currently do
Currently, there is no automated internal flow for customers to request a 2nd key or green insurance card. Requests likely happen ad-hoc via customer support, lacking standardized tracking or visibility for the customer. Delivery is handled manually without Box Now automation.

# What to do
1. Add "Request 2nd Key" and "Request Green Insurance Card" buttons/flows on the active subscription details in App & Web.
2. Integrate the Box Now widget/flow to prompt the user to select their preferred Box Now locker for delivery.
3. Backend: Register request (`POST /subscriptions/{id}/document-requests`), including the requested item type (2nd_key or green_card) and the Box Now locker ID, and generate an actionable ticket in instafleet.
4. Backend: Integrate with Box Now API to automatically generate a shipping voucher when the item is ready.
5. instafleet: Create a new ticket category for "Document/Key Requests".
6. instafleet: Display Customer Name, Box Now Locker Details, Vehicle License Plate/Model, Linked Subscription ID, Item Requested, and the generated Box Now shipping voucher.
7. Provide status updates (`Requested`, `Processing`, `Shipped` via Box Now tracking, `Completed`, `Rejected`) that sync back to the customer's app/web view via Box Now webhook statuses.
8. **Product / Ops Task:** Define the B2B request flow and clarify requirements.
9. **Ops Task:** Establish a clear offboarding communication flow to remind customers to return their 2nd key when returning a vehicle.

# Acceptance Criteria
**Given** a customer is viewing an active subscription
**When** they click "Request 2nd Key" or "Request Green Insurance Card"
**Then** they are prompted to select a Box Now locker for delivery via the Box Now widget

**Given** a customer completes the Box Now locker selection
**When** the request is submitted
**Then** a request ticket is generated in the instafleet dashboard with the selected locker details and requested item type

**Given** an instafleet agent marks the item as ready to ship
**When** the status is updated
**Then** the system automatically generates a Box Now shipping voucher and updates the status to `Shipped`

**Given** the Box Now API updates the delivery status to delivered
**When** the item is collected
**Then** the customer receives a notification and sees the status update to `Completed` on their dashboard

**Given** a customer has already requested an item for a specific vehicle
**When** they attempt to request the exact same item again (while active)
**Then** the system prevents duplicate active requests

**Given** a customer is returning their vehicle
**When** the defleet process is initiated
**Then** the customer is explicitly prompted/instructed to return the 2nd key if they received one

# Figjam
[_Flowchart link/placeholder_]

# Figma
**Desktop**: [_Link_] **Mobile**: [_Link_]

# Metrics
- Number of 2nd key and green card requests processed through the new flow.
- Time taken from request to `Completed` state.
- Reduction in manual customer support tickets regarding these items.
- Box Now voucher generation success rate.

## Notes
- **Assignee:** Evangelos
- **Team:** product
- **Status:** Ready for Tech
- Dependency: Box Now API credentials and widget integration docs.
