# iOS Design System — DESIGN-ios.md

Sourced from Figma file: INS - iOS 18 and iPadOS 18 (hR1EnHgz1LvBwQJyq4mGMF)
Last synced: 2026-06-03

---

## 1. Visual Theme

Native Apple ecosystem aesthetics optimized for iOS 18 and iPadOS 18. Emphasizes depth, translucency, and large, legible typography. Interfaces adapt gracefully across Light, Dark, and the new Tinted display modes.

---

## 2. Color Palette

*Values below represent conceptual system-level colors from Apple's HIG and the Figma extraction. Specific Hex codes vary based on Light/Dark/Tinted environments; the system relies heavily on semantic color mapping and material blurs.*

### Primary Brands / System Colors
```
Blue 500:   #3B82F6 (System Blue) ← Interactive elements, default links
Orange 400: #FF6500 (System Orange)
Green 600:  #00B341 (System Green) ← Success states, active toggles
```

### Grays & Neutrals
```
White:      #FFFFFF
Black:      #000000
Gray 400:   #94A3B8 (System Gray 4)
Gray 900:   #04070E (System Gray 6)
```

### Semantic / Labels & Fills
```
Labels/Primary:        #04070E (Standard text color)
Labels/Secondary:      #3C3C43 with 60% opacity (Subtitles, secondary information)
Labels/Tertiary:       #3C3C43 with 30% opacity (Placeholder text, disabled text)
Labels/Quaternary:     #3C3C43 with 18% opacity (Subtle text elements)

Fills/Primary:         #787880 with 20% opacity (Solid interactive elements)
Fills/Secondary:       #787880 with 16% opacity (Secondary buttons, list backgrounds)
Fills/Tertiary:        #787880 with 12% opacity (Search fields, segmented controls)

Separators/Opaque:     #C6C6C8 (Hard dividers)
Separators/Non-opaque: #545456 with 34% opacity (Subtle dividers using alpha channels)
```

---

## 3. Typography

Font family: **San Francisco (SF Pro)**
Uses Dynamic Type sizes that scale automatically based on user accessibility settings.

### Scale (Default "Large" sizes)
```
Large Title:   Emphasized
Title 1:       Emphasized
Title 2:       Regular
Title 3:       Regular / Emphasized

Headline:      Regular
Subheadline:   Regular / Emphasized

Body:          Regular / Emphasized   ← Main reading text

Callout:       Regular
Footnote:      Regular / Emphasized

Caption 1:     Regular
Caption 2:     Regular
```

### Usage rules
- Body copy: Use `Body/Regular` for all standard readable text.
- Large Headers: Use `Large Title` for main view headers.
- Buttons: Typically use `Headline` or `Body/Emphasized`.
- Metadata: Use `Footnote` or `Caption 1` for timestamps and secondary data.

---

## 4. Components

### Borders & Radius
Apple uses continuous curves (superellipses) rather than standard rounded corners.
```
Default Corner Radius: Varies continuously, standard is ~10-14pt for cards/modals.
Border width: Standard 0.33pt or 0.5pt for separators.
```

### Buttons
```
Primary:   Filled button (Tint color bg, White text), rounded corners
Secondary: Tonal or Gray filled button
Text Only: Tint color text with no background
```

### Inputs / Selects
```
Search Fields: Fills/Tertiary background with corner radius. Magnifying glass icon in tertiary label color.
Pickers:       Native scrolling wheels or inline date/time spinners.
```

### Navigation
```
Navigation Bars: Translucent background with a hair-line border. Titles scale down on scroll.
Tab Bars:        Translucent background at the bottom. Active icon is tinted.
```

---

## 5. Layout

### Sheets & Modals
- **Standard Sheets**: Partially cover the screen, allowing users to pull down to dismiss.
- **Action Sheets**: Slide up from the bottom for destructive/secondary actions.
- **Popover**: Used extensively on iPad for contextual menus attached to buttons.

### Margins
- Standard layout margins: 16pt or 20pt depending on device size.

---

## 6. Depth & Elevation

Depth is created primarily using **Materials (Blurs)** rather than drop shadows.
```
Thick Material:  Used for prominent overlays (Keyboards, Action Sheets).
Regular Material: Used for Navigation Bars, Tab Bars.
Thin Material:   Subtle overlays.
Shadows:         Soft, diffused shadows are used sparingly, mostly on floating elements (Widgets, Context Menus).
```

---

## 7. Guidelines

- **Tinted Icons (iOS 18)**: Ensure app icons have an alpha-channel "stencil" version to support user-applied monochromatic tints.
- **Control Center APIs**: Support 1x1, 2x1, or 2x2 widget actions for quick tasks.
- **Translucency**: Always use standard iOS materials rather than opaque gray backgrounds for toolbars and overlays so content can bleed through.
- **Hit Targets**: Minimum interactive area must be 44x44pt.

---

## 8. Responsive Behavior

Must adapt to various iPhone aspect ratios, Dynamic Island cutouts, and scale significantly for iPadOS 18 (utilizing floating tab bars and sidebars).

---

## 9. Agent Prompts

When building iOS UI components:
- Utilize `SF Pro` and Dynamic Type scaling exclusively.
- Replace hex values with semantic iOS UI colors (e.g., `systemBlue`, `label`, `secondarySystemBackground`).
- Implement safe area layout guides to avoid overlapping the Dynamic Island or Home Indicator.
- Favor Materials (background blurs) over standard shadows to create depth.
