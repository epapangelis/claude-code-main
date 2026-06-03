# iOS Design System — DESIGN-ios.md

Sourced from Figma JSON tokens: `ios-18-design-tokens.json`

## 1. Visual Theme
A tailored iOS aesthetic adopting native structure but extending the typography and specific color scales to match custom brand attributes.

---

## 2. Color Palette (Exact Codes)

### Neutrals
- **White**: `#ffffffff`
- **Gray 50**: `#f8fafcff`
- **Gray 100**: `#f1f5f9ff`
- **Gray 200**: `#e2e8f0ff`
- **Gray 300**: `#cbd5e1ff`
- **Gray 400**: `#94a3b8ff`
- **Gray 500**: `#64748bff`
- **Gray 600**: `#475569ff`
- **Gray 700**: `#334155ff`
- **Gray 800**: `#1e293bff`
- **Gray 900**: `#04070eff`
- **Black**: `#000000ff`

### Oranges (Primary Brand)
- **Orange 5**: `#fff9f6ff`
- **Orange 10**: `#fff3edff`
- **Orange 50**: `#ffe7d9ff`
- **Orange 100**: `#ffcaa7ff`
- **Orange 200**: `#ffa164ff`
- **Orange 300**: `#ff8636ff`
- **Orange 400**: `#ff6500ff`
- **Orange 500**: `#d45400ff`
- **Orange 600**: `#a94201ff`
- **Orange 700**: `#7e3200ff`
- **Orange 800**: `#542100ff`
- **Orange 900**: `#291000ff`

### Blues
- **Blue 50**: `#eff5ffff`
- **Blue 100**: `#dbe8feff`
- **Blue 200**: `#bfd7feff`
- **Blue 300**: `#93bbfdff`
- **Blue 400**: `#609afaff`
- **Blue 500**: `#3b82f6ff`
- **Blue 600**: `#1d64d8ff`
- **Blue 700**: `#1e55afff`
- **Blue 800**: `#1e478aff`
- **Blue 900**: `#172e54ff`
- **Baby Blue 50**: `#bae6fdff`
- **Baby Blue 400**: `#38bdf8ff`
- **Baby Blue 600**: `#0091d1ff`
- **Baby Blue 900**: `#0c4a6eff`

### Violets
- **Violet 50**: `#ddd6feff`
- **Violet 400**: `#a78bfaff`
- **Violet 600**: `#6b3bf9ff`
- **Violet 900**: `#4c1d95ff`

### Reds (Destructive)
- **Red 5**: `#fff8f8ff`
- **Red 50**: `#ffdedeff`
- **Red 400**: `#f87171ff`
- **Red 600**: `#ff2121ff`
- **Red 900**: `#ba1a1aff`

### Greens (Success)
- **Green 50**: `#d4ffe3ff`
- **Green 400**: `#4ade80ff`
- **Green 600**: `#00b341ff`
- **Green 900**: `#14532dff`

### Yellows (Warning)
- **Yellow 50**: `#fff7baff`
- **Yellow 400**: `#fde047ff`
- **Yellow 600**: `#dfbb00ff`
- **Yellow 900**: `#68380dff`

### UI Semantic Colors
**Fills:**
- **Primary**: `#78788033` (20% opacity)
- **Secondary**: `#78788029` (16% opacity)
- **Tertiary**: `#7878801f` (12% opacity)
- **Quaternary**: `#78788014` (8% opacity)

**Labels:**
- **Primary**: `#04070eff`
- **Secondary**: `#3c3c4399` (60% opacity)
- **Tertiary**: `#3c3c434d` (30% opacity)
- **Quaternary**: `#3c3c432e` (18% opacity)

**Separators:**
- **Opaque**: `#c6c6c8ff`
- **Non-Opaque**: `#54545657` (34% opacity)

---

## 3. Typography
Font family: **Geologica**  
*(Note: Replaces default SF Pro with Geologica for all hierarchy levels)*

### Scale Data (Size / Line Height / Letter Spacing)
- **Large Title**
  - Regular: 34pt / 41pt / 0.4px (Weight: 400)
  - Emphasized: 34pt / 41pt / 0.4px (Weight: 700)
- **Title 1**
  - Regular: 28pt / 34pt / 0.38px (Weight: 400)
  - Emphasized: 28pt / 34pt / 0.38px (Weight: 700)
- **Title 2**
  - Regular: 22pt / 28pt / -0.26px (Weight: 400)
  - Emphasized: 22pt / 28pt / -0.26px (Weight: 700)
- **Title 3**
  - Regular: 20pt / 25pt / -0.45px (Weight: 400)
  - Emphasized: 20pt / 25pt / -0.45px (Weight: 600)
- **Headline**
  - Regular: 17pt / 22pt / -0.43px (Weight: 600)
  - Italic: 17pt / 22pt / -0.43px (Weight: 600, Italic)
- **Body**
  - Regular: 17pt / 22pt / -0.43px (Weight: 400)
  - Emphasized: 17pt / 22pt / -0.43px (Weight: 600)
  - Italic: 17pt / 22pt / -0.43px (Weight: 400, Italic)
  - Emphasized Italic: 17pt / 22pt / -0.43px (Weight: 600, Italic)
- **Callout**
  - Regular: 16pt / 21pt / -0.31px (Weight: 400)
  - Emphasized: 16pt / 21pt / -0.31px (Weight: 600)
- **Subheadline**
  - Regular: 15pt / 20pt / -0.23px (Weight: 400)
  - Emphasized: 15pt / 20pt / -0.23px (Weight: 600)
- **Footnote**
  - Regular: 13pt / 18pt / -0.08px (Weight: 400)
  - Emphasized: 13pt / 18pt / -0.08px (Weight: 600)
- **Caption 1**
  - Regular: 12pt / 16pt / 0px (Weight: 400)
  - Emphasized: 12pt / 16pt / 0px (Weight: 500)
- **Caption 2**
  - Regular: 11pt / 13pt / 0.06px (Weight: 400)
  - Emphasized: 11pt / 13pt / 0.06px (Weight: 600)

---

## 4. Depth & Elevation
Drop Shadows extracted from the token file:

- **Elevation 1**:
  - Shadow 1: Y: 2, Blur: 3, Spread: 1, Color: `#0000000d`
  - Shadow 2: Y: 1, Blur: 1, Spread: 0, Color: `#0000000d`
- **Elevation 2**:
  - Shadow 1: Y: 2, Blur: 6, Spread: 2, Color: `#00000026`
  - Shadow 2: Y: 1, Blur: 2, Spread: 0, Color: `#0000004d`
- **Elevation 3**:
  - Shadow 1: Y: 1, Blur: 3, Spread: 0, Color: `#0000004d`
  - Shadow 2: Y: 4, Blur: 8, Spread: 3, Color: `#00000026`
- **Elevation 4**:
  - Shadow 1: Y: 2, Blur: 3, Spread: 0, Color: `#0000004d`
  - Shadow 2: Y: 6, Blur: 10, Spread: 4, Color: `#00000026`
- **Elevation 5**:
  - Shadow 1: Y: 4, Blur: 4, Spread: 0, Color: `#0000004d`
  - Shadow 2: Y: 8, Blur: 12, Spread: 6, Color: `#00000026`

---

## 5. Agent Prompts
When building iOS UI components using these tokens:
- **Font**: Must use `Geologica` instead of `SF Pro`. Use explicit weights (400, 500, 600, 700) matching the token hierarchy.
- **Colors**: Utilize the exact hex codes over generic native colors. Reference the specific transparency levels for Semantic Fills and Labels.
- **Elevation**: Replicate standard drop shadows using the 5 defined Elevation levels.
