# Description
Implement a "Premium Bundle" badge/chip on the mobile apps (iOS & Android) across the car listing page and car details screen. Tapping the badge will navigate the user to a new dedicated screen detailing the benefits of their premium bundle, as well as providing management options like pausing, transferring, or accessing more options.

# What we currently do
Currently, there is no visual indication on the mobile apps for cars that include a premium bundle. The car listing and details screens only show standard car attributes, and users cannot view specific premium bundle benefits or manage them within the app.

# What to do
1. **Car Listing Page:** Add a premium bundle badge/chip to the car cards for vehicles that have a premium bundle attached.
2. **Car Details Screen:** Display the same premium bundle badge/chip prominently near the top of the details view (e.g., near the vehicle title/price).
3. **Bundle Details Screen:** Create a new native screen that opens when the badge is tapped. This screen should display the details and benefits of the premium bundle (e.g., extra kilometers, reduced guarantee, upfront cost vs monthly, etc.).
4. **Bundle Management Actions:** On the Bundle Details screen, add the following actions:
   - "Transfer to another subscription" button/action
   - "Pause" bundle button/action
   - "More options" button
5. **Out of Scope:** Do NOT include any functionality to buy, upgrade, or renew the bundle through the app at this stage. 

# Acceptance Criteria
**Given** a user is browsing the mobile app
**When** they view the car listing page
**Then** cars that come with a premium bundle should display a clear "Premium" badge/chip.

**Given** a user is viewing a specific car's details screen
**When** the car includes a premium bundle
**Then** the "Premium" badge/chip should be prominently visible on the screen.

**Given** a user taps the "Premium" badge/chip on either the listing or details screen
**Then** they are navigated to a new "Bundle Details" screen showing the benefits of the bundle.

**Given** a user is on the "Bundle Details" screen
**Then** they should see actions for "Transfer to another subscription", "Pause", and a "More options" button.

**Given** a user is on the "Bundle Details" screen
**Then** there should be NO options to purchase, upgrade, or renew the bundle.

# Figjam
[Link to Figjam flow to be added]

# Figma
**Desktop**: N/A (Mobile App Ticket) **Mobile**: [Link to Mobile Figma designs to be added]

# Metrics
- Number of taps on the Premium badge.
- View count of the Bundle Details screen.
- Interaction rates with "Transfer", "Pause", and "More options" actions.
- Average time spent on the Bundle Details screen.

## Notes
- **Assignee:** Evangelos (me)
- **Team:** product
- **Status:** Ready for Tech
- **Design System Guidelines:** For iOS, use the `Geologica` font and follow the elevation/shadow and token colors outlined in `DESIGN-ios.md` (e.g., using `Orange` or `Blue` brand colors for the badge). For Android, follow `DESIGN-android.md` guidelines.
- See related business logic context in the `bundle-sales-spec` for details on bundle offerings.
- Buying and renewing functionality is strictly out of scope for this iteration.