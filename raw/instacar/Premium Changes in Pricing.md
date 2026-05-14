CGO sent me

Hi,  
  
Following on from today’s discussion on **instacar premium**, I’m summarising the three key points we aligned on:  
  
First, we need the ability to charge the bundle upfront as part of the initial transaction. The 12-month bundle should appear as a single payment in the offer email and be paid together with the sign-up fee and instastart. Today, this sits as a separate Viva payment link triggered upon delivery, which creates a disconnect. Bringing it into the core transaction allows us to include it in total deal value, offset it against guarantees where applicable, and—critically—track conversion properly at won deal level. In its current form, this is not enforceable or measurable.  
  
Second, we need to enable monthly charging of the bundle for existing active customers. A large upfront payment is a barrier for the base, and this is our biggest opportunity to lift MRR beyond new acquisitions. The mechanism is via contract renewal with bundle cross-sell when remaining duration is below 12 months. Once the initial 12-month bundle period is completed, it rolls into a silent monthly extension unless the customer opts out. If the customer has used their annual apalagi, termination is not allowed until the second 12-month cycle is completed. If not, termination is immediate and the customer forfeits the additional kilometers included in the bundle. (Polina has already prepared the relevant legal wording.)  
  
Third, to support bundle conversion, we need to control commercial overrides. Sales agents should not be able to reduce monthly guarantees or subscription pricing freely, as the commercial logic is to trade one month of guarantee (for 24m and 36m contracts) in exchange for bundle attachment. Override capability (currently via Pipedrive) should be restricted to specific individuals (e.g. Zoi), with all requests routed through her. This ensures visibility of bundle attachment before any guarantee adjustment is approved.  
  
Let me know if anything above needs further clarification.  
  
As a next step, I’d like your view on timelines for each of the three deliverables, and whether I should step in to help prioritise them into an upcoming sprint.  
  
I’m keen to move quickly here, as delays will cost us valuable acquisition months with suboptimal conversion.  
  
Thanks,
Chris

---

## My Reply (17/04/2026)

Hi Chris,

Thanks for the clear summary. Here are my thoughts on each point:

**1. Bundle upfront at booking creation**
Aligned. The bundle will be available directly in the booking creation flow, with the customer paying upfront alongside the other total upfront costs (sign-up fee, instastart, etc.). The Viva payment link will remain in place for existing subscribers and upsell scenarios where the bundle isn't part of the initial transaction.

On delivery: this is currently in progress with the tech team, with an estimated delivery by Friday. I want to confirm the timeline with Togias once he's back from vacation before committing, as I want to make sure we're aligned on what's actually shippable this week.

**2. Monthly charging for existing customers**
I want to be transparent here - as written, this is not yet a spec I can take to engineering. The business logic is clear in intent, but before we can scope or estimate it, we need answers to a few critical questions:
- What is the technical payment mechanism for monthly charging? (Viva, SEPA, direct debit?)
- How is "remaining duration below 12 months" detected, and what triggers the cross-sell moment? Is it automated or agent-initiated?
- What does the "silent monthly extension" look like operationally? Who charges, when, and how is it tracked in instafleet?
- What does opt-out look like for the customer?
- How does the termination restriction (second 12-month cycle) get enforced in the system?

Once we have clarity on these, I can write a proper spec and sit with Togias to get a size and complexity estimate. I'd also want to loop in Antonis on timing, as we currently have Kill Pipedrive, instacar UK, CarSwaps, mobile releases, and Overview screens all active. I want to make sure we sequence this correctly.

**3. Commercial overrides and approval routing**
I fully understand the intent here, and controlling override visibility is the right call. One concern I want to flag before we commit to this design: the approval routing needs to be async-friendly. A common scenario for our sales team is that an agent is already on the phone with a customer, has explained the offer and said "you'll receive it by email shortly." If the override requires Zoi's approval before the offer can be sent, that flow breaks down in real time.

We need to make sure that booking creation is never blocked - the salesperson should be able to create and send the offer as normal, with the override request running in parallel. Zoi (or whoever the approver is) acts on it after the fact, and any commercial correction happens at a defined checkpoint rather than as a gate. Happy to discuss what that looks like in practice.

Let me know if you'd like to jump on a call to align on (2) and (3) together.

Thanks,
Dimos