# iOS 18 Design System

**Summary**: System-level specs for iOS 18 and iPadOS 18, focusing on home screen personalization, Control Center extensibility, and Apple Intelligence integration.
**Context**: [concepts]
**Sources**: INS - iOS 18 and iPadOS 18 Figma
**Last updated**: 2026-05-25

***

## Core Updates

### Home Screen & Icon Customization
iOS 18 introduces **Dark** and **Tinted** modes for app icons. 
- **Tinted Mode**: The OS strips color from the icon and applies a monochromatic filter chosen by the user.
- **Requirement**: Designers must provide a secondary "stencil" asset (alpha-only) to ensure the brand mark remains visible and balanced under system filters.

### Control Center API
Control Center is now extensible. Third-party apps can contribute controls (toggles, buttons, or sliders).
- **instacar Opportunity**: We should expose "Quick Actions" for active subscriptions (e.g., Lock/Unlock, Climate Start, Range Check) as Control Center widgets.
- **Design**: Controls use a 1x1, 2x1, or 2x2 grid system within the new paginated Control Center.

### Apple Intelligence
New visual language for AI-driven features:
- **The Glow**: A shimmering edge animation (Luminaire) around the screen when Siri is active.
- **Writing Tools**: Standardized UI for proofreading and rewriting text.

### SF Symbols 6
The latest version of Apple's iconography system adds new animation presets:
- **Wiggle, Breathe, and Pulse**: Useful for active states.
- **Replace**: Smoother transitions when one icon changes to another (e.g., Lock to Unlock).

## iPadOS 18 Specifics
- **Floating Tab Bar**: The sidebar can now transform into a floating top tab bar, providing more horizontal real estate for content.
- **Refined Animations**: Enhanced document-opening animations and hover states for Apple Pencil Pro.

## Related pages
- [[design-system]]
- [[building-mobile-apps-at-scale]]
- [[ios-18-design-system]]