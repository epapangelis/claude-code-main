# Description
Implement new UI chips on Car Cards across the Home Page and Listing Pages to highlight package duration availability (e.g., month to month, up to 12/24/36 months). These tags will be managed manually via vehicle properties in the Car Catalogue backend.

# What we currently do
Car Cards on the Home Page and Listing Pages currently display availability and offer badges (e.g., "2-DAY DELIVERY", "ΔΙΑΘΕΣΙΜΟ", "ΜΕ 38.000 ΧΛΜ"). However, there is no visual indicator showing the commitment term or package availability options (e.g., Month-to-Month vs 12/24/36 Months) directly on the vehicle card before clicking into the details page.

# What to do
1. **Car Catalogue Integration:** Support custom package availability tags in the Car Catalogue properties (leasing admin):
   - `MHNA-MHNA` (Displayed as: **ΜΗΝΑ-ΜΗΝΑ**)
   - `ΕΩΣ 12 ΜΗΝΕΣ` (Displayed as: **ΕΩΣ 12 ΜΗΝΕΣ**)
   - `ΕΩΣ 24 ΜΗΝΕΣ` (Displayed as: **ΕΩΣ 24 ΜΗΝΕΣ**)
   - `ΕΩΣ 36 ΜΗΝΕΣ` (Displayed as: **ΕΩΣ 36 ΜΗΝΕΣ**)
2. **Car Card UI (Home Page & Listing Pages):** 
   - Render the corresponding chip/badge inside the Car Card metadata section (alongside existing chips like delivery or mileage tags).
   - Apply design system styling consistent with existing chips (typography, padding, rounded corners, brand colors).
3. **Scope Control:** These package availability chips should ONLY appear on Car Cards on the Home Page and Listing Pages.

# Acceptance Criteria
**Given** a vehicle in the Car Catalogue has a package availability tag set in its properties
**When** a user views the Home Page or any Listing Page
**Then** the corresponding chip (e.g., "ΜΗΝΑ-ΜΗΝΑ", "ΕΩΣ 12 ΜΗΝΕΣ", "ΕΩΣ 24 ΜΗΝΕΣ", "ΕΩΣ 36 ΜΗΝΕΣ") is visible on the Car Card.

**Given** a vehicle has no package availability tag defined
**When** the Car Card is rendered
**Then** no package availability chip is displayed.

**Given** a user is viewing pages outside Home Page and Listing Pages
**When** Car Cards or vehicle details are rendered elsewhere
**Then** these specific package availability chips do not break or conflict with existing card elements.

# Figjam
[Link to Figjam flow to be added]

# Figma
**Desktop**: [Link to Desktop Figma designs to be added]
**Mobile**: [Link to Mobile Figma designs to be added]

# Metrics
- Click-through rate (CTR) on Car Cards with package availability chips vs without.
- Conversion rate on vehicles tagged with "ΜΗΝΑ-ΜΗΝΑ" vs longer duration chips.

## Notes
- **Assignee:** Evangelos (me)
- **Team:** product
- **Status:** Ready for Tech
- Tag texts provided by marketing:
  - `MHNA-MHNA` (MONTH TO MONTH)
  - `ΕΩΣ 12 ΜΗΝΕΣ` (UP TO 12 MONTHS)
  - `ΕΩΣ 24 ΜΗΝΕΣ` (UP TO 24 MONTHS)
  - `ΕΩΣ 36 ΜΗΝΕΣ` (UP TO 36 MONTHS)
