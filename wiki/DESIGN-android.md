# Android Design System — DESIGN-android.md

Sourced from Figma JSON tokens: `material-3-design-tokens.json`

## 1. Visual Theme
Material Design 3 (M3) by Google, adapted with custom brand tokens. Focuses on expressive geometry, adaptable component densities, and a custom typography scale using **Geologica**.

---

## 2. Color Palette (Exact Codes)

### Theming (M3 Semantic Roles)
- **Primary**: `#ff6500ff`
- **On Primary**: `#ffffffff`
- **On Background**: `#ffffffff`
- **Error**: `#ff2121ff`
- **Error Container**: `#fff8f8ff`
- **On Error**: `#ba1a1aff`
- **Surface**: `#ffffffff`
- **On Surface**: `#000000ff`

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

### Brand Scales
- **Oranges (Primary)**: Base (400) is `#ff6500ff`.
- **Blues, Violets, Reds, Greens, Yellows**: Same hex values as iOS foundation.
- **Fills, Labels, Separators**: Core system UI scales mapping to transparency levels (same underlying hex values as iOS).

---

## 3. Typography
Font family: **Geologica**  
*(Note: Replaces default Roboto for all M3 hierarchy levels)*

### Scale Data (Size / Line Height / Letter Spacing)

**Display**
- **Large**: 57pt / 64pt / -0.25px (Regular 400, Emphasized 500)
- **Medium**: 45pt / 52pt / 0px (Regular 400, Emphasized 500)
- **Small**: 36pt / 44pt / 0px (Regular 400, Emphasized 500)

**Headline**
- **Large**: 32pt / 40pt / 0px (Regular 400, Emphasized 500)
- **Medium**: 28pt / 36pt / 0px (Regular 400, Emphasized 500)
- **Small**: 24pt / 32pt / 0px (Regular 400, Emphasized 500)

**Title**
- **Large**: 22pt / 28pt / 0px (Regular 400, Emphasized 500)
- **Medium**: 16pt / 24pt / 0.15px (Regular 500, Emphasized 600)
- **Small**: 14pt / 20pt / 0.1px (Regular 500, Emphasized 600)

**Label**
- **Large**: 14pt / 20pt / 0.1px (Regular 500, Emphasized 600)
- **Medium**: 12pt / 16pt / 0.5px (Regular 500, Emphasized 600)
- **Small**: 11pt / 16pt / 0.5px (Regular 500, Emphasized 600)

**Body**
- **Large**: 16pt / 24pt / 0.5px (Regular 400, Emphasized 500)
- **Medium**: 14pt / 20pt / 0.25px (Regular 400, Emphasized 500)
- **Small**: 12pt / 16pt / 0.4px (Regular 400, Emphasized 500)

---

## 4. Depth & Elevation
Material 3 Drop Shadows extracted from the token file:

- **Elevation 1**: 
  - Light: (Y: 2, Blur: 3, Spread: 1, `#0000000d`) + (Y: 1, Blur: 1, Spread: 0, `#0000000d`)
- **Elevation 2**:
  - Light: (Y: 2, Blur: 6, Spread: 2, `#00000026`) + (Y: 1, Blur: 2, Spread: 0, `#0000004d`)
- **Elevation 3**:
  - Light: (Y: 1, Blur: 3, Spread: 0, `#0000004d`) + (Y: 4, Blur: 8, Spread: 3, `#00000026`)
- **Elevation 4**:
  - Light: (Y: 2, Blur: 3, Spread: 0, `#0000004d`) + (Y: 6, Blur: 10, Spread: 4, `#00000026`)
- **Elevation 5**:
  - Light: (Y: 4, Blur: 4, Spread: 0, `#0000004d`) + (Y: 8, Blur: 12, Spread: 6, `#00000026`)

*(Note: Dark mode elevations alter opacity and spread slightly but share the same base structure).*

---

## 5. Agent Prompts
When building Android/Material 3 UI components using these tokens:
- **Typography**: Base typography strictly on the `Display`, `Headline`, `Title`, `Body`, and `Label` scales. Use `Geologica` font with exact weights mapped to Regular vs. Emphasized values.
- **Colors**: Map colors to M3 semantic roles (`Primary`, `Surface`, `On Surface`) utilizing the provided exact hex codes.
- **Elevation**: Utilize the specific 5-level drop shadow metrics extracted above.
