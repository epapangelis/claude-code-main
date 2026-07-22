# Description

Implement a rich image and video gallery on the car detail page across all mobile verticals: **Leasing**, **Sell Vehicles (instatrade)**, **instaride**, and the **instatrade car list**. The gallery pulls vehicle images and videos from the backend API. A marketing campaign banner is pinned to the upper area of the gallery. Tapping the collapsed carousel expands it into a vertical feed, and tapping any item in the feed opens it full-screen. The price / "Take Offer" CTA is anchored to the bottom of the expanded feed. Designs differ per platform (iOS anchor-based layout vs Android snackbar/attention pattern) using native components, but the interaction model and functionality are identical.

# What we currently do

The car detail page on mobile shows a basic image carousel with no expand/full-screen capability, no video support, no marketing campaign banner, and no in-gallery CTA. Images are not sourced dynamically per the backend media payload.

# What to do

### 1. Backend / API
- Expose (or confirm existing endpoint for) an ordered list of media items per vehicle: `{ type: "image" | "video", url, thumbnail_url, position }`.
- The first item at position 0 is always the **marketing campaign banner** (if active for that vehicle/campaign).
- Define fallback behaviour when no campaign banner exists (skip gracefully).

### 2. Collapsed carousel (default state)
- Display a horizontally scrollable image carousel at the top of the car detail page.
- **Upper-left corner:** overlay the active **marketing campaign banner** (e.g., "-50%", brand watermark) as a badge/chip on top of the first image — do not replace the image with the banner.
- Show pagination dots below the carousel.
- The carousel is swipeable left/right.

### 3. Expand interaction — vertical feed
- **Tap anywhere on the carousel** → animate the carousel expanding vertically to reveal all images and videos in a scrollable vertical feed (full-width items).
- The marketing campaign banner remains visible as the top-pinned item in the feed.
- Videos autoplay muted when they scroll into view; show a play/unmute control.
- The feed is dismissible (collapse back to carousel) via a close/back gesture or button.

### 4. Full-screen viewer
- **Tap any item inside the expanded feed** → open that item full-screen (edge-to-edge).
- Support swipe left/right to navigate between items in full-screen.
- Videos play with audio in full-screen.
- Close via swipe-down or a close button.

### 5. Price / "Take Offer" CTA — anchored in feed
- While the expanded vertical feed is open, the **price + "Πάρε προσφορά" (Take Offer) button** stays anchored at the bottom of the screen above the system navigation bar.
- The CTA must not obscure media items; the feed scrolls behind it with appropriate bottom padding.
- The CTA behaves identically to the one on the standard car detail page.

### 6. Platform-specific implementation

**iOS (anchor = 1 pattern)**
- Use native `UIScrollView` + `UIPageControl` for the collapsed carousel.
- Expand animation: layout anchor-based transition expanding the scroll view vertically.
- Full-screen viewer: `UIPageViewController` or a custom `UIViewController` with `UIPinchGestureRecognizer` support.
- Campaign banner: `UILabel`/`UIView` overlay anchored to the top-leading corner of the first carousel cell.
- Bottom CTA: `UIView` anchored to `safeAreaLayoutGuide.bottomAnchor`.

**Android (snackbar / attention pattern)**
- Use native `ViewPager2` + `CircleIndicator` (or equivalent) for the collapsed carousel.
- Expand animation: `RecyclerView` revealed via `TransitionManager` or `MotionLayout`.
- Full-screen viewer: `ZoomableImageView` / `ExoPlayer` within a `DialogFragment` or dedicated `Activity`.
- Campaign banner: `TextView`/`View` overlaid using `ConstraintLayout` in the top-start corner of item 0.
- Bottom CTA: `CardView` anchored at the bottom using `CoordinatorLayout`; use the snackbar pattern for in-feed confirmations and the attention (highlighted state) pattern for the CTA when the feed is open.

### 7. Verticals in scope
- Leasing car detail page
- Sell Vehicles (instatrade) car detail page
- instaride car detail page
- instatrade car list detail page

### 8. Out of scope (this iteration)
- Uploading or editing images from within the app.
- AR / 360 view.
- Sharing a specific image externally.

# Acceptance Criteria

**Given** a user opens a car detail page on Leasing, Sell Vehicles, instaride, or instatrade
**When** the page loads
**Then** a horizontally swipeable image carousel is shown, with the marketing campaign banner overlay on the first image (if active for that vehicle), and pagination dots below.

**Given** the user taps anywhere on the collapsed carousel
**When** the tap is registered
**Then** the carousel animates and expands vertically, revealing all vehicle images and videos in a scrollable feed, with the price / "Take Offer" CTA pinned at the bottom of the screen.

**Given** the expanded vertical feed is open
**When** the user taps a single image or video item
**Then** that item opens full-screen edge-to-edge; videos play with audio; the user can swipe left/right to navigate adjacent items.

**Given** the user is in full-screen view
**When** they swipe down or tap the close button
**Then** they return to the expanded vertical feed without losing their scroll position.

**Given** the expanded vertical feed is open
**When** the user taps the collapse/back gesture
**Then** the feed collapses back to the standard carousel state.

**Given** no marketing campaign banner is active for the vehicle
**When** the carousel or feed loads
**Then** no banner overlay is shown and the first media item displays normally.

**Given** a video item is in the expanded feed and scrolls into view
**When** the item enters the viewport
**Then** it autoplays muted; a play/unmute button is accessible.

# Figjam

[Flowchart to be added — should cover: collapsed carousel → tap → expanded feed → tap item → full-screen → dismiss flows for both iOS and Android]

# Figma

**Desktop**: N/A (Mobile-only ticket)
**Mobile**: [Link to Figma designs to be added — include iOS anchor frames and Android snackbar/attention frames as shown in the reference screenshot]

# Metrics

- **Gallery engagement rate:** % of car detail page visitors who tap to expand the gallery.
- **Full-screen open rate:** % of expanded-feed sessions where the user taps into full-screen.
- **Video play rate:** % of sessions with a video item where video is played.
- **CTA conversion from gallery:** % of "Take Offer" taps originating while the gallery feed is open vs collapsed carousel.
- **Bounce rate change:** Before/after comparison on car detail pages with gallery enabled.

## Notes

- **Assignee:** Evangelos
- **Team:** product
- **Status:** Backlog
- Reference screenshot shows iOS (anchor=1 layout) and Android (snackbar/attention layout) side by side — designs differ per platform native components but functionality is identical.
- Confirm with backend team whether the media payload already includes video URLs or only images, and whether campaign banner data is part of the vehicle API response or a separate campaigns endpoint.
- iOS team uses UIKit/SwiftUI; Android team uses Jetpack Compose or XML-based views — implementation approach should be agreed with each mobile team lead.
- The "Πάρε προσφορά" button label may vary per vertical (e.g., "Κάνε αίτηση" on instaride) — use the existing CTA label from each vertical's detail page.
- **Linear:** [PRO-3349](https://linear.app/instacar/issue/PRO-3349/vehicle-image-and-video-gallery-on-mobile-car-detail-pages-leasing)
