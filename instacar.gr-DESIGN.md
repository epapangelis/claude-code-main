# Design System Inspired by InstaCar

## 1. Visual Theme & Atmosphere

InstaCar's design system embodies a bold, energetic automotive marketplace aesthetic anchored by vibrant orange that commands attention and conveys action. The visual personality is modern, approachable, and transaction-focused, with a clean neutral foundation that allows dynamic promotional content to shine. Dark accents and warm orange create high contrast for scannability, while generous whitespace and soft border radiuses prevent the intensity from overwhelming. The system balances commercial urgency (promotional badges, price highlights) with professional credibility through refined typography and structured layouts. This is a purpose-built design language for facilitating car leasing and purchase decisions at speed.

**Key Characteristics**
- Bold primary orange (`#FF6500`) used 68 times for maximum visibility and CTAs
- Neutral grayscale foundation (light backgrounds, dark text) for clarity
- High contrast between actionable elements and passive content
- Rounded pill-shaped buttons and components for approachability
- Layered card-based layouts for product discovery
- Typography-driven hierarchy supporting quick scanning
- Promotional badges in orange and black for urgency
- Minimal shadow usage emphasizing flatness and modernity

## 2. Color Palette & Roles

### Primary
- **Vibrant Orange** (`#FF6500`): Primary brand color, call-to-action buttons, promotional highlights, navigation accents, price emphasis. Used across all interactive elements requiring immediate attention.
- **Deep Black** (`#000000`): Primary text color, body copy, dense information layouts. Provides maximum contrast and readability on light backgrounds.

### Accent Colors
- **Bold Blue** (`#007AFF`): Secondary interactive accent, delivery promotions, informational highlights. Used sparingly for secondary CTAs and status indicators.
- **Vivid Purple** (`#552CFF`): Tertiary accent for special promotions or feature distinction. Limited usage for maximum impact.

### Interactive
- **Orange Border** (`#FF6500`): Active button states, focus indicators, engagement cues. Paired with white backgrounds for maximum contrast.
- **Orange Fill** (`#FF6500`): Primary buttons, promotional cards, hero sections. Full background treatment for highest-priority actions.
- **Black Fill** (`#000000`): Secondary buttons, alternate CTAs, dark promotional badges. Creates visual hierarchy separation from primary orange.

### Neutral Scale
- **Off-White** (`#FFFFFF`): Card backgrounds, button surfaces, primary UI containers. Maximum contrast with dark text.
- **Light Gray** (`#E2E8F0`): Subtle backgrounds, disabled states, secondary surfaces. Creates visual separation without distraction.
- **Lighter Gray** (`#F8FAFC`): Minimal usage background, very subtle differentiation. Reserve for lowest-emphasis surfaces.
- **Medium Gray** (`#EEEFF3`): Secondary neutral, subtle dividers, muted backgrounds. Used sparingly.
- **Dark Gray** (`#8C8C8C`): Muted text, placeholder copy, disabled states.
- **Charcoal** (`#475569`): Secondary text, captions, supporting information. Mid-tone between body black and disabled gray.
- **Slate Gray** (`#1E293B`): Tertiary text, metadata, auxiliary information. Between charcoal and black.
- **Muted Gray** (`#6E7181`): Secondary copy, labels, supporting context. High usage (51 times) for non-emphasis text.
- **Softer Gray** (`#8B8E9E`): Borders, dividers, subtle background variations.
- **Pale Gray** (`#A6A9B7`): Tertiary borders, disabled buttons. Low-contrast divider usage.
- **Lavender Tint** (`#ECECF6`): Ultra-subtle background variation, minimal usage.

### Surface & Borders
- **Card White** (`#FFFFFF`): All card and container backgrounds. Primary surface for content.
- **Border Light** (`#E2E8F0`): Default border color for input fields, subtle dividers, container outlines.
- **Border Subtle** (`#A6A9B7`): Disabled state borders, low-emphasis divisions. Lighter weight than primary borders.

### Semantic / Status
- **Success Green** (`#10AB00`): Success states, completed actions, positive confirmations. Minimal usage (1 instance).
- **Warning Amber** (`#FFAA00`): Warning alerts, caution indicators, attention-needed states. Used sparingly for non-critical notices.

## 3. Typography Rules

### Font Family
**Primary:** Proxima Nova (400, 700 weights), fallback to `system-ui, -apple-system, sans-serif`

**Secondary:** Proxima Nova (fallback to system sans-serif)

All headings and body copy use Proxima Nova. The system relies on weight and size variation rather than font family changes.

### Hierarchy

| Role | Font | Size | Weight | Line Height | Letter Spacing | Notes |
|------|------|------|--------|-------------|-----------------|-------|
| **Display / Hero** | Proxima Nova | 32px | 700 | 48px | 0 | Large promotional headings, section titles |
| **H1 / Page Title** | Proxima Nova | 24px | 700 | 25px | 0 | Top-level page headings, card titles |
| **H2 / Section** | Proxima Nova | 32px | 700 | 48px | 0 | Major section dividers, category names |
| **H3 / Subhead** | Proxima Nova | 16px | 700 | 24px | 0 | Card headings, nested sections, labels |
| **H4 / Medium** | Proxima Nova | 20px | 400 | 28px | 0 | Featured pricing, emphasis copy |
| **Body / Standard** | Proxima Nova | 14px | 400 | 20px | 0 | Primary body text, descriptions, product details |
| **Span / Auxiliary** | Proxima Nova | 16px | 400 | 24px | 0 | Secondary copy, metadata, supporting info |
| **Caption / Fine** | Proxima Nova | 12px | 400 | 16px | 0 | Smallest text, disclaimers, fine print |
| **Button / CTA** | Proxima Nova | 16px | 400 | 24px | 0 | All button labels, interactive text |

### Principles
- Weight drives hierarchy: 700 for headings, 400 for body and interactive elements.
- Size variety is restrained to 4–5 distinct levels, preventing visual chaos.
- Line height is generous (1.25× to 1.5× font size) for readability on light backgrounds.
- Orange pricing (`#FF6500`) receives bold or larger-size treatment to drive attention.
- No letterspacing variation; all values default to 0 for tight, professional appearance.
- Proxima Nova's rounded terminals reinforce the approachable, modern brand personality.

## 4. Component Stylings

### Buttons

#### Primary Button (Orange)
- **Background:** `#FF6500`
- **Text Color:** `#FFFFFF`
- **Font Size:** `16px`
- **Font Weight:** `400`
- **Padding:** `12px 24px`
- **Border Radius:** `9999px`
- **Border:** `0px solid transparent`
- **Min Height:** `44px`
- **Box Shadow:** `none`
- **Hover State:** `background: #E55A00; cursor: pointer;`
- **Active State:** `background: #D45000; transform: scale(0.98);`
- **Disabled State:** `background: #E2E8F0; color: #8C8C8C; cursor: not-allowed;`

#### Secondary Button (Black)
- **Background:** `#000000`
- **Text Color:** `#FFFFFF`
- **Font Size:** `16px`
- **Font Weight:** `400`
- **Padding:** `12px 24px`
- **Border Radius:** `9999px`
- **Border:** `0px solid transparent`
- **Min Height:** `44px`
- **Box Shadow:** `none`
- **Hover State:** `background: #1E293B; cursor: pointer;`
- **Active State:** `background: #0F172A; transform: scale(0.98);`

#### Ghost Button (Orange Border)
- **Background:** `rgba(0, 0, 0, 0)`
- **Text Color:** `#FF6500`
- **Font Size:** `16px`
- **Font Weight:** `400`
- **Padding:** `8px 16px`
- **Border Radius:** `9999px`
- **Border:** `2px solid #FF6500`
- **Min Height:** `40px`
- **Box Shadow:** `none`
- **Hover State:** `background: rgba(255, 101, 0, 0.05); border-color: #E55A00;`
- **Active State:** `background: rgba(255, 101, 0, 0.1); border-color: #D45000;`

#### Icon Button (White Border)
- **Background:** `#FFFFFF`
- **Border:** `2px solid #A6A9B7`
- **Border Radius:** `9999px`
- **Width:** `40px`
- **Height:** `40px`
- **Display:** `flex; align-items: center; justify-content: center;`
- **Icon Color:** `#000000`
- **Hover State:** `border-color: #FF6500; background: #F8FAFC;`

#### Icon Button (Orange Border)
- **Background:** `#FFFFFF`
- **Border:** `2px solid #FF6500`
- **Border Radius:** `9999px`
- **Width:** `40px`
- **Height:** `40px`
- **Display:** `flex; align-items: center; justify-content: center;`
- **Icon Color:** `#FF6500`
- **Hover State:** `background: rgba(255, 101, 0, 0.08);`

### Cards & Containers

#### Product Card (White)
- **Background:** `#FFFFFF`
- **Border Radius:** `16px`
- **Padding:** `0px`
- **Border:** `1px solid rgba(0, 0, 0, 0)` (effectively no border)
- **Box Shadow:** `none`
- **Min Height:** `280px`
- **Display:** `flex; flex-direction: column;`
- **Interior Padding:** `16px` for image, `12px` for text content
- **Image Area:** `background: #F8FAFC; border-radius: 16px 16px 0 0; height: 160px;`
- **Text Area:** `padding: 12px 16px 16px; background: #FFFFFF;`

#### Promotional Card (Orange)
- **Background:** `#FF6500`
- **Border Radius:** `16px`
- **Padding:** `40px`
- **Border:** `0px solid transparent`
- **Box Shadow:** `none`
- **Min Height:** `200px`
- **Text Color:** `#FFFFFF`
- **Display:** `flex; flex-direction: column; justify-content: center; align-items: center;`
- **Heading Font Size:** `20px`
- **Heading Weight:** `700`
- **Line Height:** `28px`

#### Badge / Promo Tag (Orange)
- **Background:** `#FF6500`
- **Text Color:** `#FFFFFF`
- **Font Size:** `14px`
- **Font Weight:** `700`
- **Padding:** `8px 16px`
- **Border Radius:** `16px`
- **Display:** `inline-block`

#### Badge / Promo Tag (Black)
- **Background:** `#000000`
- **Text Color:** `#FFFFFF`
- **Font Size:** `14px`
- **Font Weight:** `700`
- **Padding:** `8px 16px`
- **Border Radius:** `16px`
- **Display:** `inline-block`

### Inputs & Forms

#### Text Input
- **Background:** `#FFFFFF`
- **Border:** `1px solid #E2E8F0`
- **Border Radius:** `12px`
- **Padding:** `12px 16px`
- **Font Size:** `14px`
- **Font Weight:** `400`
- **Font Family:** `Proxima Nova`
- **Text Color:** `#000000`
- **Placeholder Color:** `#8C8C8C`
- **Min Height:** `44px`
- **Focus State:** `border-color: #FF6500; box-shadow: 0 0 0 3px rgba(255, 101, 0, 0.1);`
- **Disabled State:** `background: #EEEFF3; border-color: #E2E8F0; color: #8B8E9E; cursor: not-allowed;`

#### Select / Dropdown
- **Background:** `#FFFFFF`
- **Border:** `1px solid #E2E8F0`
- **Border Radius:** `12px`
- **Padding:** `12px 16px`
- **Font Size:** `14px`
- **Text Color:** `#000000`
- **Min Height:** `44px`
- **Focus State:** `border-color: #FF6500;`

#### Checkbox
- **Width:** `20px`
- **Height:** `20px`
- **Border:** `2px solid #E2E8F0`
- **Border Radius:** `4px`
- **Background:** `#FFFFFF`
- **Checked Background:** `#FF6500`
- **Checked Border:** `2px solid #FF6500`
- **Cursor:** `pointer`

#### Radio Button
- **Width:** `20px`
- **Height:** `20px`
- **Border:** `2px solid #E2E8F0`
- **Border Radius:** `50%`
- **Background:** `#FFFFFF`
- **Selected Border:** `2px solid #FF6500`
- **Selected Inner Circle:** `background: #FF6500; width: 12px; height: 12px; border-radius: 50%; margin: 4px;`

### Navigation

#### Header Navigation Bar
- **Background:** `rgba(0, 0, 0, 0)` (transparent)
- **Height:** `80px`
- **Padding:** `0 32px`
- **Display:** `flex; align-items: center; justify-content: space-between;`
- **Box Shadow:** `rgba(50, 50, 71, 0.04) 0px 24px 32px 0px`
- **Position:** `sticky; top: 0; z-index: 100;`

#### Navigation Link (Default)
- **Text Color:** `#000000`
- **Font Size:** `16px`
- **Font Weight:** `400`
- **Padding:** `8px 16px`
- **Border Radius:** `0px`
- **Border:** `0px solid transparent`
- **Cursor:** `pointer`
- **Hover State:** `color: #FF6500; border-bottom: 2px solid #FF6500;`
- **Active State:** `color: #FF6500; border-bottom: 2px solid #FF6500;`

#### Navigation Link (Orange Accent)
- **Text Color:** `#FF6500`
- **Font Size:** `16px`
- **Font Weight:** `400`
- **Padding:** `8px 12px`
- **Border:** `2px solid #FF6500`
- **Border Radius:** `9999px`
- **Background:** `transparent`
- **Hover State:** `background: rgba(255, 101, 0, 0.08);`

#### Breadcrumb
- **Font Size:** `14px`
- **Color:** `#6E7181`
- **Separator:** `/` in `#8B8E9E`
- **Link Color:** `#FF6500`
- **Link Hover:** `color: #E55A00; text-decoration: underline;`

## 5. Layout Principles

### Spacing System

**Base Unit:** `4px`

**Scale:**
- `4px` — Tight gaps between elements, icon spacing
- `8px` — Small padding in buttons, input insets
- `12px` — Standard padding in cards, text blocks
- `16px` — Medium padding, form fields, component internals
- `20px` — Gap between card groups, column spacing
- `28px` — Section spacing, moderate vertical rhythm
- `32px` — Large gap between content blocks, grid column gaps
- `56px` — Major section separation, hero-to-content transitions
- `80px` — Page-level vertical spacing, large whitespace
- `104px` — Maximum spacing for top-level section breaks

**Usage Context:**
- Buttons: `12px 24px` (vertical × horizontal)
- Cards: `16px` internal padding
- Section headers: `80px` above, `28px` below
- Grid gaps: `32px` horizontal, `28px` vertical
- Form groups: `20px` between fields
- Hero sections: `104px` top and bottom padding

### Grid & Container

**Max Width:** `1440px` (primary breakpoint width)

**Container Strategy:**
- Full-width hero sections with `104px` vertical padding
- Centered content container at `1440px` max-width, `32px` horizontal margin
- 2–5 column flexible grids depending on breakpoint
- Leasing product cards: 5 columns at desktop, collapsing to fewer at smaller screens

**Section Patterns:**
- Hero banner (full width, orange background, tall aspect)
- Content section (centered, max-width, uniform side margins)
- Product grid (flexible columns, `32px` gap)
- Testimonial / promotional carousel (hero-style overlay, navigation arrows)

### Whitespace Philosophy

InstaCar follows a **generous whitespace approach** that prevents cognitive overload on a data-heavy product catalog. Large vertical gaps (`56px`–`104px`) separate major sections, allowing users to process information in discrete chunks. Horizontal padding is uniform (`32px` on medium+ screens) for consistent left-edge alignment. Cards maintain breathing room (`12px`–`16px` internal padding) so text and images don't touch borders. The combination of light backgrounds, tall line-height typography, and open spacing creates a premium, uncluttered aesthetic despite the transactional nature of the content.

### Border Radius Scale

- **`0px`** — Straight edges for text links, dividers, form inputs in strict layouts
- **`4px`** — Minimal rounding on checkboxes, small form elements
- **`12px`** — Standard form inputs, select dropdowns, medium containers
- **`16px`** — Product cards, promotional cards, featured containers
- **`9999px`** — Fully rounded buttons, pill-shaped badges, circular icon buttons

## 6. Depth & Elevation

| Level | Treatment | Use |
|-------|-----------|-----|
| **Flat / No Shadow** | `box-shadow: none;` | Primary cards, buttons, most UI elements. Default for modern flat aesthetic. |
| **Subtle Lift** | `box-shadow: rgba(0, 0, 0, 0) 0px 0px 0px 0px, rgba(0, 0, 0, 0) 0px 0px 0px 0px, rgba(0, 0, 0, 0) 0px 0px 0px 0px;` | Card base layer. Minimal visual distinction (effectively no shadow in current extraction). |
| **Navigation Depth** | `box-shadow: rgba(0, 0, 0, 0) 0px 0px 0px 0px, rgba(0, 0, 0, 0) 0px 0px 0px 0px, rgba(50, 50, 71, 0.04) 0px 24px 32px 0px;` | Header/navigation bar. Subtle downward shadow for depth separation from content. |
| **Hover Elevation** | `box-shadow: rgba(0, 0, 0, 0.08) 0px 8px 16px 0px;` | Interactive elements on hover (inferred). Slight shadow to indicate lift. |
| **Modal/Overlay** | `box-shadow: rgba(0, 0, 0, 0.15) 0px 20px 40px 0px;` | Full-screen modals, popovers (inferred). Strong shadow for maximum depth. |

**Shadow Philosophy:**

InstaCar employs **minimal shadow usage** to maintain a modern, flat aesthetic. The system avoids excessive depth effects, relying instead on color contrast, spacing, and borders to define hierarchy. The only substantial shadow occurs in the navigation bar (`rgba(50, 50, 71, 0.04) 0px 24px 32px 0px`), which is deliberately subtle to avoid visual heaviness. Most cards and containers use no shadow, keeping the design lightweight and focused on content. Hover states introduce minimal lift to signal interactivity without dramatic visual shift.

## 7. Do's and Don'ts

### Do

- **Use orange (`#FF6500`) sparingly for highest-priority actions.** Reserve it for primary CTAs, pricing, and promotional highlights to maintain impact.
- **Pair orange with white text** for maximum contrast and readability in buttons and badges.
- **Maintain consistent padding:** `12px` in cards, `16px` in form fields, `32px` in page margins.
- **Employ generous vertical spacing** (`56px`–`104px`) to separate major sections and prevent visual fatigue.
- **Use pill-shaped buttons** (`border-radius: 9999px`) for all interactive elements to reinforce the approachable brand voice.
- **Keep typography weight hierarchy simple:** 700 for headings, 400 for body. Avoid intermediate weights.
- **Apply `16px` border radius to cards** for consistency across product cards and promotional containers.
- **Use borders only for inputs and disabled states;** cards and main containers should rely on background and spacing.
- **Keep line-height at 1.4–1.5× font size** for comfortable reading on light backgrounds.
- **Place promotional badges in orange or black** with white text; reserve these combinations for high-priority callouts only.

### Don't

- **Don't use orange as a background for large text blocks;** it creates eye strain. Reserve orange for buttons, badges, and short promotional copy.
- **Don't mix border radiuses on the same component type;** all product cards should use `16px`, all buttons `9999px`.
- **Don't apply multiple shadows** to a single element; the system uses flat or single-layer shadows only.
- **Don't reduce line-height below `1.25×` the font size;** text will feel cramped and reduce readability.
- **Don't center-align body copy in long blocks;** use left-align for standard readability.
- **Don't use gray text smaller than `14px` on white backgrounds;** contrast ratio falls below WCAG AA.
- **Don't apply letter-spacing to any text;** the design relies on natural Proxima Nova spacing.
- **Don't hide important information in small print** (`12px` caption text) without providing a clear visual hierarchy above it.
- **Don't use color alone to convey status** (success, warning, error); combine with text labels or icons.
- **Don't stretch buttons beyond `max-width: 100%` of their container;** maintain padding discipline even at mobile widths.

## 8. Responsive Behavior

### Breakpoints

| Breakpoint Name | Width | Key Changes |
|-----------------|-------|-------------|
| **Mobile** | `320px` | Single column layout, `16px` side margins, full-width cards, stacked navigation, font size -1px (body: 13px) |
| **Tablet** | `768px` | 2-column grids, `24px` side margins, touch-optimized button heights (`48px`), form fields widen to `100%` |
| **Desktop** | `1024px` | 3–5 column grids, `32px` side margins, standard button heights (`44px`), full navigation menu visible |
| **Large Desktop** | `1440px` | Full-width container cap, maximum grid columns (5), comfortable horizontal spacing, hero sections scale to full viewport |
| **Extra Large** | `1920px` and up | Content max-width enforced (`1440px`), centered with equal side margins, navigation remains fixed-width |

### Touch Targets

- **Minimum tap area:** `44px × 44px` for all interactive elements (buttons, icon buttons, links)
- **Safe spacing:** `8px` minimum gap between adjacent touch targets to prevent accidental activation
- **Form inputs:** Min height `44px` for easy mobile interaction
- **Navigation links:** `8px` vertical padding, `16px` horizontal padding minimum
- **Icon buttons:** `40px × 40px` baseline, `48px × 48px` preferred on mobile
- **Carousel controls:** `48px × 48px` minimum size with `12px` internal padding

### Collapsing Strategy

**Desktop to Tablet (`1440px` → `768px`):**
- Product grid collapses from 5 columns to 2 columns; maintain `32px` gap
- Hero section remains full-width; reduce internal padding from `104px` to `80px`
- Navigation menu becomes hamburger icon; full-width overlay on mobile
- Form fields expand to fill available width; remove multi-column layouts

**Tablet to Mobile (`768px` → `320px`):**
- All grids collapse to single column, full-width cards
- Side margins reduce from `32px` to `16px`
- Spacing scale reduces: `56px` → `40px`, `80px` → `56px`, `104px` → `80px`
- Font size reduces by `1px` for body text (14px → 13px) to maintain line-length control
- Button padding adjusts: `12px 24px` → `12px 16px`
- Cards maintain `16px` border radius; no reduction for smaller screens

**Navigation Collapse:**
- Desktop: Full horizontal menu with logo, links, dropdown language selector, user profile
- Tablet: Primary nav visible, secondary nav in dropdown menu
- Mobile: Hamburger menu with full vertical menu overlay; logo moves to top-left

**Image & Media Scaling:**
- Hero images: `100vw` width, `60vh` height on desktop; `100vw` × `auto` on mobile
- Product images in cards: scale proportionally; maintain aspect ratio
- Promotional badges: maintain readable text; `font-size: 14px` minimum

## 9. Agent Prompt Guide

### Quick Color Reference

- **Primary CTA:** Vibrant Orange (`#FF6500`)
- **Secondary CTA:** Deep Black (`#000000`)
- **Background:** Off-White (`#FFFFFF`)
- **Page Background:** Light Gray (`#E2E8F0`)
- **Heading text:** Deep Black (`#000000`)
- **Body text:** Deep Black (`#000000`)
- **Secondary text:** Muted Gray (`#6E7181`)
- **Disabled text:** Dark Gray (`#8C8C8C`)
- **Borders (inputs):** Light Gray (`#E2E8F0`)
- **Promotional badge bg:** Vibrant Orange (`#FF6500`) or Deep Black (`#000000`)
- **Success state:** Success Green (`#10AB00`)
- **Warning state:** Warning Amber (`#FFAA00`)

### Iteration Guide

1. **All primary action buttons use `#FF6500` background with `#FFFFFF` text, `9999px` border radius, `12px 24px` padding.**

2. **Typography starts with `Proxima Nova` at `14px` for body, `16px` for headings, `32px` for display. Weight is 400 for body, 700 for all headings.**

3. **Card components always use `16px` border radius, `#FFFFFF` background, and no shadow (flat design).**

4. **Page-level spacing uses `80px` or `104px` vertical margins between sections; horizontal margins are `32px` on desktop, reducing to `16px` on mobile.**

5. **Form inputs require `12px` border radius, `1px #E2E8F0` border, `12px 16px` padding, with orange focus state border (`#FF6500`) and subtle blue shadow.**

6. **Navigation bar is transparent background with `80px` height, sticky positioning, and subtle shadow (`rgba(50, 50, 71, 0.04) 0px 24px 32px 0px`).**

7. **Links default to black text; orange (`#FF6500`) only for promotional or secondary links. Underline on hover.**

8. **Responsive breakpoints: mobile 320px, tablet 768px, desktop 1024px, large desktop 1440px. Single-column layouts below 768px.**

9. **Touch targets minimum `44px × 44px`; icon buttons use `40px × 40px` on desktop, `48px × 48px` on mobile.**

10. **Promotional badges are orange or black background with white text, `8px 16px` padding, `16px` border radius. Use sparingly to maintain visual hierarchy.**

11. **Line-height is always generous: `1.5×` for 14px body (20px), `1.4×` for headings. Never reduce below 1.25×.**

12. **Disabled states use light gray background (`#E2E8F0`), muted text (`#8C8C8C`), and `cursor: not-allowed`. Never use color alone to indicate disabled state.**