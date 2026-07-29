# Description

Implement a rich image and video gallery on the car detail page across all mobile verticals: **Leasing**, **Sell Vehicles (instatrade)**, **instaride**, and the **instatrade car list**. The gallery pulls vehicle images and videos from the backend API. A marketing campaign banner is overlaid on the upper corner of the carousel. Tapping any image in the carousel opens a **full-screen showroom** where the user can browse all media. Designs differ per platform (iOS vs Android) using native components, but the interaction model and functionality are identical.

# What we currently do

The car detail page on mobile shows a basic image carousel with no full-screen capability, no video support, and no marketing campaign banner. Images are not sourced dynamically per the backend media payload.

# What to do

### 1. Backend / API
- Expose (or confirm existing endpoint for) an ordered list of media items per vehicle: `{ type: "image" | "video", url, thumbnail_url, position }`.
- The first item at position 0 is always the **marketing campaign banner** (if active for that vehicle/campaign).
- Define fallback behaviour when no campaign banner exists (skip gracefully).

### 2. Collapsed carousel (default state)
- Display a horizontally scrollable image carousel at the top of the car detail page.
- **Upper-left corner:** overlay the active marketing campaign banner (e.g., "-50%", brand watermark) as a badge/chip on top of the first image — do not replace the image with the banner.
- Show pagination dots below the carousel.
- The carousel is swipeable left/right.

### 3. Full-screen showroom
- **Tap any image in the carousel** → open the full-screen showroom starting at the tapped item.
- The showroom displays all vehicle images and videos edge-to-edge.
- Support swipe left/right to navigate between items.
- Videos play with audio in full-screen.
- Close via swipe-down or a close button, returning the user to the car detail page.

### 4. Platform-specific implementation

**iOS**
- Use native `UIScrollView` + `UIPageControl` for the collapsed carousel.
- Campaign banner: `UILabel`/`UIView` overlay anchored to the top-leading corner of the first carousel cell.
- Full-screen showroom: `UIPageViewController` or a custom `UIViewController` with `UIPinchGestureRecognizer` support.

**Android**
- Use native `ViewPager2` + `CircleIndicator` (or equivalent) for the collapsed carousel.
- Campaign banner: `TextView`/`View` overlaid using `ConstraintLayout` in the top-start corner of item 0.
- Full-screen showroom: `ZoomableImageView` / `ExoPlayer` within a `DialogFragment` or dedicated `Activity`.

### 5. Verticals in scope
- Leasing car detail page
- Sell Vehicles (instatrade) car detail page
- instaride car detail page
- instatrade car list detail page

### 6. Out of scope (this iteration)
- Vertical feed / expand-to-feed interaction.
- Anchored price / CTA in the gallery.
- Uploading or editing images from within the app.
- AR / 360 view.
- Sharing a specific image externally.

# Acceptance Criteria

**Given** a user opens a car detail page on Leasing, Sell Vehicles, instaride, or instatrade
**When** the page loads
**Then** a horizontally swipeable image carousel is shown, with the marketing campaign banner overlay on the first image (if active for that vehicle), and pagination dots below.

**Given** the user taps any image in the carousel
**When** the tap is registered
**Then** the full-screen showroom opens, starting at the tapped item, displaying all vehicle media edge-to-edge.

**Given** the full-screen showroom is open
**When** the user swipes left or right
**Then** they navigate between vehicle images and videos.

**Given** the user is in the full-screen showroom
**When** they swipe down or tap the close button
**Then** they return to the car detail page.

**Given** no marketing campaign banner is active for the vehicle
**When** the carousel loads
**Then** no banner overlay is shown and the first media item displays normally.

# Figjam

[Flowchart to be added — should cover: carousel → tap → full-screen showroom → dismiss for both iOS and Android]

# Figma

**Desktop**: N/A (Mobile-only ticket)
**Mobile**: [Link to Figma designs to be added]

# Metrics

- **Full-screen open rate:** % of car detail page visitors who tap into the full-screen showroom.
- **Video play rate:** % of sessions with a video item where video is played.
- **Bounce rate change:** Before/after comparison on car detail pages with the gallery enabled.

## Notes

- **Assignee:** Evangelos
- **Team:** product
- **Status:** Backlog
- **Linear:** [PRO-3349](https://linear.app/instacar/issue/PRO-3349/vehicle-image-and-video-gallery-on-mobile-car-detail-pages-leasing)
- Confirm with backend team whether the media payload already includes video URLs or only images, and whether campaign banner data is part of the vehicle API response or a separate campaigns endpoint.
- iOS team uses UIKit/SwiftUI; Android team uses Jetpack Compose or XML-based views — implementation approach to be agreed with each mobile team lead.
