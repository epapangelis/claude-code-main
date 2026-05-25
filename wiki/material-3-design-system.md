# Material 3 Design System

**Summary**: Google's Material You (M3) standards, focusing on dynamic color tonal palettes, expressive motion, and refined component density for data-heavy interfaces.
**Context**: [concepts]
**Sources**: INS - Material 3 Design Kit Figma
**Last updated**: 2026-05-25

***

## Key Principles

### Dynamic Color & Tonal Palettes
M3 uses a color system derived from the user's wallpaper.
- **Tonal Palettes**: Instead of a single primary color, M3 generates a palette of 13 tones (0-100 luminosity).
- **Accessibility**: Contrast is guaranteed by selecting specific tones (e.g., Tone 40 for text on Tone 90 background) rather than specific hex codes.

### Component Density
M3 provides three density levels: **Default**, **Comfortable**, and **Compact**.
- **Compact Density**: Reduces the height of components (buttons, list items, text fields). This is the recommended standard for **instafleet** to maximize information density on agent dashboards.

### State Layers
Standardized semi-transparent overlays (Hover, Focus, Pressed, Dragged) that sit on top of the container color. This ensures interactive feedback is consistent across all components regardless of their underlying color.

## Component Updates

### Navigation
- **Navigation Bar**: For mobile (bottom).
- **Navigation Rail**: For tablets/foldables (side).
- **Navigation Drawer**: For deep navigation hierarchies.

### Side Sheets
M3 formalizes Side Sheets as a standard container for supplemental content. These can be "Standard" (persists with content) or "Modal" (interrupts workflow). This aligns with our **Unified View** email panel design.

## Related pages
- [[design-system]]
- [[atomic-design]]
- [[unified-view]]