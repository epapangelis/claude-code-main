# Instafleet Design System

**Summary**: Design tokens for the Instafleet product — colors, typography, shadows, buttons, and UI components extracted from the Figma Design System file.

**Sources**: Figma — Instafleet-DS (node: Building Blocks, 17552:96705 · node: Buttons, 17552:97516 · node: Buttons updated, 18029:198997 · node: Navigation, 17552:107061 · node: Fields, 17963:136184 · node: Lists, 18622:94375 · node: Email, 18477:133094 · node: InfoBar, 18622:94374 · node: History, 18622:106747 · node: Cards, 18929:154855)

**Last updated**: 2026-04-29

---

## Logo

Three variants of the Instafleet logo (200 × 42px each):

| Variant | Usage |
|---|---|
| **White Bg** | On light/white backgrounds |
| **Black Bg** | On dark/black backgrounds |
| **Colour BG** | On the brand blue background |

---

## Colors

### BG (Backgrounds)

| Token | Hex | Notes |
|---|---|---|
| `BG/White` | `#FFFFFF` | Default white background |
| `BG/Light` | `#FFFFFF` | Light background (alias of White) |
| `BG/Lightest Blue` | `#EFF6FF` | Subtle blue-tinted background |
| `BG/Lightest Gray` | `#F8FAFC` | Subtle gray-tinted background |

---

### Primary (Brand Blue)

| Token | Hex |
|---|---|
| `Primary/Blue 100` | `#DBEAFE` |
| `Primary/Blue 200` | `#BFDBFE` |
| `Primary/Blue 300` | `#93C5FD` |
| `Primary/Blue 400` | `#60A5FA` |
| `Primary/Blue 500` | `#3B82F6` ← **Brand blue** |
| `Primary/Blue 600` | `#2563EB` |
| `Primary/Blue 700` | `#1654DD` |
| `Primary/Blue 800` | `#1E3A8A` |
| `Primary/Blue 900` | `#0D1F54` |

> `primary/dark 1` = `#242731` (dark UI surface, e.g. dark sidebar or overlay)

---

### Grays

| Token | Hex |
|---|---|
| `Grays/Gray 100` | `#F1F5F9` |
| `Grays/Gray 200` | `#E2E8F0` |
| `Grays/Gray 300` | `#CBD5E1` |
| `Grays/Gray 400` | `#94A3B8` |
| `Grays/Gray 500` | `#64748B` |
| `Grays/Gray 600` | `#475569` |
| `Grays/Gray 700` | `#334155` |
| `Grays/Gray 800` | `#1E293B` |
| `Grays/Gray 900` | `#0F172A` |

---

### Color Coding

Used for labels, tags, badges, and status indicators. Each family has 4 shades: 200 (lightest / bg), 400 (mid), 600 (strong / default), 900 (darkest / text).

| Family | 200 | 400 | 600 | 900 |
|---|---|---|---|---|
| **Pink** | `#FBCFE8` | `#F472B6` | `#F3208F` | `#831843` |
| **Fukshia** | `#F5D0FE` | `#E879F9` | `#D31BEF` | `#701A75` |
| **Violet** | `#DDD6FE` | `#A78BFA` | `#6B3BF9` | `#4C1D95` |
| **Purple** | — | `#818CF8` | `#2F41F1` | `#312E81` |
| **Baby Blue** | `#BAE6FD` | `#38BDF8` | `#0091D1` | `#0C4A6E` |
| **Teal** | `#A5F3FC` | `#22D3EE` | `#00B2CD` | `#164E63` |
| **Mint** | `#99F6E4` | `#2DD4BF` | `#00A994` | `#134E4A` |
| **Green** | `#BBF7D0` | `#4ADE80` | `#00B341` | `#14532D` |
| **Lime** | `#D9F99D` | `#A3E635` | `#77BF00` | `#365314` |
| **Lime/Yellow** (Chaki) | `#F7FFBA` | `#CDDE4A` | `#A7BD00` | `#596500` |
| **Yellow** | `#FFF7BA` | `#FDE047` | `#DFBB00` | `#68380D` |
| **Orange** | `#FED7AA` | `#FB923C` | `#ED6B00` | `#631F07` |
| **Red** | `#FECACA` | `#F87171` | `#FF2121` | `#7F1D1D` |

> Pattern for usage: **200** for background chips/tags, **400** for icons/accents, **600** for primary badge/label color, **900** for text on light backgrounds.

---

## Typography

**Font family:** [Geologica](https://fonts.google.com/specimen/Geologica) — used exclusively across all weights.

Token naming convention: `M` = Regular (400), `SM` = Medium (500), `B` = SemiBold (600).

| Token | Size | Weight | Style | Line Height |
|---|---|---|---|---|
| `B 10` | 10px | 600 | SemiBold | 100% |
| `M 12` | 12px | 400 | Regular | 100% |
| `B 12` | 12px | 600 | SemiBold | 100% |
| `M 14` | 14px | 400 | Regular | 100% |
| `SM 14` | 14px | 500 | Medium | 100% |
| `B 14` | 14px | 600 | SemiBold | 100% |
| `M 16` | 16px | 400 | Regular | 100% |
| `B 16` | 16px | 600 | SemiBold | 100% |
| `M 18` | 18px | 400 | Regular | 100% |
| `B 18` | 18px | 600 | SemiBold | 100% |
| `M 20` | 20px | 400 | Regular | 100% |
| `B 20` | 20px | 600 | SemiBold | 100% |

> Letter spacing is 0 on all tokens. Line height is 100% (tight) on all tokens.

---

## Shadows

All shadows are drop shadows with offset (0, 0) — purely diffused glows, no directional lift.

| Token | Color | Opacity | Radius | Spread | Usage |
|---|---|---|---|---|---|
| `Light Shadow` | `#000000` | 12% | 8px | 0 | Default card / panel elevation |
| `Focused` | `#3B82F6` | 20% | 10px | 0 | Input focus ring |
| `Error State` | `#F87171` | 30% | 6px | 0 | Input or element in error state |
| `Success State` | `#22C55E` | 30% | 6px | 0 | Input or element in success state |
| `Warning` | `#F4E111` | 30% | 6px | 0 | Input or element in warning state |

---

## Components

### Icons

**Library:** Font Awesome 7 Pro (Solid style)
**Size in buttons:** 12px rendered inside a 16×16px container

---

### Buttons

**Base specs** (all types):
- Height: `32px`
- Padding: `8px`
- Border radius: `4px`
- Gap (icon ↔ label ↔ icon): `4px`
- Text style: `M 14` (Geologica Regular, 14px)
- Icon: Font Awesome 7 Pro Solid, 12px

Buttons support optional left icon, label, and right icon — any combination can be shown/hidden.

#### Button Types & States

Buttons have **4 types** and an **`error` boolean modifier** that applies destructive styling to any type. This replaced the previous 6-type model.

**Filled (error=No)**

| State | Background | Border | Text & Icon |
|---|---|---|---|
| Enabled | `#3B82F6` | — | White |
| Hover | `#2563EB` | — | White |
| Pressed | `#1654DD` | — | White |
| Disabled | `#CBD5E1` | — | White |

**Filled (error=Yes)** — solid destructive, use for irreversible actions

| State | Background | Border | Text & Icon |
|---|---|---|---|
| Enabled | `#F87171` | — | White |
| Hover | `#F87171` | — | White |
| Pressed | `#F87171` | — | White |
| Disabled | `#FECACA` | — | White |

**Ghost (error=No)**

| State | Background | Border | Text & Icon |
|---|---|---|---|
| Enabled | — | `#3B82F6` | `#3B82F6` |
| Hover | `#EFF6FF` | `#2563EB` | `#2563EB` |
| Pressed | `#DBEAFE` | `#1654DD` | `#1654DD` |
| Disabled | — | `#94A3B8` | `#94A3B8` |

**Link (error=No)**

| State | Background | Border | Text & Icon |
|---|---|---|---|
| Enabled | — | — | `#3B82F6` |
| Hover | `#EFF6FF` | — | `#2563EB` |
| Pressed | `#DBEAFE` | — | `#1654DD` |
| Disabled | — | — | `#94A3B8` |

**Link (error=Yes)** — ghost-style destructive, use for lower-risk destructive actions

| State | Background | Border | Text & Icon |
|---|---|---|---|
| Enabled | — | — | `#F87171` |
| Hover | `#FFF3F3` | — | `#F87171` |
| Pressed | `#FECACA` | — | `#F87171` |
| Disabled | — | — | `#FECACA` |

**White (error=No)**

| State | Background | Border | Text & Icon |
|---|---|---|---|
| Enabled | `#FFFFFF` | `#E2E8F0` | `#1A212C` |
| Hover | `#F8FAFC` | `#E2E8F0` | `#1A212C` |
| Pressed | `#F1F5F9` | `#E2E8F0` | `#1A212C` |
| Disabled | `#CBD5E1` | — | White |

> **Choosing destructive style:** Use **Filled + error** for permanent/irreversible actions (e.g. delete). Use **Link + error** for lower-prominence destructive actions (e.g. remove an item inline).

---

### Tabs

Used for in-page navigation within boards and detail pages.

**States:** Default, Hover, Disabled, Selected (active tab)
**Badge variants:** None, Number (count), Attention (red dot)

| State | Selected | Appearance |
|---|---|---|
| Default | No | Plain text, gray |
| Disabled | No | Lighter gray, not interactive |
| Hover | No | Slightly darker text |
| Default | Yes | Blue text + blue underline |
| Hover | Yes | Blue text + blue underline, subtle bg |

Badge types add a small indicator after the label:
- **Number** — shows a count (e.g. `3`)
- **Attention** — shows a red dot for alerts

---

### Checkbox

**States:** Checked, Unchecked, Multiple Selection (indeterminate), Disabled (checked & unchecked)
**Size:** 20×20px

---

### Radio Button

**States:** Selected, Unselected, Disabled (selected & unselected)
**Size:** 20×20px

---

### Switch (Toggle)

**States:** Active (on), Inactive (off), Disabled (both)
**Size:** 58×38px

---

### Priorities

Used for task/ticket priority labelling.

| Priority | Colour |
|---|---|
| No priority | Gray |
| Urgent | Red |
| High | Orange |
| Medium | Yellow |
| Low | Blue/Gray |

---

### Search Bar

**Size:** 300×32px
**States:**

| State | Description |
|---|---|
| Default | Placeholder text, no focus |
| Focused / Empty | Focus ring active, no input |
| Filled / Focused | Has input, focus ring active |
| Filled / No Focus | Has input, no focus ring |

---

### Select (Dropdown)

6 size variants based on the number of visible options (1–6 items). Width: 138px.

---

### Tooltip

Single variant. Width: ~150px.

---

### Toast Messages

Auto-dismissing feedback messages. 4 types × 3 time-indication states.
**Size:** 280×84px

| Type | Icon colour | Example message |
|---|---|---|
| **Success** | Green | "Your changes are saved successfully." |
| **Info** | Blue | "New Settings Available on your account." |
| **Error** | Red | "Error has occurred while saving changes." |
| **Warning** | Yellow/Orange | "Username you have entered is invalid." |

**Time Indication states** (progress bar showing time remaining before auto-dismiss):
- **Start** — bar full
- **Mid** — bar half
- **End** — bar nearly empty

---

## Navigation

### Sidebar Header

The top bar of the sidebar. Always visible, not scrollable.

| Property | Value |
|---|---|
| Width | `230px` |
| Padding | `12px 24px` |
| Background | `#F8FAFC` (BG/Lightest Gray) |
| Logo icon | 24×24px, blue `#3B82F6` rounded square |
| Wordmark | 85×18px SVG |
| Collapse icon | FA `angles-left`, 14px, `#1E293B` (Gray 800) |

---

### Sidebar Section (parent nav item)

Each collapsible section in the sidebar (e.g. Overview, Sales, Fleet).

| Property | Value |
|---|---|
| Width | `230px` |
| Padding | `8px` |
| Gap | `4px` |
| Section icon | 16×16px (custom per section) |
| Label | Geologica Regular 14px, `#1A212C` |
| Caret (closed) | FA `caret-right`, 10px, `#1A212C` |
| Caret (open) | FA `caret-down`, 10px, `#1A212C` |

**States:** Closed (caret-right, no children visible) / Open (caret-down, children stacked below).

---

### List Item (child nav item)

Sub-pages within each sidebar section.

| Property | Value |
|---|---|
| Width | `194px` (230px when full-width in open section) |
| Height | `30px` |
| Padding left | `36px` |
| Border radius | `4px` |
| Gap | `20px` (left indicator line → label) |
| Left indicator | Thin vertical line (decorative, full height) |
| Text style | Geologica 12px |

**States:**

| State | Background | Text color | Font weight |
|---|---|---|---|
| Default | — | `#64748B` (Gray 500) | Regular |
| Hover | `#F8FAFC` (BG/Lightest Gray) | `#1A212C` | Regular |
| Selected & Hover | `#F1F5F9` (Gray 100) | `#1A212C` | SemiBold |
| Disabled | — | `#CBD5E1` (Gray 300) | Regular |

---

### Category Header

Used for top-level groupings like "My Hub", "Favorites", "Workspace" — sections that contain sidebar sections.

| Property | Value |
|---|---|
| Width | `194px` |
| Padding | `12px 8px` |
| Gap | `4px` |
| Label | Geologica SemiBold 12px, `#0F172A` (Gray 900) |
| Caret (closed) | FA `caret-right`, 10px, `#0F172A` |
| Caret (open) | FA `caret-down`, 10px, `#1A212C` |

---

### Board / List Title

The page title bar shown at the top of every board (e.g. BOOKINGS, SUBSCRIPTIONS).

| Property | Value |
|---|---|
| Favorite star (off) | FA `star` Light, 14px, `#3B82F6` |
| Favorite star (on) | FA `star` Solid, 14px, `#3B82F6` |
| Board name | Geologica SemiBold 16px, `#1A212C` |
| Item count | Geologica Regular 12px, `#94A3B8` (Gray 400), format: `(n)` |

---

### Ticket Title Bar

The sub-header shown when a specific ticket or record is open.

| Property | Value |
|---|---|
| Height | `40px` |
| Padding | `20px` horizontal |
| Bottom border | 1px solid `#CBD5E1` (Gray 300) |

**Left side — breadcrumb:**
- Back arrow: FA `Arrow-left`, 14px, `#3B82F6`
- Board name: Geologica SemiBold 12px, `#1A212C`
- Separator `/`: Geologica Regular 12px, `#64748B`
- Ticket ID: Geologica Regular 12px, `#64748B`
- Refresh: FA `arrow-rotate-right`, 14px, `#3B82F6`

**Right side — actions:**
- Optional **Lost** button: Filled + error=Yes (`#F87171`), FA icon `skull-crossbones`
- Options buttons: Ghost icon-only, FA `ellipsis`, 12px, `#3B82F6`

---

## Fields

Form input components used across all Instafleet boards and detail pages.

### Base Field Specs

Applies to all field types (Text, Dropdown, Date, Number):

| Property | Value |
|---|---|
| Width | `223px` (base); min `230px`, max `400px` in composite with title |
| Height | `40px` |
| Padding | `12px` vertical / `10px` horizontal |
| Border radius | `4px` |
| Text style | Geologica Regular 14px |

---

### Field States

All field types share the same state model. Text field is the reference; other types follow the same pattern with type-specific additions noted below.

| State | Background | Border | Text color | Notes |
|---|---|---|---|---|
| Default | `#FFFFFF` | `#CBD5E1` (Gray 300) | `#1A212C` | — |
| Hover | `#FFFFFF` | `#CBD5E1` | `#1A212C` | Same as Default |
| Focused | `#F8FAFC` | `#93C5FD` (Blue 300) | `#1A212C` | Text cursor visible |
| Disabled | `#FFFFFF` | `#CBD5E1` | `#64748B` (Gray 500) | Muted text, not interactive |
| Error | `#FFFFFF` | `#FECACA` (Red 200) | `#F87171` (Red 400) | Error message below in Red 400, Regular 12px |
| Non Editable / Read Only | `#FFFFFF` | `#F1F5F9` (Gray 100) | `#1A212C` | Very subtle border, no interaction |

---

### Field Types

**Text** — standard single-line text input. Reference implementation for all state specs above.

**Dropdown** — same container as Text. Adds:
- Right-side caret icon: FA `caret-down`, 14px, `#1A212C`
- Sub-variants: **Simple** (plain text value), **Chip** (coloured tag value), **Assignee** (avatar + name), **Priority** (priority icon + label)

**Date** — same container as Text. Adds a calendar picker.

**Number** — same container as Text. Numeric input only.

**Checkbox** — see [Checkbox component](#checkbox) above.

---

### Field Title

Labels displayed above a field. Three variants:

| Variant | Appearance |
|---|---|
| **Normal** | Geologica Regular 14px, `#1A212C` |
| **Mandatory** | Same + asterisk `*` in `#3B82F6` (Blue 500) |
| **Infos** | Same + blue pill badge (bg `#DBEAFE`, FA `info` icon 8px `#3B82F6`) |

---

### Field with Title (Composite)

A label stacked above a field input, used throughout detail pages and forms.

| Property | Value |
|---|---|
| Layout | Vertical stack, gap `8px` |
| Min width | `230px` |
| Max width | `400px` |

The title variant (Normal / Mandatory / Infos) is set independently of the field state.

---

## Lists

Components used to render board list views and Kanban views.

---

### List Title Row (Column Header)

The header row of a list table. Each column header is a standalone component.

| Property | Value |
|---|---|
| Height | `36px` |
| Padding | `12px` left / `10px` right / `10px` vertical |
| Border | Right side only, `#CBD5E1` |
| Text | Geologica SemiBold 12px, `#1A212C` |

**States:**

| State | Background | Right-side icons |
|---|---|---|
| Default | — | — |
| Hover | `#F8FAFC` | FA `arrow-down-arrow-up` 14px `#94A3B8` + FA `ellipsis-vertical` 14px `#94A3B8` |

---

### List Item Row

A single data row in a list view. Shares the same container as the title row but renders a value instead of a column label.

**Container specs:** Height `36px` · Padding `12px` left / `10px` right · Border right `#CBD5E1`

**Disabled state:** `opacity: 60%` applied to the whole row.

10 item types are supported:

| Type | Enabled | Content | Icon / Control |
|---|---|---|---|
| **Text** | Yes / No | Geologica Regular 12px `#1A212C`, truncated | — |
| **Action** | Yes only | — | FA `trash` Solid 12px `#F87171` (red) |
| **Dropdown** | Yes / No | Geologica Regular 12px `#1A212C`, truncated | FA `caret-down` Solid 14px `#1A212C` on right |
| **Link** | Yes / No | Geologica Regular 12px `#3B82F6` (blue), truncated | — |
| **Chip** | Yes / No | Pill: bg `#E2E8F0`, rounded-full, padding `6px`, gap `2px` · FA `caret-down` 8px `#334155` + label Geologica Regular 12px `#334155` + FA `caret-down` 8px `#334155` | Embedded in chip |
| **Toggle** | Yes / No | Switch component | — |
| **Checkbox** | Yes / No | 20×20px checkbox | — |
| **Date** | Yes / No | Geologica Regular 12px `#1A212C` | FA `calendar` Regular 14px `#1A212C` on right |
| **Number** | Yes / No | Geologica Regular 12px `#1A212C` | Stacked FA `caret-up` + `caret-down` Solid 10px `#1A212C` on right |
| **Radio Button** | Yes / No | 20×20px radio button | — |

---

### List Toolbar

The top action bar above every board list or Kanban. Height `40px`. Two view variants: **List** and **Kanban** — the active view icon gets a `#EFF6FF` background, the inactive one is plain.

**Left side:**

| Element | Specs |
|---|---|
| View switcher | List icon \| Kanban icon — active has bg `#EFF6FF`; icons are 16×16px |
| Search bar | FA `search` Regular 14px `#94A3B8` + placeholder Geologica Regular 12px `#94A3B8`, left padding `20px` |

**Right side (left → right):**

| Element | Icon | Size | Color |
|---|---|---|---|
| ERFUDD Alerts toggle | Switch (on) + label "ERFUDD Alerts" | — | Label: Geologica Regular 12px `#1A212C` |
| Filter | FA `bars-filter` Solid | 14px | `#64748B` |
| Export / Download | FA `download` Solid | 14px | `#64748B` |
| Divider | — | 28px tall | `#CBD5E1` |
| Refresh | FA `arrow-rotate-right` Regular | 14px | `#64748B` |
| Column visibility | FA `columns-3` Regular | 14px | `#64748B` |
| Date range | FA `calendar-circle-plus` Regular | 14px | `#64748B` |
| Divider | — | 28px tall | `#CBD5E1` |
| CTA Button | Link type with icon + label | 32px | Blue (`#3B82F6`) |

---

### Kanban Ticket

The card shown in Kanban board columns. 4 variants:

| Variant | Width | Background | Notes |
|---|---|---|---|
| **Card** | `304px` | `#FFFFFF` + shadow | Default state |
| **Variant2** | `304px` | `#F8FAFC` | Hover state |
| **Instatrade** | `296px` | `#FFFFFF` + shadow | Instatrade-specific layout |
| **Instatrade Hover** | `296px` | `#F8FAFC` | Instatrade hover state |

**Card container:** Border `1px #E2E8F0` · Border radius `8px` · Padding `12px` · Gap between sections `8px`

**Card / Variant2 content (top → bottom):**

| Element | Style |
|---|---|
| Ticket code | Geologica Regular 12px `#3B82F6` |
| Assignee avatar | 20px circle, bg `#3B82F6`, initials white Geologica Regular 10px |
| Title | Geologica Regular 14px `#1E293B`, truncated |
| Body / subtitle | Geologica Regular 12px `#64748B`, truncated |
| Amount (Card only) | Geologica Regular 12px `#1A212C` |
| Label chips | Pill: bg `#E2E8F0`, Geologica Regular 12px `#334155`, rounded-full, padding `6px` |
| Timestamps | Geologica Regular 10px `#94A3B8` — "Created at", "Updated at" |
| Service dates | Geologica Regular 10px `#94A3B8` — "In Service", "Out Of Service" |

**Instatrade content (key-value layout):**

Each row: label fixed width `60px` Geologica Regular 12px `#64748B` · value flex Geologica Regular 12px `#1A212C` (except Lease value which is `#3B82F6` blue)

Fields shown: Client · Sell · Plate · Lease · Contract Period

Status indicator: FA `check` Solid 14px `#00B341` + "Docs Uploaded" Geologica Regular 12px `#00B341`

Timestamp: Geologica Regular 10px `#94A3B8`

---

## Email Composer

The email compose UI used in the Unified View. Two variants: **Default** (embedded in the page) and **Window** (floating "New Message" modal).

**Container:** 780×700px · bg `#FFFFFF` · border-radius `8px` · shadow: `rgba(59,130,246,0.2)` blue glow (the Focused shadow token)

---

### Recipient Fields

Each address row is a standalone component. Height `40px`, padding vertical `12px`.

| Field | Label | Notes |
|---|---|---|
| **To:** | "To:" in Geologica Regular 14px `#1E293B` | Right side shows "Bcc" and "Cc" toggle links (Geologica Regular 14px `#3B82F6`, gap `8px`) |
| **Cc:** | "Cc:" | Same structure, no toggle links, bg `#FFFFFF` |
| **Bcc:** | "Bcc:" | Same as Cc |

**Email chip** (added recipient): bg `#E2E8F0`, rounded-full, padding `6px` · Geologica Regular 12px `#334155` · FA `xmark` Solid 8px `#334155` to remove

**Placeholder:** Text cursor `|` (16px `#1A212C`) + "Type emails" (Geologica Regular 14px `#CBD5E1`)

---

### Rich Text Editor (Email Body)

Height `290px` · Border `1px #CBD5E1` · Border-radius `8px`

**Toolbar** (padding `12px`, flex row, space-between):

Left side:
- Font style selector: "Normal" text (Geologica Regular 14px `#1A212C`) + small caret icon
- **Templates** button: Filled blue (`#3B82F6`), 32px height

Right side — formatting icons (all FA Solid 14px `#475569`, 20×20px hit targets):

| Group | Icons |
|---|---|
| Text formatting | `bold` · `italic` · `underline` · `strikethrough` · `quote-right` |
| Lists & indent | `list-ol` · `list-ul` · `outdent` · `indent` |
| Insert | `link` · `paperclip` |
| Highlight | `marker` — active state: bg `#EFF6FF` pill (rounded-full, padding `2px`) |

Separator: 1px horizontal line `#CBD5E1`

**Body area:** Padding `20px` · Geologica Regular 14px `#1A212C` · whitespace pre-wrap

Scrollbar: `#CBD5E1`, 8px wide, rounded bottom corners

---

### Full Email Composer Layout

Fields rendered top-to-bottom:

| # | Field | Notes |
|---|---|---|
| 1 | **From** | Dropdown — value "drive@instacar.gr", FA `caret-down` Solid 14px `#1A212C`; uses the shared sender address |
| 2 | **To:** | Recipients row with Cc/Bcc toggles |
| 3 | **Cc:** | Optional, shown when toggled |
| 4 | **Bcc:** | Optional, shown when toggled |
| 5 | **Subject** | Mandatory field (asterisk `*` in `#3B82F6`), plain text input |
| 6 | **Body** | Rich text editor with toolbar (see above) |
| 7 | **Attachments** | Section with border `1px #CBD5E1`, rounded `8px`, padding `12px` |

**Attachment row:** FA `paperclip-vertical` Solid 12px `#64748B` · filename Geologica Regular 12px `#64748B` · upload date Geologica Regular 10px `#64748B` · Link+error trash button (FA `trash` 12px `#F87171`) on right

**Bottom action bar:**
- Left: **Send** button — Filled blue (`#3B82F6`), 32px
- Right: **Delete** button — Link+error style: FA `trash` 12px `#F87171` + "Delete" label Geologica Regular 14px `#F87171`

---

### Window Variant

Identical content to Default, but wrapped in a floating panel with a title bar at the top:

| Property | Value |
|---|---|
| Title bar background | `#EFF6FF` |
| Title bar padding | `12px` |
| Title text | "New Message" — Geologica Regular 14px `#1E293B` |
| Window controls (right) | FA `window-minimize` Solid 14px `#475569` · FA `xmark` Solid 14px `#475569` |
| Border radius | `8px` top corners only |

---

## InfoBar Fields

The informational sidebar shown on every ticket detail page. Width `286px`. Each field is a vertical stack: uppercase label on top, value below.

**Label style** (all types): Geologica Regular 12px · `#94A3B8` · UPPERCASE

**Gap between label and value:**
- Text, Link: `4px`
- Chip, Checkbox, Toggle, Field: `8px`

**6 field types:**

| Type | Value appearance | Extra |
|---|---|---|
| **Text** | Geologica Regular 14px `#1A212C` | FA `copy` Regular 14px `#94A3B8` icon on right |
| **Link** | Geologica Regular 14px `#3B82F6` (blue) | FA `copy` Regular 14px `#94A3B8` icon on right |
| **Chip** | Green pill: bg `#D4FFE3`, text `#14532D` Geologica Regular 12px | Optional add pill: bg `#E2E8F0`, FA `add` 8px `#334155` |
| **Checkbox** | 20×20px checkbox component | — |
| **Toggle** | Switch component (58×38px) | — |
| **Field** | Full text input: bg `#FFFFFF`, border `1px #CBD5E1`, height `40px`, border-radius `4px`, full width | — |

---

## History Items

The activity timeline shown in the History tab of every ticket. Items are displayed as a vertical list connected by a timeline rail.

### Timeline Rail

Each item has a left-side rail:
- Vertical line: thin, gray (`#CBD5E1`)
- Node marker: `#60A5FA` (Blue 400), `10×4px`, border-radius `2px`

### Content Structure (shared by all types)

Right of the rail — vertical stack, padding vertical `16px`, gap `4px`:
- **Timestamp**: Geologica Regular 12px `#1A212C`
- **Type badge** (Status Chip): bg `#DBEAFE` · Geologica SemiBold 12px `#1E3A8A` · UPPERCASE · border-radius `4px` · padding `4px`
- **Secondary chips** (agent, status, stage, etc.): bg `#FFFFFF` · border `0.5px #CBD5E1` · Geologica Regular 12px `#94A3B8` · same dimensions
- **Body text**: Geologica Regular 12px `#475569`

### 11 History Item Types

**Ticket**
- FA `up-right-from-square` Solid 14px `#3B82F6` before the type badge
- Chips: type badge (TASK) + status chip + stage chip + agent name chip + ticket ID (blue `#3B82F6`, no chip)
- Optional body text + optional "Reason: [value]" key-value (label `#64748B`, value `#1A212C`)

**Changelog**
- Chips: CHANGELOG badge + agent name chip
- Field change row: field name in Geologica SemiBold 12px `#1A212C` + "From:" label `#64748B` + old value `#1A212C` + "To:" label `#64748B` + new value `#1A212C`

**SMS**
- Chips: SMS badge + channel chip (with small colored dot indicator) + optional "NOT RECEIVED" warning chip (bg `#FFF7BA`, border `#FDE047` Yellow, text `#68380D`)
- Sender/Recipient row: label `#94A3B8` + sender name `#3B82F6` + FA `arrow-right` Solid 7px `#93C5FD` + recipient `#3B82F6`
- Body text

**Comment (Edited=No)**
- Chips: COMMENT badge + agent name chip
- Body text (full width)

**Comment (Edited=Yes)**
- Same as above but body row has inline edit/delete actions on the right: FA `pen` Regular 14px `#3B82F6` + FA `trash` Regular 14px `#F87171`
- "Updated Xmin ago" footer: Geologica Regular 10px `#94A3B8`

**Email (Simple Mail, Expanded=Yes)**
- FA `up-right-from-square` + EMAIL badge + status chip (DONE)
- Email title (Geologica SemiBold 12px `#1A212C`) + Sender/Recipient row (same pattern as SMS)
- Body text preview + FA `chevron-up` Solid 14px `#3B82F6` (collapse toggle)
- **Reply** button — Link type, blue

**Email (Simple Mail, Expanded=No)**
- Same header, body truncated to one line with FA `chevron-down` expand toggle

**Email (Reply, Expanded=No)**
- Collapsed: same header as Email, body on one line, chevron-down
- Expanded: renders the full Email Composer component inline (see [Email Composer](#email-composer)), with **Reply** button at bottom

**Email (Template, Expanded=Yes)**
- Same header as Email
- Body shows the full branded email template preview (375px wide, dark `#242731` background, Proxima Nova font, orange `#FF6500` CTA button, Instacar footer)
- FA `chevron-up` collapse toggle + **Reply** button

**Exception**
- Top row: "Start: [datetime]" + "End: [datetime]" — Geologica Regular 12px, label `#64748B` / value `#1A212C`, gap `8px`
- EXCEPTION badge
- "Amount Charged: [value]" key-value
- Body description text

**Promise**
- Same structure as Exception
- PROMISE badge
- "Amount Promised: [value]" key-value
- Body description text

---

## Cards

Selectable and informational cards used in billing and guarantor sections of the subscription and payment flows.

---

### Billing Info Card

A selectable card representing a billing entity (individual or company). Used when an agent picks or edits billing details.

**Container:** Width ~291px · Padding `20px` · Border-radius `16px` · Gap `12px`

**5 states:**

| State | Background | Border | Shadow | Radio |
|---|---|---|---|---|
| **Selected** | `#FFFFFF` | `#93C5FD` (Blue 300) | Blue glow `rgba(59,130,246,0.2)` | Selected |
| **Hover Selected** | `#F8FAFC` | `#93C5FD` | Blue glow | Selected |
| **Deselected** | `#FFFFFF` | `#CBD5E1` | — | Unselected |
| **Deselected/Hover** | `#F8FAFC` | `#CBD5E1` | — | Unselected |
| **Disabled** | `#FFFFFF` | `#CBD5E1` | — | Unselected · `opacity: 60%` |

**Header row** (top of card, flex row):
- Company/person name: Geologica SemiBold 14px `#1A212C`, flex-1
- Edit icon: FA `pen` Solid 18px `#3B82F6`, 20×20px container
- Radio button: 20×20px

**Data rows** (gap `8px` between rows · gap `4px` between label and value):

| Field | Label width | Label style | Value style |
|---|---|---|---|
| TIN | 60px | Geologica Regular 12px `#64748B` | Geologica Regular 12px `#1A212C` |
| Company Name | 60px | same | same |
| DOY | 60px | same | same |
| Activity | 60px | same | same |
| Email | 60px | same | same |
| Address | 60px | same | same |
| Postal Code | 60px | same | same |

---

### Guarantor Card

A read/edit card displaying guarantor information. Used in the Payment & Billing tab of subscriptions.

**Container:** Width `900px` (full-width) · Height `138px` · Bg `#FFFFFF` · Border `1px #E2E8F0` · Border-radius `12px` · Padding `12px`

Two variants (**Default** and **Variant2**) with identical visual layout.

**Layout:** Three-column horizontal:

| Column | Width | Content |
|---|---|---|
| Left | flex-1 | Name (SemiBold 16px `#1A212C`) + Email + Phone |
| Middle | `400px` fixed | TIN + Address + Company Name + DOY |
| Right | `16×16px` | FA `pen` Solid 14px `#3B82F6` (edit) |

**Left column fields** — label fixed `70px`, value flex:
- Email
- Phone

**Middle column fields** — label fixed `80px`, value flex:
- TIN · Address · Company Name · DOY

All key-value pairs: label Geologica Regular 14px `#64748B` · value Geologica Regular 14px `#1A212C` · gap `8px`

---

## Related pages

- [[booking]]
- [[subscriptions]]
- [[arm]]
- [[navigation]]
