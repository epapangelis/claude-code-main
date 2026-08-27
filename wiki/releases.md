# Releases

**Summary**: Digest of new features, improvements, and fixes shipped, compiled from every Linear ticket marked Done on the product team (all assignees). Updated monthly.
**Context**: [instacar]
**Sources**: Linear (product team, Done tickets)
**Last updated**: 2026-08-27

***

Newest month first. Each section groups that month's Done tickets into Features & Improvements, Fixes, and Other/Internal (planning, presentations, admin, and infra work that shipped no user-facing change). Descriptions are one-line summaries of the Linear ticket; see the ticket for full detail.

## August 2026

### Features & Improvements

- **Vehicle image & video gallery on mobile car detail pages** (PRO-3349) - rich image/video carousel on car detail pages across Leasing, Sell Vehicles, instaride, and instatrade. Tapping any image opens a full-screen showroom (swipe to browse, video with audio, swipe-down to close). First carousel item can carry a marketing campaign banner overlay (e.g. "-50%") when active. Built natively per platform (UIScrollView/UIPageControl + UIPageViewController on iOS, ViewPager2/CircleIndicator + ZoomableImageView/ExoPlayer on Android). (source: Linear PRO-3349)

### Fixes

- **Unified view: credit emails not appearing** (PRO-3411) - emails were showing in Gmail but not surfacing in instafleet's unified view starting 2026-07-29; fixed same-day, high priority, part of the Kill Pipedrive post-release work. (source: Linear PRO-3411)

## July 2026

### Improvements

- **Vehicle document upload redesign** (PRO-2605) - improvements/redesign of the vehicle document upload flow in the apps. (source: Linear PRO-2605)
- **Sales workspace improvements** (PRO-2578) - general improvements to the instafleet Sales workspace. (source: Linear PRO-2578)

### Fixes

- **Leasing vehicle appearing under personal vehicles** (PRO-3307) - bug where a leasing vehicle incorrectly showed up under the personal vehicles list. (source: Linear PRO-3307)
- **Customer name not clickable on Booking Overview** (PRO-3337) - customer name field on the Booking Overview wasn't linking through to the customer profile. (source: Linear PRO-3337)
- **Subscriptions changed from DH to Standard** (PRO-3389) - data correction on instafleet subscriptions incorrectly set to DriveHome instead of Standard. (source: Linear PRO-3389)

### Other / Internal

- **Mobile application roadmap - next steps** (PRO-2981) - roadmap planning for the mobile app. (source: Linear PRO-2981)
- **Email template deletion request** (PRO-3370) - request to delete unused email templates and adjust deletion permissions. (source: Linear PRO-3370)

## June 2026

### Features & Improvements

- **"Won Date" column and filter in Bookings** (PRO-2518) - added the Pipedrive-equivalent "Won Date" as a column and filter in instafleet Bookings. (source: Linear PRO-2518)
- **Automated generic ticket creation for subscriptions** (PRO-2811) - CS workflow automation that auto-creates generic tickets from subscription events. (source: Linear PRO-2811)
- **GetAccept integration** (PRO-2210) - implemented GetAccept for instafleet Subscriptions (document signing/tracking). (source: Linear PRO-2210)

### Fixes

- **instacar "change" button text cut off** (PRO-3140) - button label was being clipped/truncated. (source: Linear PRO-3140)

### Other / Internal

- **Kill Pipedrive leftovers** (PRO-3193) - cleanup of remaining Pipedrive references/data after migration. (source: Linear PRO-3193)

## May 2026

### Features & Improvements

- **Link Bookings to related subscriptions** (PRO-2896) - bidirectional linking between a Booking and its related Subscription records. (source: Linear PRO-2896)
- **ARM Accidents/Claims: columns and exports** (PRO-3099) - added new columns and export capability to the ARM Accidents/Claims view. (source: Linear PRO-3099)

### Fixes

- **Labels recovery on Bookings/Subscriptions** (PRO-2965) - restored labels that had gone missing on Bookings and Subscriptions. (source: Linear PRO-2965)

### Other / Internal

- **Sales pipeline frontend implementation** (PRO-3079) - frontend implementation work for the Sales Pipeline -> instafleet project. (source: Linear PRO-3079)
- **Slack credentials for n8n bot** (PRO-2892) - credential setup for the n8n Slack bot integration. (source: Linear PRO-2892)
- **Gmail OAuth setup for drive@instacar.gr** (PRO-2885) - OAuth setup enabling [[n8n-workflow-automation]]'s email-triggered document pipeline. (source: Linear PRO-2885)

## April 2026

### Features & Improvements

- **Add Vehicle Document** (PRO-2740) - new capability to add vehicle documents in the apps. (source: Linear PRO-2740)
- **Car History: add ARM reason** (PRO-2953) - ARM ticket reason now recorded in a vehicle's Car History. (source: Linear PRO-2953)

### Fixes

- **Delivery cancellation not resetting Delivery Status** (PRO-2944) - cancelling a subscription delivery now correctly resets the Delivery Status field. (source: Linear PRO-2944)

### Other / Internal

- **Drive Home pricing update** (PRO-2995) - updated Drive Home pricing to new rates. (source: Linear PRO-2995)

## March 2026

### Features & Improvements

- **Pricing in the Availability Table** (PRO-2662) - added pricing data to the instafleet Availability Table. (source: Linear PRO-2662)
- **App onboarding** (PRO-2460) - new app onboarding flow/design. (source: Linear PRO-2460)

### Improvements

- **my.instacar header and navigation update** (PRO-465) - reworked header and navigation on my.instacar. (source: Linear PRO-465)

### Other / Internal

- **n8n Pro Plan purchase and account setup** (PRO-2877) - upgraded n8n plan and set up the account for [[n8n-workflow-automation]]. (source: Linear PRO-2877)

## February 2026

### Features & Improvements

- **Additional filter UI items** (PRO-2572) - added filter UI items as part of the instafleet redesign project. (source: Linear PRO-2572)
- **SKU search on site search** (PRO-2584) - site search now supports searching by SKU. (source: Linear PRO-2584)
- **GIF support in unified view signatures** (PRO-2767) - users can add a GIF in their unified-view email signature. (source: Linear PRO-2767)

### Improvements

- **Booking Details tab improvements** (PRO-2175) - improvements to the Booking Details tab. (source: Linear PRO-2175)
- **Ticket detail improvements (Sales)** (PRO-2171) - improvements to ticket detail in the Sales pipeline. (source: Linear PRO-2171)
- **All document types displayed** (PRO-2689) - apps now display all document types instead of a limited subset. (source: Linear PRO-2689)

## January 2026

### Features & Improvements

- **Instacar+ subscription statuses** (PRO-2548) - new statuses for instacar+ subscriptions. (source: Linear PRO-2548)
- **Vehicle Details page for Leasing** (PRO-2394) - new/updated Vehicle Details page for the Leasing vertical. (source: Linear PRO-2394)

### Improvements

- **Add owned vehicle flow refinement** (PRO-2591) - refined the flow for adding an owned vehicle. (source: Linear PRO-2591)
- **ERFUDD: "AVAILABLE NOW" on expired dates** (PRO-2581) - expired availability dates now show "AVAILABLE NOW" in ERFUDD. (source: Linear PRO-2581)
- **ERFUDD: time shown next to date** (PRO-2582) - availability time now displays alongside the date in ERFUDD. (source: Linear PRO-2582)
- **ERFUDD improvements** (PRO-2620) - further improvements to ERFUDD. (source: Linear PRO-2620)
- **Bookings List & Kanban improvements** (PRO-2177) - improvements to the Bookings List and Kanban views. (source: Linear PRO-2177)
- **instacar+ native clients migration** (PRO-2454) - migrated instacar+ services to native mobile clients. (source: Linear PRO-2454)
- **Generic Ticket Sidebar default state** (PRO-2723) - defined default state for the Generic Ticket sidebar on desktop and mobile. (source: Linear PRO-2723)

### Fixes

- **ARM mail typos** (PRO-2569) - fixed typos in ARM-related emails. (source: Linear PRO-2569)

### Other / Internal

- **2025 capitalization review** (PRO-2663) - year-end capitalization review. (source: Linear PRO-2663)
- **App redesign QAs** (PRO-2557) - QA pass on the app redesign. (source: Linear PRO-2557)

## December 2025

### Features & Improvements

- **DriveHome "ENDEAVORGREECE" coupon activation** (PRO-2563) - activated a coupon code for DriveHome. (source: Linear PRO-2563)

### Fixes

- **Driver's license number: allow letters** (PRO-2636) - driver's license number field now accepts letters, not just digits. (source: Linear PRO-2636)

## November 2025

### Features & Improvements

- **Subscriptions in instafleet (Instacar+)** (PRO-2448) - subscriptions support for Instacar+ inside instafleet. (source: Linear PRO-2448)
- **Service Points Map View** (PRO-2476) - new map view for Service Points. (source: Linear PRO-2476)
- **instatrade dealer email** (PRO-2560) - new dealer email for instatrade. (source: Linear PRO-2560)

### Improvements

- **instacar+ refactor for apps (BE)** (PRO-2529) - backend refactor of instacar+ for the mobile apps. (source: Linear PRO-2529)
- **Logistics Table field placement** (PRO-2544) - reorganized ticket field placement in the Logistics Table. (source: Linear PRO-2544)
- **Logistics Board improvements pt. 2** (PRO-2534) - second round of Logistics Board improvements. (source: Linear PRO-2534)

### Other / Internal

- **Product & Tech KPIs** (PRO-2461) - KPI review for Product & Tech. (source: Linear PRO-2461)
- **instacar+ presentation** (PRO-2452) - stakeholder presentation for instacar+. (source: Linear PRO-2452)
- **instacar+ screen wireframes** (PRO-2470) - structured wireframes prepared for instacar+ screens. (source: Linear PRO-2470)
- **Improvements presentation to C-level** (PRO-2513) - presentation summarizing improvements to leadership. (source: Linear PRO-2513)
- **Billing project breakdown** (PRO-2397) - scoping/breakdown of the billing project. (source: Linear PRO-2397)
- **Credit items** (PRO-2462) - review of credit-related items. (source: Linear PRO-2462)
- **instacar+ ticket creation** (PRO-2528) - UX/UI and card design help for instacar+ ticket creation. (source: Linear PRO-2528)
- **Apps design system handover** (PRO-2463) - handover of the design system to iOS and Android app teams. (source: Linear PRO-2463)

## October 2025

### Features & Improvements

- **USP placement for BoxNow** (PRO-2375) - added BoxNow USP messaging to the car page, car list, and homepage. (source: Linear PRO-2375)

### Improvements

- **Lottie animation and button color update** (PRO-2441) - updated lottie animation and button color/copy. (source: Linear PRO-2441)
- **Work Order beautification** (PRO-2444) - visual cleanup of Work Orders. (source: Linear PRO-2444)

### Other / Internal

- **Microsoft Clarity case study materials** (PRO-2420) - materials and form for a Microsoft Clarity case study (feeds [[blog-microsoft-clarity-framework]]). (source: Linear PRO-2420)
- **Global Prioritization** (PRO-2435) - cross-team prioritization exercise. (source: Linear PRO-2435)
- **Brand Guidelines materials** (PRO-2431) - preparation of brand guideline materials. (source: Linear PRO-2431)
- **BoxNow cancellation** (PRO-2404) - handled cancellation process/terms with BoxNow. (source: Linear PRO-2404)
- **BoxNow PPC reel content** (PRO-2485) - ad content produced for a BoxNow PPC campaign. (source: Linear PRO-2485)

## September 2025

### Features & Improvements

- **Logistics screens: add/edit** (PRO-2226) - new and edited logistics screens. (source: Linear PRO-2226)

### Improvements

- **CS improvements** (PRO-2232) - general Customer Success workflow improvements. (source: Linear PRO-2232)
- **iOS UI Kit import + Geologica font** (PRO-2414) - imported base iOS UI Kit into the design system and replaced SF Pro with Geologica. (source: Linear PRO-2414)
- **Android M3 UI Kit import + Geologica font** (PRO-2415) - imported base Android Material 3 UI Kit and replaced Roboto with Geologica. (source: Linear PRO-2415)
- **Platform-default font sizes (Geologica)** (PRO-2437) - replaced custom oversized fonts with platform-default type scales while keeping Geologica. (source: Linear PRO-2437)

### Other / Internal

- **Logistics release notes** (PRO-2361) - release notes written for a logistics update. (source: Linear PRO-2361)
- **Billing improvements evaluation** (PRO-2373) - evaluation phase for potential billing improvements. (source: Linear PRO-2373)
- **Global Prioritization Q3-Q4 (+Q1 2026)** (PRO-2372) - prioritization planning spanning Q3 2025 through Q1 2026. (source: Linear PRO-2372)
- **Triage presentation** (PRO-2357) - company-wide presentation on the triage process. (source: Linear PRO-2357)

## August 2025

### Other / Internal

- **noindex staging pages** (PRO-2337) - SEO housekeeping, staging pages excluded from indexing. (source: Linear PRO-2337)
- **instatrade: APP** (PRO-2346) - planning/scoping work for the instatrade app. (source: Linear PRO-2346)
- **DS 2025** (PRO-2220) - design system planning for 2025. (source: Linear PRO-2220)

## December 2024

*(no Done tickets on the product team this month)*

## November 2024

### Improvements

- **Filter modal** (PRO-1499) - new filter modal (AR&M to instafleet). (source: Linear PRO-1499)

## September 2024

### Improvements

- **Permissions to Roles (Sell Vehicles)** (PRO-1684) - moved permissions from individual users to roles in Sell Vehicles. (source: Linear PRO-1684)

### Other / Internal

- **SEO: noindex Blueground, CU pages, MyUi & Drupal** (PRO-1694) - SEO housekeeping across several legacy surfaces. (source: Linear PRO-1694)

## March 2024

### Fixes

- **UI inconsistencies on DriveHome** (PRO-1083) - fixed assorted UI inconsistencies on DriveHome. (source: Linear PRO-1083)

## February 2024

### Improvements

- **AR&M: search bar results via ticket ID** (PRO-1284) - AR&M search bar can now search by ticket ID (REP-XXXX). (source: Linear PRO-1284)

## January 2024

### Improvements

- **Email text: 30 days -> 60 days** (PRO-1080) - updated copy on an automated email from a 30-day to a 60-day window. (source: Linear PRO-1080)

## Related pages
- [[roadmap]]
- [[instafleet]]
- [[customer-facing-platform]]
- [[unified-view]]
- [[n8n-workflow-automation]]
- [[design-system]]
