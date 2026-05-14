# Wiki Operations Log

Append-only record of all wiki changes.

---

## 2026-04-15 (Session 1)

**Ingested**: instacar_claude_project_instructions.md, instafleet_team_usage.md, PRD_n8n_Workflow_Automation_instacar_v2.pdf

**Created**: wiki/index.md, wiki/log.md

**Summary**: Initialized wiki with table of contents mapping company context, products, active roadmap initiatives, and technical reference areas. Ready for detailed pages to be written on demand.

---

## 2026-04-15 (Session 2 -- Full Raw Ingest)

**Ingested**: instacar-uk-launch-spec.md, PRD_n8n_Workflow_Automation_instacar_v2.pdf (full), swagger.json, subs export.csv, subs report.csv

**Not ingested (too large / binary)**: Kill Pipedrive Plan.pdf, instacar Booking Flow.pdf, instacar_offer_16_03_2026.pdf, n8n-documentation.pdf, all image files (png, jpg)

**Created**:
- wiki/instacar-uk-launch-spec.md -- Phase 1 UK launch spec (buy + sell-to-us verticals, Instacar Promise, action items)
- wiki/n8n-workflow-automation.md -- full PRD for n8n financial document automation
- wiki/instafleet.md -- instafleet overview, teams, workspaces
- wiki/instafleet-sales.md -- Sales team screens and Pipedrive dependency
- wiki/instafleet-subscriptions.md -- CS team subscription module and tabs
- wiki/instafleet-arm.md -- ARM team ticket management
- wiki/kill-pipedrive.md -- initiative to migrate Sales off Pipedrive
- wiki/kill-trello.md -- initiative to migrate Trello usage
- wiki/defleet.md -- fleet end-of-life process initiative
- wiki/booking-flow-redesign.md -- booking flow redesign initiative
- wiki/instacar-api.md -- API endpoint reference from swagger
- wiki/subscriptions-data-model.md -- subscription schema, fields, tags, status values

**Updated**: wiki/index.md -- added all new pages, added UK expansion section

**Summary**: Full ingest of all processable raw files. All index.md skeleton pages now have corresponding wiki pages. 4 large PDFs and all image files remain undigested (require manual upload or smaller file sizes to process).

---

## 2026-04-15 (Session 3 -- Linear instacar-uk sync)

**Source**: Linear instacar-uk team (UK-1 through UK-18)

**Updated**: wiki/instacar-uk-launch-spec.md

**Changes**:
- Corrected sell vertical URL to /instatrade + /instatrade/find-your-vehicle (not /sell)
- Added /privacy page as required (UK GDPR + PECR)
- Removed homepage row; added 301 redirect note (/ → /buy, no homepage in Phase 1)
- Added cookie consent (Cookiebot) as pre-launch requirement
- Added contact email decision as open item (drive@ vs hello@instacar.uk)
- Added WhatsApp routing as open blocker
- Added USPs/marketing copy as urgent dependency for multiple pages
- Updated action items: Linear creation marked done, backend scoping, PreLeads decision all surfaced as active tickets
- Clarified UK Instatrade uses UK plate lookup API

---

## 2026-04-15 (Session 4 -- Index audit and link fixes)

**Source**: Full read of all wiki pages

**Updated**: wiki/index.md, wiki/instacar.md, wiki/customer-facing-platform.md, wiki/users-b2c.md

**Changes**:
- Rewrote index.md descriptions to be substantially richer -- each entry now summarizes key content, not just the page title
- Added "Missing Pages" section to index flagging [[instacar-offer]] (referenced in 2 pages, no page exists)
- Fixed broken [[instacar-uk]] links in instacar.md and customer-facing-platform.md -- corrected to [[instacar-uk-launch-spec]]
- Annotated [[instacar-offer]] references in customer-facing-platform.md and users-b2c.md as "no page yet"

**Summary**: Index now accurately reflects all wiki content. Two broken link types identified and fixed. One missing concept (instacar-offer) flagged for future creation.

---

## 2026-04-16 (Session 6 - Blog ingest)

**Ingested**: All 17 articles from raw/blog/

**Files processed**:
1st instacar hackathon.md, Be the problem solver in the room.md, BoldieBot Daily Script.md, BoxNow x instacar.md, Don't Sleep on Microsoft Clarity.md, Embracing Second-Level Thinking.md, How I Learn New Things.md, How many weeks do you have left?.md, I hired my first PM.md, Internal resistance.md, Outwork everyone.md, Prophet forecasting.md, The Art of Fast Delivery.md, The Reset.md, Velocity over everything.md, Yearly Recap 2024.md, instacar Featured by Microsoft Clarity.md

**Created**:
- wiki/blog-articles.md -- catalog of all 17 articles with key takeaways, grouped by theme (instacar stories, product philosophy, mindset, technical tools)
- wiki/blog-microsoft-clarity-framework.md -- full behavioral analytics framework extracted from the Clarity deep-dive article; basis of the Microsoft Clarity case study
- wiki/blog-learning-system.md -- multi-LLM + NotebookLM learning framework
- wiki/blog-technical-tools.md -- BoldieBot (GA4 → Slack) and Prophet forecasting guide

**Updated**: wiki/index.md -- added [blog] section with 4 new pages, updated last updated date

**Summary**: First full blog ingest. 17 articles processed. Frameworks extracted and stored as standalone reusable pages. Recurring blog themes identified: velocity/iteration, empathy-driven product, behavioral data, continuous learning, finite time, building in public.

---

## 2026-04-16 (Session 7 - Wiki lint and cleanup)

**Source**: Lint audit of all instacar wiki pages

**Updated**: 15 wiki pages + index.md

**Changes**:
- Added `**Context**: [instacar]` field to all 15 pages that were missing it
- Fixed remaining broken `[[instacar-uk]]` link in customer-facing-platform.md → `[[instacar-uk-launch-spec]]`
- Merged kill-trello.md stub into instafleet.md (Key Active Workstreams section); stub converted to redirect
- Merged booking-flow-redesign.md stub into customer-facing-platform.md (Active Initiatives section); stub converted to redirect
- Removed `[[kill-trello]]` and `[[booking-flow-redesign]]` links from instacar.md, instafleet.md, kill-pipedrive.md, instacar-uk-launch-spec.md Related pages
- Removed unresolvable "Subscription Status hex codes" section from subscriptions-data-model.md
- Updated index.md: removed kill-trello and booking-flow-redesign entries from Roadmap Initiatives

**Summary**: Wiki cleaned up. Context field now present on all pages. Two stub pages collapsed. One persistent broken link fixed. One unverifiable data section removed.

---

## 2026-04-20 (Session 8 - Wiki lint and consolidation)

**Source**: Full lint audit of all instacar wiki pages

**Deleted**: wiki/kill-trello.md, wiki/instafleet-sales.md, wiki/instafleet-arm.md

**Created**: wiki/instacar-offer.md (stub)

**Changes**:
- Merged instafleet-sales.md and instafleet-arm.md content into instafleet.md (team usage sections); thin pages deleted
- Removed duplicate Subscription Data Model section from instafleet-subscriptions.md; replaced with link to subscriptions-data-model.md
- Stripped ticket-level status detail from kill-pipedrive.md; kept goal, approach, and feature list; Live status now points to Linear
- Removed Action Items table from instacar-uk-launch-spec.md; replaced with pointer to Linear project
- Removed staging API token from n8n-workflow-automation.md (security hygiene)
- Fixed *** separator to --- in instacar.md, users-b2c.md, users-b2b.md, customer-facing-platform.md
- Updated defleet.md related pages: [[instafleet-arm]] removed, replaced with [[instafleet]]
- Updated index.md: collapsed instafleet sub-pages, added instacar-offer

---

## 2026-04-15 (Session 5 - Kill Pipedrive v1 Linear sync)

**Source**: Linear project "Sales Pipeline -> instafleet" (fetched via Linear MCP)

**Updated**: wiki/kill-pipedrive.md, wiki/index.md

**Changes**:
- Full rewrite of kill-pipedrive.md with v1 launch scope from Linear tickets
- Added completed features table (13 shipped items)
- Added in-QA, Ready for Release, Code Review, Blocked, and Ready for Tech sections with ticket refs
- Added v2 scope section
- Added data engineering track note (DAT-62, Power BI / Neon)
- Updated index.md description to reflect v1 QA status

---

## 2026-04-20 (Session 9 - Blog article creation and Notion posting)

**Source**: raw/blog/My Personal Wiki Powered by Claude Code.md (original draft)

**Updated**: raw/blog/My Personal Wiki Powered by Claude Code.md, CLAUDE.md

**Created**: Notion entry in "Thoughts" database (dimosthenis avgeris workspace)

**Changes**:
- Renamed article to "LLM Wiki Framework with Claude Code"
- Removed all pizza fan greece references from article (problem statement, BLUF section, wiki contents)
- Added new "Claude Code Product Skills" section detailing 10 available skills (/update-config, /keybindings-help, /simplify, /loop, /schedule, /claude-api, /init, /review, /security-review, /fewer-permission-prompts)
- Added new "Obsidian Setup: Plugins & Tips" section covering Terminal plugin, Graph View, and the statusline hack with configuration examples
- Replaced "How LLMs Work" section with "Workflow Impact: First Week Data" featuring data-driven metrics on time savings (89% reduction in doc search, 91% reduction in re-reading), cognitive load reduction (66% context switching decrease), and knowledge reuse metrics with citations to Atlassian and Zappi research
- Added new "Meeting Digestion Workflow" section describing how to use Claude to transform meeting notes and Slack messages into context-rich Linear tickets
- Updated "What's Next" with concrete forward-looking goals (daily logs, Obsidian dashboard view)
- Added CLAUDE.md "Notion posting workflow" section with standard procedure for publishing articles

**Summary**: Article transformed from product tool overview into a comprehensive case study on building a personal LLM-powered knowledge management system. Key additions: practical product skills documentation, hands-on Obsidian setup guide, credible first-week impact metrics with external research validation, and workflow automation patterns for meeting-to-ticket conversion. Article now ready for publication to dimosthenisavgeris.com blog.

---

## 2026-04-20 (Session 10 - Roadmap system setup)

**Source**: Chris Noulis Slack message (4 instafleet projects for sprint prioritization)

**Created**:
- raw/instacar/chris-noulis-instafleet-projects-2026-04-20.md -- source file with 4 projects (Bundle sales, Procurement book, Dealer system access, instacar+ pilot)
- wiki/roadmap.md -- centralized tracker of all feature requests and work items, organized by date requested

**Updated**: CLAUDE.md (added Roadmap workflow section), wiki/index.md (added Roadmap & Planning section at top)

**First roadmap entry**:
- instafleet: 4 Projects for Sprint Prioritization (2026-04-20) -- pending prioritization; awaiting meeting with Chris

**Summary**: Roadmap system established. Single source of truth for all feature requests. Workflow: user adds to raw/ → say "add to roadmap" → I extract and organize by date → you query by date/context/status. Chris Noulis's 4 projects now tracked.

---

## 2026-04-20 (Session 11 - CGO Response Strategy digested to roadmap)

**Source**: raw/instacar/CGO_Response_Strategy.md

**Updated**: wiki/roadmap.md

**Changes**:
- Enhanced 2026-04-20 roadmap entry with detailed scoping for each of the 4 instafleet projects
- Added realistic effort estimates for each project (Bundle Sales: 1-2 weeks; Procurement Book: 2-6 weeks; Dealer System: 4-7 weeks; instacar+ Pilot: 2-3 weeks)
- Added strategic recommendations (UI-first for Bundle Sales, process mapping required for Procurement Book, separate Dealer System into 3 phases, clarify app capacity trade-off for instacar+ Pilot)
- Linked CGO response strategy document as reference for meeting prep

**Summary**: CGO Response Strategy document provides tactical playbook for the upcoming 30-min meeting with Chris Noulis. Clear scoping questions identified for each project to unlock realistic estimates. Status moved from "pending prioritization" to "scoped & ready for prioritization".

---

## 2026-04-20 (Session 12 - Revised roadmap estimates)

**Source**: Slack message from Dimosthenis with updated rough estimates

**Updated**: wiki/roadmap.md

**Changes**:
- **Bundle Sales**: Confirmed ~1-2 weeks (no changes from strategy doc)
- **Procurement Book**: Updated from "2-6 weeks" to "~2-3 weeks" (current state is 80% Excel + 20% instafleet; customs + ERFUDD logic is complexity driver)
- **Dealer System**: Updated from "4-7 weeks" to "~3-4 weeks" (3 separate features; recommend hard iteration on smaller chunks; ship Bookings & Ticketing 1st, etc.)
- **instacar+ Pilot**: Changed from "2-3 weeks" to "TBD" (need to sync with Togias on current state, service scope, ELTREKA implementation status)
- Added framing for prioritization conversation: focus on business need over complexity; managing parallel projects

**Notes**:
- Estimates are indicative only, will confirm Thursday
- Key constraint: several projects happening in parallel, need to sequence work
- Preference: iterative shipping over waiting for full spec

**Summary**: Rough estimates finalized for CGO conversation. Ready for prioritization discussion without getting bogged down in scope complexity.

---

## 2026-04-21 (Session 13 - Customer FAQ ingest)

**Ingested**: [Sell Vehicles] New LPs- FAQs.md

**Created**: wiki/instacar-customer-faqs.md

**Updated**: wiki/index.md (added instacar-customer-faqs entry under Products section)

**Changes**:
- Consolidated 14 vehicle category FAQs into single reference page
- Extracted repeating 4-question pattern: Why choose? → Inspection process? → Options? → Payment methods?
- Documented core trust signals: "like-new" positioning, <5 years age, zero accidents, thorough inspection, flexible payment (Santander 0% down + 84 months, or direct installments)
- Created category matrix covering size (small/medium/large/SUV), fuel (petrol/diesel/EV/hybrid/gas), transmission (auto/manual), and tier (premium/commercial)
- Captured language tone: formal, reassuring; "eliminate risk" framing
- Added usage notes for content maintenance and SEO templating

**Summary**: FAQ library consolidated as single source of truth for Sell Vehicles landing page content. Standardized messaging across categories enables scalable SEO content generation while maintaining brand voice consistency.

---

## 2026-04-22 (Session 14 - Car Swaps ingest and spec)

**Ingested**: car-swap-discussion.md, booking_creation_modal_swap_section.html, booking_detail_sidebar_and_warnings.html, subscription_list_swap_indicators.html, subscription_detail_swap_trigger.html, car_swap_modal.html

**Created**: wiki/carswaps.md

**Updated**: wiki/index.md (added carswaps entry under Roadmap Initiatives)

**Changes**:
- Created full carswaps wiki page covering: swap entitlement rules by contract type, booking label enum, trigger button spec (placement, states, eligibility pips), modal spec (header, left/right panels, 3-step flow), product carry-over logic table, warning states, three hard problems (race condition, deposit proration, bidirectional linking), and subscription list changes
- Documented all open questions: Extra Months rule, Bundles carry-over, Sign Up Fee recharge, Display To Offer inheritance, who can initiate, Instastart month count reset
- Linked to Linear project URL and noted status (empty shell, pending Finance validation)
- Two new HTML mockup files created: subscription_detail_swap_trigger.html and car_swap_modal.html

**Summary**: Full carswaps feature spec ingested and documented. Wiki now captures both the PRD-level logic and the designer-facing UI spec. Open questions explicitly flagged for resolution before final design.

---

## 2026-04-23 (Session 15 - Billing Detail Selection feature ticket)

**Source**: Product requirement from user (kill-pipedrive initiative; booking billing detail selection)

**Created**:
- Linear ticket PRO-2996: "Billing detail auto-select with toast confirmation in booking details"
- wiki/instafleet-billing-detail-selection.md

**Updated**: wiki/index.md (added instafleet-billing-detail-selection entry under Roadmap Initiatives section)

**Ticket structure**:
- Full Linear ticket with all sections: Description, What we currently do, What to do, Acceptance Criteria (Given/When/Then), Figjam, Figma (Desktop/Mobile), Metrics, Notes
- Status: Ready for Tech (product team)
- Design: Auto-save with 3-second toast confirmation ("Billing detail updated")
- UI: Add radio button/selection indicator to each billing detail card; active card visually distinct

**Summary**: Minimal UX feature for kill-pipedrive initiative. Each booking can now explicitly select which billing detail is active. Auto-save with toast confirmation. Wiki page created with full context and acceptance criteria. Ticket structured per standard Linear ticket format and assigned to product team at Ready for Tech status.

---

## 2026-04-23 (Session 16 - Billing Detail Validation feature ticket)

**Source**: Product requirement from user (kill-pipedrive initiative; billing detail completion validation before stage transition)

**Created**:
- Linear ticket PRO-2997: "Validate active billing details completion before 'Buy the Car' stage transition"
- wiki/instafleet-billing-validation.md

**Updated**: wiki/index.md (added instafleet-billing-validation entry under Roadmap Initiatives section)

**Ticket structure**:
- Full Linear ticket with all sections: Description, What we currently do, What to do, Acceptance Criteria (Given/When/Then), Figjam, Figma (Desktop/Mobile), Metrics, Notes
- Status: Ready for Tech (product team)
- Validation: Block stage transition to "Buy the Car" if active billing detail is incomplete
- Error handling: Clear error message listing missing/empty required fields

**Summary**: Data integrity feature for kill-pipedrive booking workflow. Prevents bookings from advancing to "Buy the Car" stage unless active billing detail is fully completed. Wiki page created with full context. Ticket structured per standard Linear ticket format and assigned to product team at Ready for Tech status. Requires Finance/ARM coordination to confirm which fields are required vs. optional.

---

## 2026-04-23 (Session 17 - New roadmap items from CEO priorities)

**Source**: User submission of 4 new features to add to CEO spec list

**Updated**: wiki/roadmap.md, wiki/log.md

**Changes**:
- Added 4 new roadmap items to Quick View table (date: 2026-04-23)
- Created detailed feature sections for each:
  1. **Merge persons & organisations in instafleet** — data model / architecture decision; no orgas exist yet; TBD estimate; pending spec
  2. **soft1 integration with RF & dunning** — integration project; automated payment recovery; TBD estimate; pending spec
  3. **Credit limit in bulk** — per-user approved booking limits to reduce CS verification overhead; TBD estimate; pending spec
  4. **Dunning credit** — already has spec; spec exists but marked for prioritization; TBD estimate; ready for prioritization
- Updated roadmap "Last updated" to 2026-04-23

**Summary**: 4 new high-priority features added to roadmap. 3 need spec work (persons/orgas model, soft1 integration, credit limits); 1 has spec already (dunning credit). All flagged for CEO prioritization conversation.

---

## 2026-04-16 — Raw files added (not yet ingested at time of addition)

**Files added to raw/**:
- `raw/blog/(6) Every feature should earn its place.md` — clipping from Karri Saarinen on product discipline and feature carrying cost
- `raw/instacar/Guarantee Aggrement.md` — product note on instastart quantity lock and change vehicle approval flow
- `raw/instacar/approval-mechanism-ticket.md` — system design ticket for reusable approval mechanism in instafleet

---

## 2026-04-17 — Raw files added (not yet ingested at time of addition)

**Files added to raw/**:
- `raw/instacar/QA Kill Pipedrive.md` — QA Session 1 findings: 2 blockers, 7 non-blocker categories
- `raw/instacar/QA Kill Pipedrive Slack.md` — Greek Slack summary of the same QA session
- `raw/instacar/Premium Changes in Pricing.md` — CGO email + Dimos reply covering 3 bundle components: upfront at booking, monthly charging, commercial overrides

---

## 2026-04-23 — Raw files added (not yet ingested at time of addition)

**Files added to raw/**:
- `raw/instacar/cto-call-instafleet-uk-brief.md` — CTO call brief on instafleet UK Phase 1 tech scope: pages needed, DB requirements, 3 open architecture decisions, and prioritization context for CEO

---

## 2026-04-23 (Session 18 - Full ingest of undigested raw files)

**Ingested**:
- raw/blog/(6) Every feature should earn its place.md
- raw/instacar/Guarantee Aggrement.md
- raw/instacar/approval-mechanism-ticket.md
- raw/instacar/QA Kill Pipedrive.md
- raw/instacar/QA Kill Pipedrive Slack.md
- raw/instacar/Premium Changes in Pricing.md
- raw/instacar/cto-call-instafleet-uk-brief.md

**Created**:
- wiki/instafleet-approval-mechanism.md -- reusable approval ticket pattern; 3 use cases: instastart lock, change vehicle resubmission, commercial overrides
- wiki/bundle-sales-spec.md -- 3-component bundle spec from CGO with Dimos replies; upfront bundle (in progress), monthly charging (pending spec), commercial overrides (approval mechanism)

**Updated**:
- wiki/kill-pipedrive.md -- added QA Session 1 findings: 2 blockers (filters/views, credit validation) and full non-blocker list
- wiki/instacar-uk-launch-spec.md -- added instafleet UK Phase 1 scope from CTO call: pages needed, DB requirements, 3 open tech decisions
- wiki/blog-articles.md -- added 18th article: "(6) Every feature should earn its place" (Karri Saarinen clipping)
- wiki/index.md -- added instafleet-approval-mechanism and bundle-sales-spec to Roadmap Initiatives; updated kill-pipedrive description; updated last updated date

**Summary**: Full retroactive ingest of 7 files spanning 3 days (Apr 16, 17, 23). Two new wiki pages created covering the approval mechanism architecture and the full bundle sales spec. Kill Pipedrive, UK spec, and blog catalog all updated with new material.

---

## 2026-04-24 (Session 19 - Fleet data entry initiative from CFO)

**Source**: fleet-data-entry-initiative-2026-04-24.md (session notes from CFO request)

**Created**:
- wiki/instafleet-fleet-data-entry.md -- full initiative page with three workstreams (permission grant, mass import, export exposure)
- log/24-04-2026.md -- daily work log

**Updated**: wiki/index.md (added instafleet-fleet-data-entry under Roadmap Initiatives)

**Linear tickets created**:
- PRO-3014 (parent) -- Fleet Data Entry - Migrate from Google Sheets to instafleet
- PRO-3015 -- Grant sourcing team permission to edit invoice details in instafleet
- PRO-3016 -- Mass import fleet sourcing data (backfill)
- PRO-3017 -- Expose fleet sourcing fields in fleet export

**All tickets**: Ready for Tech, High priority, assigned to Dimos

**Key insight**: Fields already exist and are editable. Issue is permission-based, not feature build. PRO-3015 is quick win (permission grant).

**Summary**: CFO-mandated initiative to replace Google Sheets workaround with instafleet. Permission issue discovered during planning -- fields already exist. Three parallel workstreams ready for tech team. All tickets at Ready for Tech with High priority.

---

## 2026-05-03

No changes recorded for this date.
---

## 2026-05-04

Created log/03-05-2026.md — no file changes detected for that date.

---

## 2026-05-14 -- Atomic Design ingest

**Ingested**: atomic-design.pdf (Brad Frost, 2016)

**Created**: wiki/atomic-design.md

**Updated**: wiki/index.md (added atomic-design entry under [concepts] section, updated last updated date)

**Summary**: Full read and digest of Atomic Design by Brad Frost. Wiki page covers the 5-level hierarchy with instafleet-mapped examples, the interface inventory workflow, Pattern Lab purpose and key features, the design-systems-not-pages mental shift and its implications for engineer handoff, a ten-point governance framework for long-term maintenance, and all of Frost's key memorable principles. Includes a direct mapping of instafleet's current design tokens and components to Frost's five levels, plus a gap analysis noting absent lineage documentation, under-documented pattern variations, and lack of formal governance.

---

## 2026-05-14 -- Building Mobile Apps at Scale ingest

**Ingested**: Building Mobile Apps at Scale - 39 Engineering Challenges v1.02.pdf (Gergely Orosz)

**Created**: wiki/building-mobile-apps-at-scale.md

**Updated**: wiki/index.md (added building-mobile-apps-at-scale entry under [concepts] section)

**Summary**: Full read and digest of all 39 engineering challenges across 5 parts. Wiki page is structured for a product designer: each challenge has key insight, tradeoff, and product implication in scannable table format. Notable product implications captured: IAP limitations (no cancel/refund tooling), forced upgrade as a strategy requiring early investment, binary distribution as an irreversible constraint, the long tail of old app versions as a planning factor, analytics certification process to prevent metric drift, performance budgets and why APMs are less useful on mobile than backend, and cross-platform tradeoffs (Flutter, React Native, KMM). Includes a section of cross-cutting mental models directly applicable to product decisions at instacar.
