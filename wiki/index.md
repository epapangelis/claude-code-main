# Wiki Index -- Table of Contents

A personal knowledge base for Dimos: product work, consulting, writing, and personal projects.

---

## Roadmap & Planning

- [[roadmap]] -- centralized tracker of all feature requests, projects, and work items organized by date requested; single source of truth for what's been asked and its status

---

## [instacar]

Pages related to my Head of Product role at instacar greece.

### Company and Context

- [[instacar]] -- Greek automotive company, two business lines (used car sales + leasing), serving B2C and B2B; competitors include Flexcar, Spotawheel; tech stack includes Linear, GA, Clarity, n8n; growth stage; multiple workspaces (Greece, instaride/kineo, UK planned)
- [[users-b2c]] -- B2C individual buyers/lessees (28-55, price-sensitive, high trust needs, often first-time online car buyers, need inspection reports, transparent pricing, easy comms)
- [[users-b2b]] -- B2B small Greek companies (owners/office managers, fleet needs, efficiency-focused, value invoicing and account management)

### Products

- [[customer-facing-platform]] -- main buyer-facing app (search/discovery, vehicle detail, purchase/lease funnel, trust signals); customers submit financial docs via my.instacar.gr portal or email reply (n8n); UK expansion planned
- [[instacar-customer-faqs]] -- bilingual (Greek/English) FAQ library for 14 vehicle categories (by size, fuel, transmission, tier); standardizes "like-new" positioning, inspection rigor, payment flexibility; targets Sell Vehicles landing page SEO
- [[instafleet]] -- instacar's internal operational backbone (CRM, fleet lifecycle, bookings, contracts, ARM ticketing, subscription management); multi-workspace (Greece, instaride/kineo, UK planned); replacing Pipedrive and Trello; includes Sales, CS, and ARM team usage
  - [[design-system]] -- instafleet design tokens and visual system: colors, typography, shadows, buttons, tabs, fields, lists, cards, and email composer components
  - [[navigation]] -- global sidebar structure, global search, and filter system across all instafleet boards
  - [[booking]] -- sales pipeline from Prelead to Buy the Car; Kanban and list views, booking ticket detail, and "Add New Booking" modal
  - [[subscriptions]] -- CS workspace for active subscription contracts: list view, lifecycle stages, and detail page with 9 tabs (Products, Delivery/Return, Payment, Drivers, Docs, Fees, Members, Linked Subs, History)
  - [[instafleet-subscriptions]] -- CS team usage: subscription list and detail with tabs for Delivery & Return, Communication, Status, Drivers, Documents, Changelog
  - [[arm]] -- AR&M module: vehicle repair ticket list, ticket detail, work orders, and financial approval flow
  - [[unified-view]] -- internal email hub: shared mailboxes, compose, templates, mass actions, custom filtering, and per-contact communication history

### Roadmap Initiatives

- [[kill-pipedrive]] -- migrate Sales team fully into instafleet; v1 in QA (April 2026): 13 features shipped; QA Session 1 found 2 blockers (filters/views, credit validation) and a list of non-blockers; v2 covers labels, filter views, lost/won tracking
- [[instafleet-approval-mechanism]] -- reusable system-triggered "Needs Approval" ticket pattern; first use case: instastart quantity lock (approver: Zoi); also covers change-vehicle resubmission and commercial override routing; async-friendly design
- [[bundle-sales-spec]] -- 3-component bundle spec from CGO: upfront bundle at booking creation (in progress), monthly charging for existing customers (pending spec), commercial overrides via approval mechanism
- [[defleet]] -- define fleet-end-of-life process and team handoffs (Ops, Sales, ARM, Finance); system-level "defleeted" stage and "fordefleet" reservation type already exist; workflow formalization in progress
- [[carswaps]] -- CS-initiated vehicle swap flow inside instafleet; trigger button on subscription detail + full-screen modal with product carry-over, proration logic, and bidirectional subscription linking; part of kill-pipedrive; Linear project empty pending Finance validation
- [[instafleet-billing-detail-selection]] -- allow users to select which billing detail is active for a booking, with auto-save and toast confirmation; minimal UI change for booking management; PRO-2996
- [[instafleet-billing-validation]] -- validate that active billing detail is fully completed before allowing booking to advance to "Buy the Car" stage; prevents incomplete data submission; PRO-2997
- [[n8n-workflow-automation]] -- email-triggered automation for financial document collection (drive@instacar.gr); processes only replies to booking confirmation threads with attachments; uploads docs to instafleet via API, updates booking status to 3 (docs uploaded), notifies agents via Slack #n8n; target: 50-100+ emails/day, under 2 min processing
- [[instafleet-fleet-data-entry]] -- migrate fleet sourcing data from Google Sheets into instafleet with three coordinated changes: grant sourcing team permission to edit invoice details (permission-based issue, not feature build), mass import tool for historical backfill, expose fields in fleet export; CFO mandate, high priority, Ready for Tech

### Expansion

- [[instacar-uk-launch-spec]] -- Phase 1 UK launch (April 2026 kickoff): /buy + sell-to-us (Instatrade) verticals only; "instacar Approved Used Cars" branding; 10-point instacar Promise; GBP/miles localisation; separate instafleet workspace; project lead: Alexandros Chatzisavvas

### Technical Reference

- [[instacar-api]] -- API docs (swagger v1.0), endpoints for bookings, subscriptions, sales, leasing, integrations
- [[subscriptions-data-model]] -- subscription entity schema: ID formats (SUB/SUBP/SUBT), core fields, delivery fields, vehicle status fields (Stage, Availability Status, Reservation Type), customer journey tags (new_customer, returning_customer, etc.), location values (instacar-hq, anoixh, pigasou, thessaloniki-airport)
- [[instacar-offer]] -- personalised offer sent by email before contract signing; customers land on my.instacar.gr to upload documents (stub)

### Linear ticket structure
# Description

[_Short description of the task or issue, including necessary background information & context_]

# What we currently do

[_Short description of current implementation, screenshots/looms, and relevant content clearly illustrating the issue_]

# What to do

[_Detailed description of what is to be done by the engineering team to complete the task. Be precise, provide information, critical documents, context, relevant tickets, and/or images of other relevant points_]

# Acceptance Criteria

**Given**

**When**

**Then**

# Figjam

[_A flowchart of the desired implementation should always be here_]

# Figma

**Desktop**:

**Mobile**:

# Metrics

[_Metrics to be used to measure the success and impact of the desired implementation_]

## Notes

[_Comments, user stories, resources, tools, or other less critical information and input needed to that may assist the desired implementation_]

---

## [blog]

Pages related to my personal blog -- writing, publishing, and audience-building.

- [[blog-articles]] -- catalog of all 17 blog articles with key takeaways; topics: product/instacar stories, velocity/delivery philosophy, behavioral analytics, mindset, technical tools
- [[blog-microsoft-clarity-framework]] -- full behavioral analytics framework: heatmaps, session recordings, smart events, advanced filtering, MCP integration, 3-week setup guide; basis of the Microsoft Clarity case study
- [[blog-learning-system]] -- multi-LLM learning framework: precision prompt → ChatGPT/Perplexity/Gemini/Grok → NotebookLM → mind map; designed to avoid single-source bias
- [[blog-technical-tools]] -- technical implementations: BoldieBot (GA4 → Slack daily cron script) and Prophet forecasting/anomaly detection guide

---

## [personal]

Pages related to hobbies, personal projects, and side experiments.

---

## [concepts]

Cross-context reusable frameworks and mental models that apply across instacar, blog, and personal work.

---

## Daily Logs

Work summaries are tracked in `/log/` with daily files (DD-MM-YYYY.md format). These capture what changed each day and serve as a quick reference without reading full wiki/log.md.

---

## Navigation rules for Claude

1. Read this file first on every session.
2. Use the context tags [instacar], [blog], [personal] to scope your work.
3. Never read all wiki pages at once. Follow links from the relevant section only.
4. When adding a new page, append it to the correct section here with a one-line description.
5. Keep descriptions short -- one line per page is enough.

---

**Last updated**: 2026-04-30
**Source documents**: instacar_claude_project_instructions.md, instafleet_team_usage.md, PRD_n8n_Workflow_Automation_instacar_v2.pdf, instacar-uk-launch-spec.md, swagger.json, subs export.csv, subs report.csv