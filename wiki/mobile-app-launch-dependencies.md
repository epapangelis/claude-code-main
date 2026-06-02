# Product Launch Dependency Model - Mobile Apps

**Summary**: Outlines key product dependencies for mobile application releases, establishing a pattern for coordinating multiple feature rollouts (e.g., Login flow vs. main feature sets) and emphasizing the critical role of successful QA testing windows.
**Context**: [instacar]
**Sources**: raw/articles/slack-discussion-release-timeline-2026-06-02.md
**Last updated**: 2026-06-02

***

## 1. Feature Dependencies and Sequencing (Login Flow)

A recurring theme in product releases is the need to define the minimum viable feature set (MVFS) that must ship first to keep the development momentum going.

*   **Login Requirement First**: When introducing a major change (e.g., modifying the main screen image), the most foundational components, such as the **Login flow**, must be prioritized for a standalone release.
    *   *Example:* If the app requires a new main screen image, the *Login* should be released first, as its completion provides the stable foundation needed for the subsequent visual updates. (Source: raw/articles/slack-discussion-release-timeline-2026-06-02.md)

## 2. Release Cadence and QA Buffer

Managing the gap between development completion and live release requires careful coordination between product stakeholders (Product Designers, Product Managers) and engineering teams.

*   **The QA Buffer:** There is a high probability that any release, regardless of development effort, will require a buffer period for Quality Assurance (QA) to run and raise `findings` (bugs/issues).
    *   *Best Practice:* Project timelines must factor in **extra days/weeks** *after* the developers declare the product "ready" to accommodate this QA cycle. (Source: raw/articles/slack-discussion-release-timeline-2026-06-02.md, raw/articles/slack-discussion-release-timeline-2026-06-02.md)
*   **Timeline Agreement:** When conflicts arise between quick, immediate launches (e.g., Monday/Tuesday) and the need for validation, the timeline must be set by **consensus** (Source: raw/articles/slack-discussion-release-timeline-2026-06-02.md).
*   **Estimation:** For strategic planning, requesting a rough, macro-level estimation (e.g., "2-3 weeks" instead of "a few extra days") is necessary to enable subsequent project scheduling.

## 3. General Product Launch Principles

When coordinating multiple related applications or features, the following principles apply:

*   **Cohesive Launch:** If two or more applications are closely related (e.g., two parts of the same ecosystem), there is strong support for integrating them into a single, comprehensive release to provide a seamless, holistic user experience. (Source: raw/articles/slack-discussion-release-timeline-2026-06-02.md)
*   **Single Source of Truth:** All release decisions and dependencies must be documented in a central place (e.g., the Jira/Linear ticket tracking system, or this wiki page) to prevent scope creep and misaligned expectations.

## Related pages
- [[mobile-app-launch-dependencies]] (Self-reference)
- [[product-release-timeline]] (Potential related page)
- [[kill-pipedrive]] (Related to migration/launching a new system)

---