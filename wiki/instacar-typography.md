# instacar-typography

**Summary**: Defines the mandatory font family, weight hierarchy, and sizing scale for InstaCar, prioritizing readability and a modern aesthetic over stylistic variety to ensure information is consumed efficiently on all devices.
**Context**: [instacar] or [concepts]
**Sources**: instacar.gr-DESIGN.md
**Last updated**: 2026-06-19

***

## Core Font System
*   **Primary Font Family:** Proxima Nova (Fallback: `system-ui, -apple-system, sans-serif`). The system relies solely on weight and size variation of this single font family.
*   **Font Philosophy:** Weight drives hierarchy (700 for headings, 400 for body/interactive elements). Size variety must be restricted to a small, controlled set of levels.

## 📐 Type Scale Hierarchy & Usage
The system enforces distinct typographical tiers to guide the user's attention through pricing and product details. Line height is kept generous across all sizes for comfortable reading:

| Semantic Role | Font Size (px) | Weight | Line Height Ratio | Example Use Case | Notes on Impact |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Display / Hero** | 32px | 700 | 1.5x (`48px`) | Primary page headers, large calls-to-action copy sections. | High impact, reserved for major selling points. |
| **H1 / Page Title** | 24px | 700 | 1.25x (`25px`) | Top-level content titles (e.g., "Product Features"). | Clear identity for the user's current view. |
| **H2 / Section Header** | 32px | 700 | 1.5x (`48px`) | Major section dividers or defined category groupings. | Must maintain high visibility. |
| **H3 / Subhead** | 16px | 700 | 1.5x (`24px`) | Card headings, nested content labels, feature bullet points. | Good for organizing information chunks. |
| **H4 / Medium Emphasis** | 20px | 400 | 1.4x (`28px`) | Featured pricing details (e.g., 'Monthly Rate'), key copy emphasis within body text.| Subtler than headings, but still demands attention. |
| **Body / Standard Text**| 14px | 400 | 1.5x (`20px`) | Primary paragraph dumps, product descriptions, core details. | The workhorse of the system; must be highly readable and consistently spaced. |
| **Span / Auxiliary Copy**| 16px | 400 | 1.5x (`24px`) | Metadata tags, contextual information blocks (e.g., "Ideal for families"). | Slightly larger than body text to signal secondary but important detail. |
| **Caption / Fine Print**| 12px | 400 | 1.3x (`16px`) | Legal disclaimers, micro-copy, footer information. | The smallest size; treat as non-critical reads. |
| **Button / CTA Label** | 16px | 400 | 1.5x (`24px`) | All text within interactive buttons and primary link calls. | Consistent height (minimum 44px) is mandatory. |

## Principles for Scale Usage
1.  **Consistency:** Only use Proxima Nova variants; do not vary font styles arbitrarily.
2.  **Emphasis:** Use weight variance (700 vs 400) first, and size variation second, to create a natural hierarchy.
3.  **Line Height:** Maintain large line-height values (`1.4x` minimum for body text; `1.5x` preferred) to improve scannability on light backgrounds (source: instacar.gr-DESIGN.md).

## 🛑 Typographical Don'ts
*   Letter spacing must remain at the default value or `0`. Any deviation is considered a visual break from professional standards (source: instacar.gr-DESIGN.md).
*   Do not center-align large blocks of body copy; left alignment is mandatory for optimal reading flow.