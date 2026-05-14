# Instafleet Design System — DESIGN.md

Sourced from Figma file: Instafleet DS (DzJ17Kk2eyyTBGndp4qrAx)
Last synced: 2026-04-23

---

## 1. Visual Theme

Clean, data-dense internal tooling for CS and Sales agents. Light backgrounds with strong typographic hierarchy. No decorative elements — every visual decision must serve legibility or task completion. Functional and trustworthy, not flashy.

---

## 2. Color Palette

### Primary Blue (Tailwind Blue / Slate hybrid)
```
Blue 100:  #DBEAFE
Blue 200:  #BFDBFE   ← border-info
Blue 300:  #93C5FD
Blue 400:  #60A5FA
Blue 500:  #3B82F6   ← primary blue (brand)
Blue 600:  #2563EB   ← text-info, interactive elements, CTA
Blue 700:  #1554DC
Blue 800:  #1E3A8A
Blue 900:  #0D1F53
```

### Grays (Slate scale)
```
Gray 100:  #F1F5F9   ← background-secondary
Gray 200:  #E2E8F0   ← border-primary, border-tertiary
Gray 300:  #CBD5E1   ← border-secondary
Gray 400:  #94A3B8   ← placeholder text
Gray 500:  #64748B   ← text-secondary
Gray 600:  #475569
Gray 700:  #334155
Gray 800:  #1E293B
Gray 900:  #0F172A   ← text-primary
```

### Backgrounds
```
White:         #FFFFFF  ← background-primary
Lightest Gray: #F8FAFC  ← background-secondary (panels, rows)
Lightest Blue: #EFF6FF  ← background-info (info states, highlighted sections)
```

### Semantic / Status
```
Success text:   #166534
Success bg:     #F0FDF4
Success border: #BBF7D0
Success accent: #22C55E  ← active dot, checkmarks

Warning text:   #B45309
Warning bg:     #FFFBEB
Warning border: #FDE68A

Danger text:    #DC2626
Danger bg:      #FEF2F2
Danger border:  #FECACA

Info text:      #2563EB  ← Blue 600
Info bg:        #EFF6FF  ← Lightest Blue
Info border:    #BFDBFE  ← Blue 200
```

### Color Coding (badge/chip use only)
Green 400: #4ADE80 / Green 900: #14532D
Red 200: #FECACA / Red 900: #7F1D1D

---

## 3. Typography

Font family: **Geologica** (Google Fonts)
Import: `https://fonts.googleapis.com/css2?family=Geologica:wght@400;500;600&display=swap`

### Scale
```
B 10: Geologica 600  10px / 12.5px
M 12: Geologica 400  12px / 15px
B 12: Geologica 600  12px / 15px
M 14: Geologica 400  14px / 17.5px   ← body default
SM 14: Geologica 500 14px / 17.5px   ← medium emphasis
B 14: Geologica 600  14px / 17.5px   ← labels, field values
M 16: Geologica 400  16px / 20px
B 16: Geologica 600  16px / 20px     ← section titles
M 18: Geologica 400  18px / 22.5px
B 18: Geologica 600  18px / 22.5px
M 20: Geologica 400  20px / 25px
B 20: Geologica 600  20px / 25px     ← modal titles
```

### Usage rules
- Labels: B 12 uppercase, letter-spacing 0.5px, Gray 500
- Body copy: M 14, Gray 900
- Field values: SM 14 or B 14, Gray 900
- Secondary info: M 12, Gray 500
- Section headers: B 14 uppercase, letter-spacing 0.5px
- Modal title: B 16, Gray 900

---

## 4. Components

### Borders & Radius
```
--border-radius-sm:  4px   ← chips, small badges
--border-radius-md:  6px   ← inputs, buttons, small cards
--border-radius-lg:  10px  ← cards, panels
--border-radius-xl:  12px  ← modals, overlays

Border width: 0.5px (default) or 1px (focused/active)
```

### Buttons
```
Primary:   bg Blue 600, white text, radius-md, 8px 16px padding
Secondary: bg White, Gray 500 text, border Gray 300, radius-md
Disabled:  bg Gray 200, Gray 400 text, cursor not-allowed
```

### Inputs / Selects
```
Border: 0.5px Gray 300
Border-radius: radius-md
Padding: 8px 12px
Font: M 14
Focus ring: 0 0 0 3px rgba(37,99,235,0.12), border Blue 600
```

### Chips / Badges
```
Pill: border-radius 100px, 10px font, 600 weight, 2px 7px padding
Status-active:   bg #DCFCE7, text #166534
Status-warning:  bg #FFFBEB, text #B45309
Status-info:     bg #EFF6FF, text #2563EB
Status-neutral:  bg Gray 100, text Gray 500, border Gray 200
```

### Cards
```
Background: White
Border: 0.5px Gray 200
Border-radius: radius-lg
Shadow: 0 1px 3px rgba(0,0,0,0.06), 0 4px 12px rgba(0,0,0,0.04)
Padding: 14px–20px depending on density
```

---

## 5. Layout

### Modals
Full-screen overlay for complex workflows (e.g. car swap).
- Max-width: 1200px, centered
- Two-panel grid: `grid-template-columns: 1fr 1px 1fr`
- Left panel: read-only context (Gray 100 background)
- Right panel: agent action (White background)
- Header + Footer: fixed, White background, border Gray 200

### Spacing scale
4px · 6px · 8px · 10px · 12px · 14px · 16px · 20px · 24px · 32px

---

## 6. Depth & Elevation

```
Level 0 (flat):    no shadow, border only
Level 1 (card):    0 1px 3px rgba(0,0,0,.06), 0 4px 12px rgba(0,0,0,.04)
Level 2 (modal):   0 8px 32px rgba(0,0,0,.12)
Level 3 (tooltip): 0 4px 16px rgba(0,0,0,.16)
```

Modals sit on a `rgba(0,0,0,0.4)` backdrop.

---

## 7. Guidelines

- Never use more than 2 blue tones in the same component.
- Gray 500 for all secondary text. Never use Gray 400 for text (too low contrast).
- Status colors are semantic — green = active/success, amber = pending/agent-action, red = error/danger, blue = info/suggested.
- Inline actions (transfer, clear, expand) should be visible on hover, not always-on.
- Dense data tables: 0.5px borders, no cell padding above 10px vertical.
- All monetary values: right-aligned, monospace-ish weight (B 14 or SM 14).

---

## 8. Responsive Behavior

These mockups target a 1280px+ desktop internal tool. No mobile breakpoints required for instafleet agent views.

---

## 9. Agent Prompts

When building instafleet UI components:
- Always import Geologica from Google Fonts
- Use the `:root` CSS variables defined below — never hardcode hex values directly
- Background panels (read-only context): Gray 100 (#F8FAFC)
- Interactive panels (agent edits): White (#FFFFFF)
- Primary action buttons: Blue 600 (#2563EB)
- Section label pattern: B 12, uppercase, letter-spacing 0.5px, Gray 500
- Clickable rows must have hover background: Gray 100 (#F1F5F9)
- Transfer/carry-over interactions: highlight with Blue 100 (#DBEAFE) background + Blue 600 left border (3px)

### CSS root variables to always include
```css
:root {
  --font-sans: 'Geologica', -apple-system, BlinkMacSystemFont, sans-serif;
  --color-text-primary: #0F172A;
  --color-text-secondary: #64748B;
  --color-text-info: #2563EB;
  --color-text-danger: #DC2626;
  --color-text-warning: #B45309;
  --color-text-success: #166534;
  --color-background-primary: #FFFFFF;
  --color-background-secondary: #F8FAFC;
  --color-background-info: #EFF6FF;
  --color-background-warning: #FFFBEB;
  --color-background-success: #F0FDF4;
  --color-background-danger: #FEF2F2;
  --color-border-primary: #E2E8F0;
  --color-border-secondary: #CBD5E1;
  --color-border-tertiary: #E2E8F0;
  --color-border-info: #BFDBFE;
  --color-border-warning: #FDE68A;
  --color-border-danger: #FECACA;
  --color-blue-500: #3B82F6;
  --color-blue-600: #2563EB;
  --color-blue-100: #DBEAFE;
  --border-radius-sm: 4px;
  --border-radius-md: 6px;
  --border-radius-lg: 10px;
  --border-radius-xl: 12px;
}
```
