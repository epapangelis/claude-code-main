# Android Design System — DESIGN-android.md

Sourced from Figma file: INS - Material 3 Design Kit (59RCSAb6exIo7IWlueDcbb)
Last synced: 2026-06-03

---

## 1. Visual Theme

Material Design 3 (M3) by Google. Focuses on expressive geometry, dynamic color extraction (Material You), and adaptable component densities. Interfaces are built with layered states, accessible tonal palettes, and prominent rounded container shapes.

---

## 2. Color Palette

*M3 uses a dynamic, tonal palette system. Colors are generated from a source color (e.g., Orange) and split into tones ranging from 0 (Black) to 100 (White).*

### Core Tones extracted from Figma
```
Oranges (Primary Theme)
Orange 5:    #FFF9F6
Orange 10:   #FFF3ED
Orange 50:   #FFE7D9
Orange 100:  #FFCAA7
Orange 200:  #FFA164
Orange 300:  #FF8636
Orange 400:  #FF6500 (Primary Base)
Orange 500:  #D45400
Orange 600:  #A94201
Orange 700:  #7E3200
Orange 800:  #542100
Orange 900:  #291000

Neutrals (Surfaces and Text)
White:       #FFFFFF
Gray 50:     #F8FAFC
Gray 100:    #F1F5F9
Gray 200:    #E2E8F0
Gray 300:    #CBD5E1
Gray 400:    #94A3B8
Gray 500:    #64748B
Gray 600:    #475569
Gray 700:    #334155
Gray 800:    #1E293B
Gray 900:    #04070E
Black:       #000000
```

### Semantic / Status (M3 standard)
```
Primary:           Main app color (Orange/brand)
On Primary:        Text/icons on top of Primary
Primary Container: Lighter variant of primary
On Primary Cont.:  Text/icons on top of container

Secondary / Tertiary: Used for distinct elements or accents
Error:             Standard red scale for destructive actions
```

---

## 3. Typography

Font family: **Roboto** (or brand custom font mapped to M3 roles).
M3 defines 5 distinct scale groups, each with Large, Medium, and Small variants.

### Scale
```
Display Large / Medium / Small   ← Massive hero numbers or localized headers
Headline Large / Medium / Small  ← Page headers
Title Large / Medium / Small     ← Component headers (cards, dialogs)
Body Large / Medium / Small      ← Main reading text
Label Large / Medium / Small     ← Buttons, chips, UI metadata
```

### Usage rules
- App Bar titles: `Title Large`
- Button text: `Label Large` (all-caps or sentence case depending on brand)
- Body text: `Body Medium` or `Body Large`
- Overlines / Metadata: `Label Small`

---

## 4. Components

### Borders & Radius
M3 highly standardizes shape across the system.
```
Extra Small: 4dp (Snackbars)
Small:       8dp (Chips, Text Fields)
Medium:      12dp (Cards)
Large:       16dp (Navigation Drawers)
Extra Large: 28dp (Large Dialogs, Bottom Sheets)
Full:        Pill shape (Buttons, FABs)
```

### Buttons
```
Filled:     Primary color bg, full radius
Elevated:   Surface color + shadow
Tonal:      Secondary container bg
Outlined:   Transparent bg, outline border
Text:       No bg, no border
FAB:        Floating Action Button (Rounded square or circle)
```

### Inputs / Selects
```
Text Fields: Filled (solid background, bottom line) or Outlined (fully enclosed border).
Chips:       Filter, Input, Suggestion, and Assist variants. Heavy use of 8dp radius.
```

### State Layers
M3 uses standard semi-transparent overlays on top of components to represent states:
- Hover, Focus, Pressed, Dragged.

---

## 5. Layout

### Containers
- **Dialogs**: Highly rounded (28dp), centered, dark scrim.
- **Bottom Sheets**: Swipeable from the bottom, highly rounded top corners.
- **Side Sheets**: Formalized in M3 for supplemental content (sliding from the side).

### Density
- **Compact, Comfortable, Default**: Padding and heights adjust based on the density setting (e.g., lowering a list item height for dense data).

---

## 6. Depth & Elevation

M3 moves away from deep shadows and introduces **Tonal Elevation**.
```
Level 0:  Standard surface (no shadow, base color)
Level 1:  Slight tonal shift (lighter/darker) + very soft shadow
Level 2:  More tonal shift + soft shadow
Level 3:  Used for FABs and Menus
Level 4/5: Used for Dialogs and Bottom Sheets
```

---

## 7. Guidelines

- **Dynamic Color**: Ensure UI components do not hardcode exact hex codes unless it's a fixed brand element. Rely on Tonal Palette references (e.g., `Primary 40` text on `Primary 90` background) for automatic contrast compliance.
- **Ripple Effect**: Ensure all interactive surfaces (Cards, List Items, Buttons) include the standard Material Ripple state layer.
- **Accessibility**: Tap targets must be at least 48x48dp.

---

## 8. Responsive Behavior

Adapt across mobile, foldables, and tablets using standard M3 window size classes. Side Navigation Rails replace bottom bars on wide screens.

---

## 9. Agent Prompts

When building Android/Material 3 UI components:
- Base typography on the standard M3 `Display, Headline, Title, Body, Label` scaling system.
- Map colors to M3 semantic roles (`Primary`, `Primary Container`, `On Primary`, `Surface`, etc.) rather than hard-coded hexes.
- Apply standard M3 shape values (e.g., 28dp for large dialogs, fully rounded pills for standard buttons).
- Instead of using harsh black dropshadows, utilize **Tonal Elevation** (lightening the background color slightly) to indicate depth on surfaces.
