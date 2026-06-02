# Wiki Maintenance Instructions

These instructions apply to all markdown files in the `wiki/` directory.

## Page Format
Every wiki page MUST follow this structure:

```markdown
# Page Title

**Summary**: One to two sentences describing this page.
**Context**: [instacar] or [blog] or [personal] or [concepts]
**Sources**: List of raw source files this page draws from.
**Last updated**: YYYY-MM-DD

***

Main content...

## Related pages
- [[related-concept-1]]
```

## Rules
- **Filenames:** Lowercase with hyphens (e.g., `instacar-product-strategy.md`).
- **Linking:** Use `[[wiki-links]]` to connect concepts.
- **Index:** Always update `wiki/index.md` after adding or renaming a page.
- **Log:** Always append a record of changes to `wiki/log.md`.
- **Consistency:** If a concept cuts across contexts, keep it neutral and link to context-specific pages.
