# instacar-color-palette

**Summary**: Defines the functional roles, hex codes, and usage context of all colors within the InstaCar design system, ensuring visual consistency across promotional, standard, and disabled states.
**Context**: [instacar] or [concepts]
**Sources**: instacar.gr-DESIGN.md
**Last updated**: 2026-06-19

***

## Palette Roles & Definitions
The InstaCar palette is built on a high contrast axis, leveraging vibrant orange (`#FF6500`) to convey primary action and energy against neutral backgrounds (source: instacar.gr-DESIGN.md).

### 🎨 Primary Colors (Action & Brand)
*   **Vibrant Orange** (`#FF6500`): The main brand color. Used for all Call-to-Action buttons, pricing emphasis, navigational accents, and key promotional highlights. *Usage:* Primary buttons, active states, badges.
*   **Deep Black** (`#000000`): Provides maximum contrast for body copy and primary text content where high readability is critical. Used alongside white backgrounds for core content blocks.

### 🌈 Accent Colors (Secondary Emphasis)
These colors are used sparingly to provide targeted visual distinction without competing with the primary CTA.
*   **Bold Blue** (`#007AFF`): Reserved for secondary interactive highlights, informational sections, or delivery promotions. Limited usage is key (source: instacar.gr-DESIGN.md).
*   **Vivid Purple** (`#552CFF`): Tertiary accent for unique features or special high-impact campaigns, ensuring maximum visual differentiation when necessary.

### 🌫️ Neutral/Grayscale Scale (Clarity & Separation)
The neutral scale is crucial for providing a clean canvas and subtle structural separation without distraction. Colors are selected to prevent low contrast ratios in body copy.
| Color Name | Hex Code | Role / Usage Context | Notes |
| :--- | :---: | :--- | :--- |
| **Off-White** | `#FFFFFF` | Primary card/container background, clean content areas. | Maximum contrast base layer. |
| **Light Gray** | `#E2E8F0` | Default element borders (inputs, dividers), disabled states for non-critical elements. | Standard structural divider. |
| **Lighter Gray** | `#F8FAFC` | Very subtle background variation, reserved for low-emphasis backgrounds like image containers. | Minimal usage area lift. |
| **Medium Gray** | `#EEEFF3` | Subtle secondary surfaces or slightly muted content blocks. | Used sparingly to avoid general gray noise. |
| **Dark Gray** | `#8C8C8C` | Placeholder text, utility copy, subtle metadata, disabled form fields. | Must not be used for primary body text (WCAG violation risk). |
| **Charcoal** | `#475569` | Secondary text/captions that need to stand apart from the main content flow without being black. | Ideal for support information. |
| **Slate Gray** | `#1E293B` | Tertiary labels and auxiliary data that require a slight separation from body copy or captions.| Used for highly contextual, non-essential text elements. |
| **Muted Gray** | `#6E7181` | General supporting context, generic labels, utility tooltips. | High usage color (51 times) for low-attention content areas. |

### ✅ Semantic Status Indicators
These colors must be used strictly to convey status, not mere decoration.
*   **Success Green** (`#10AB00`): Used only for confirmed success states and positive completions.
*   **Warning Amber** (`#FFAA00`): Reserved for non-critical alerts or required attention flags (caution).

***

### 💡 Design Rules Enforcement
*   **Contrast:** All primary text must be readable against the background. *Rule of Thumb:* Never use a gray tone smaller than `14px` on pure white backgrounds without careful consideration (source: instacar.gr-DESIGN.md).
*   **Primary CTA Pairing:** The `#FF6500` brand color always pairs with `--FFFFFF` text for optimal contrast and impact in buttons/badges.