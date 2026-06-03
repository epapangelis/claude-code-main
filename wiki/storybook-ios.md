# iOS 18 Design System Storybook

This document serves as the Storybook-style component reference for the UI derived directly from the Figma design tokens (`ios-18-design-tokens.json`).

## 1. Color Swatches

### Neutrals
- `White`: #ffffffff
- `Gray 50`: #f8fafcff
- `Gray 100`: #f1f5f9ff
- `Gray 200`: #e2e8f0ff
- `Gray 300`: #cbd5e1ff
- `Gray 400`: #94a3b8ff
- `Gray 500`: #64748bff
- `Gray 600`: #475569ff
- `Gray 700`: #334155ff
- `Gray 800`: #1e293bff
- `Gray 900`: #04070eff
- `Black`: #000000ff

### Brand Colors (Oranges, Blues, Violets, Reds, Greens, Yellows)
*Refer to DESIGN-ios.md for the full numeric scale (50-900) across all hues.*

### Semantic Colors
- **Fills**: `Primary` (#787880 @ 20%), `Secondary` (#787880 @ 16%), `Tertiary` (#787880 @ 12%), `Quaternary` (#787880 @ 8%)
- **Labels**: `Primary` (#04070e), `Secondary` (#3c3c43 @ 60%), `Tertiary` (#3c3c43 @ 30%), `Quaternary` (#3c3c43 @ 18%)
- **Separators**: `Opaque` (#c6c6c8), `Non-Opaque` (#545456 @ 34%)

## 2. Typography Variants

All text utilizes the **Geologica** font family. 

- `<LargeTitle variant="Regular" />` - Size: 34, Weight: 400, Line Height: 41
- `<LargeTitle variant="Emphasized" />` - Size: 34, Weight: 700, Line Height: 41
- `<Title1 variant="Regular" />` - Size: 28, Weight: 400, Line Height: 34
- `<Title1 variant="Emphasized" />` - Size: 28, Weight: 700, Line Height: 34
- `<Title2 variant="Regular" />` - Size: 22, Weight: 400, Line Height: 28
- `<Title2 variant="Emphasized" />` - Size: 22, Weight: 700, Line Height: 28
- `<Title3 variant="Regular" />` - Size: 20, Weight: 400, Line Height: 25
- `<Title3 variant="Emphasized" />` - Size: 20, Weight: 600, Line Height: 25
- `<Headline variant="Regular" />` - Size: 17, Weight: 600, Line Height: 22
- `<Headline variant="Italic" />` - Size: 17, Weight: 600, Line Height: 22, Style: italic
- `<Body variant="Regular" />` - Size: 17, Weight: 400, Line Height: 22
- `<Body variant="Emphasized" />` - Size: 17, Weight: 600, Line Height: 22
- `<Callout variant="Regular" />` - Size: 16, Weight: 400, Line Height: 21
- `<Callout variant="Emphasized" />` - Size: 16, Weight: 600, Line Height: 21
- `<Subheadline variant="Regular" />` - Size: 15, Weight: 400, Line Height: 20
- `<Subheadline variant="Emphasized" />` - Size: 15, Weight: 600, Line Height: 20
- `<Footnote variant="Regular" />` - Size: 13, Weight: 400, Line Height: 18
- `<Footnote variant="Emphasized" />` - Size: 13, Weight: 600, Line Height: 18
- `<Caption1 variant="Regular" />` - Size: 12, Weight: 400, Line Height: 16
- `<Caption1 variant="Emphasized" />` - Size: 12, Weight: 500, Line Height: 16
- `<Caption2 variant="Regular" />` - Size: 11, Weight: 400, Line Height: 13
- `<Caption2 variant="Emphasized" />` - Size: 11, Weight: 600, Line Height: 13

## 3. Depth & Elevation Components

- `<Elevation level="1" />`: Minimal lift (Y2 B3 + Y1 B1)
- `<Elevation level="2" />`: Subtle depth (Y2 B6 + Y1 B2)
- `<Elevation level="3" />`: Medium depth (Y4 B8 + Y1 B3)
- `<Elevation level="4" />`: Heavy depth (Y6 B10 + Y2 B3)
- `<Elevation level="5" />`: Extreme depth (Y8 B12 + Y4 B4)

## 4. Derived OS Components (Conceptual)

*(While specific UI geometries like Buttons and Inputs were not explicitly defined in the token output, they derive from the above tokens).*

### Action Components
- `<Button variant="Primary" />`: Uses **Orange 400** (#ff6500ff) fill, **White** text.
- `<Button variant="Secondary" />`: Uses **Fills/Secondary** (#78788029), **Labels/Primary** text.
- `<Button variant="Destructive" />`: Uses **Red 600** (#ff2121ff) fill, **White** text.
- `<Button variant="Success" />`: Uses **Green 600** (#00b341ff) fill, **White** text.

### Feedback & Information
- `<Divider />`: Implemented using **Separators/Opaque** (#c6c6c8ff).
- `<Card />`: Background **White** or **Gray 50**, Drop shadow using `<Elevation level="2" />`.

### Overlays
- `<Modal />`: Uses `<Elevation level="4" />` or `<Elevation level="5" />` with deep dimming effect behind it.
