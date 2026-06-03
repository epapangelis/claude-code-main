# Material 3 Design System Storybook

This document serves as the Storybook-style component reference for the Android/Material 3 UI derived directly from the Figma design tokens (`material-3-design-tokens.json`).

## 1. Color Swatches

### Theming (M3 Roles)
- `Primary`: #ff6500ff
- `On Primary`: #ffffffff
- `On Background`: #ffffffff
- `Error`: #ff2121ff
- `Error Container`: #fff8f8ff
- `On Error`: #ba1a1aff
- `Surface`: #ffffffff
- `On Surface`: #000000ff

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

*(Other brand palettes like Oranges, Blues, Violets match the shared cross-platform palette).*

## 2. Typography Variants

All text utilizes the **Geologica** font family, conforming to M3 Type Scale logic.

### Display
- `<Display variant="Large" />` - Size: 57, Line Height: 64, Weight: 400
- `<Display variant="LargeEmphasized" />` - Size: 57, Line Height: 64, Weight: 500
- `<Display variant="Medium" />` - Size: 45, Line Height: 52, Weight: 400
- `<Display variant="MediumEmphasized" />` - Size: 45, Line Height: 52, Weight: 500
- `<Display variant="Small" />` - Size: 36, Line Height: 44, Weight: 400
- `<Display variant="SmallEmphasized" />` - Size: 36, Line Height: 44, Weight: 500

### Headline
- `<Headline variant="Large" />` - Size: 32, Line Height: 40, Weight: 400
- `<Headline variant="LargeEmphasized" />` - Size: 32, Line Height: 40, Weight: 500
- `<Headline variant="Medium" />` - Size: 28, Line Height: 36, Weight: 400
- `<Headline variant="MediumEmphasized" />` - Size: 28, Line Height: 36, Weight: 500
- `<Headline variant="Small" />` - Size: 24, Line Height: 32, Weight: 400
- `<Headline variant="SmallEmphasized" />` - Size: 24, Line Height: 32, Weight: 500

### Title
- `<Title variant="Large" />` - Size: 22, Line Height: 28, Weight: 400
- `<Title variant="LargeEmphasized" />` - Size: 22, Line Height: 28, Weight: 500
- `<Title variant="Medium" />` - Size: 16, Line Height: 24, Weight: 500
- `<Title variant="MediumEmphasized" />` - Size: 16, Line Height: 24, Weight: 600
- `<Title variant="Small" />` - Size: 14, Line Height: 20, Weight: 500
- `<Title variant="SmallEmphasized" />` - Size: 14, Line Height: 20, Weight: 600

### Label
- `<Label variant="Large" />` - Size: 14, Line Height: 20, Weight: 500
- `<Label variant="LargeEmphasized" />` - Size: 14, Line Height: 20, Weight: 600
- `<Label variant="Medium" />` - Size: 12, Line Height: 16, Weight: 500
- `<Label variant="MediumEmphasized" />` - Size: 12, Line Height: 16, Weight: 600
- `<Label variant="Small" />` - Size: 11, Line Height: 16, Weight: 500
- `<Label variant="SmallEmphasized" />` - Size: 11, Line Height: 16, Weight: 600

### Body
- `<Body variant="Large" />` - Size: 16, Line Height: 24, Weight: 400
- `<Body variant="LargeEmphasized" />` - Size: 16, Line Height: 24, Weight: 500
- `<Body variant="Medium" />` - Size: 14, Line Height: 20, Weight: 400
- `<Body variant="MediumEmphasized" />` - Size: 14, Line Height: 20, Weight: 500
- `<Body variant="Small" />` - Size: 12, Line Height: 16, Weight: 400
- `<Body variant="SmallEmphasized" />` - Size: 12, Line Height: 16, Weight: 500

## 3. Depth & Elevation Components

Standard M3 Elevations:
- `<Elevation level="1" />`: Modest shadow depth.
- `<Elevation level="2" />`: Typical component depth.
- `<Elevation level="3" />`: Floating Action Buttons.
- `<Elevation level="4" />`: Prominent modaling.
- `<Elevation level="5" />`: Deeply stacked sheets/dialogs.

## 4. Derived M3 Components (Conceptual)

*(While specific UI geometries like Buttons and Inputs were not explicitly defined in the token output, they derive from the M3 foundation and these tokens).*

### Actions & Controls
- `<Button variant="Filled" />`: Uses **Primary** (#ff6500) fill, **On Primary** (#ffffff) text. Fully rounded corners.
- `<Button variant="Outlined" />`: Transparent fill, **Primary** outline and text.
- `<Button variant="Text" />`: Transparent fill, no outline, **Primary** text.
- `<FAB />`: Floating Action Button, `<Elevation level="3" />`, uses **Primary Container** colors.

### Layout & Containers
- `<Card />`: Background mapped to **Surface**, Drop shadow using `<Elevation level="1" />` or `<Elevation level="2" />`.
- `<BottomBar />`: Maps to **Surface** with `Elevation` and appropriate M3 padding grids.
- `<Dialog />`: Large radius (e.g., 28dp), **Surface** background, `<Elevation level="5" />`.
