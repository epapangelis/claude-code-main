# instacar-component-library

**Summary**: Provides detailed CSS component specifications for all core UI elements in the InstaCar design system, including dimensions, states, and interactions to ensure a cohesive and scalable front-end experience.
**Context**: [instacar] or [concepts]
**Sources**: instacar.gr-DESIGN.md
**Last updated**: 2026-06-19

***

## Component Anatomy & Specifications
All components are designed for modularity, maintaining a flat aesthetic, and leveraging the core color palette (See [[instacar-color-palette]] and [[instacar-typography]]).

### 👇 Buttons (The primary actionable element)
Buttons must adopt the pill-shape (`border-radius: 9999px`) to maintain approaching brand affinity. The minimal height is mandatory for touch targets of at least `44px`.

#### Primary Button (Orange Action)
*   **Background:** `#FF6500` (Vibrant Orange).
*   **Text Color:** `#FFFFFF`.
*   **Dimensions:** `12px` vertical padding, `24px` horizontal padding. Minimum height `44px`.
*   **Interaction States:** The hover state must provide a slight gradient shift (`background: #E55A00;`). The active state should compress slightly for tactile feedback (source: instacar.gr-DESIGN.md).

#### Secondary Button (Black Action)
*   **Background:** `#000000` (Deep Black).
*   **Text Color:** `#FFFFFF`.
*   **Dimensions:** Identical to Primary button padding/min height. Used for secondary, but equally important actions.

#### Ghost & Bordered Buttons
These allow contrast using outlines:
1.  **Ghost Button (Orange Outline):** Background `rgba(0, 0, 0, 0)`. Utilize the primary orange border (`2px solid #FF6500`). Used when the action is important but not the *most* critical CTA.
2.  **Icon Buttons:** Use a consistent size of `40px x 40px` on desktop (minimum). Icon color should match the state/theme, and the hover background must use subtle opacity to signal interactivity.

### 🖼️ Cards & Containers
Cards define product information and promotional content. They enforce visual segmentation from the page background using white space and light borders.

#### Product Card (The standard display unit)
*   **Structure:** Multi-part component with a defined internal padding (`16px` on text side, `12px` image side).
*   **Shape:** Mandatory `border-radius: 16px`.
*   **Style:** Must be flat, using no box shadow. The border itself is minimal or absent to blend seamlessly into content grids.

#### Promotional Card (Highlight/Hero)
*   **Use Case:** High impact "Sale" or feature promotion. Requires full-bleed width and often uses the primary orange background (`#FF6500`) with white text, prioritizing headline visibility (source: instacar.gr-DESIGN.md).
*   **Impact:** Overrides standard card styling for maximum visual draw.

### ✍️ Inputs & Forms
Inputs must feel native and accessible while carrying the brand accent.

#### Text Input / Dropdown
*   **Default Border:** `1px solid #E2E8F0` (Light Gray).
*   **Focus State:** Critical interaction point. Must visibly change to the primary orange (`border-color: #FF6500;`) and introduce a minimal, subtle complementary shadow for focus indication (source: instacar.gr-DESIGN.md).

### 🗺️ Navigation Structure
All navigation elements must adhere to functional rules that enhance discoverability and speed:

*   **Header Bar:** Must be fixed (`sticky`) with height `80px` and a very subtle box shadow (to signal depth separation from content) (source: instacar.gr-DESIGN.md).
*   **Links:** Standard links default to black; promotional or emphasized links should adopt the `#FF6500` color, visually underlined on hover. The breadcrumb separator should use `/#8B8E9E/`.

***

### ⚙️ Global Layout & Principles
*   **Spacing Scale (Base Unit: 4px):** Use predefined gaps (`12px`, `16px`, `32px` for margins, etc.) to avoid arbitrary spacing. These provide a consistent 'rhythm' that guides the user through complex data.
*   **Grid:** Content should be centered within a single maximum width container (recommended at `1440px`). Side margins are key differentiators across breakpoints (**32px** default, reducing to **$16 \text{px}$ on mobile**) (source: instacar.gr-DESIGN.md).
*   **Whitespace Philosophy:** Embrace the void. Use generous vertical spacing (`56px` to `104px`) between major components/sections to prevent cognitive overload in a data-dense environment (source: instacar.gr-DESIGN.md).