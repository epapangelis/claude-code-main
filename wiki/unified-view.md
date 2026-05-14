# Unified View

**Summary**: Instafleet's internal email hub, used by all teams (Sales, CS, AR&M) to manage shared company mailboxes, compose emails, and track communication history per contact.

**Sources**: raw/instafleet/Unified View - instafleet/ (8 screenshots)

**Last updated**: 2026-04-29

---

## Overview

Unified View is the communication centre of [[instafleet]]. It aggregates two shared company email addresses into a single inbox-style interface, accessible by all teams. It replaces ad-hoc email clients for internal agent workflows.

There are two sub-sections in the sidebar:
- **Mailboxes** — the main inbox and email list
- **Templates** — management of reusable email templates

---

## Mailboxes

### List view

The main view shows all emails in an inbox-style list. Each row displays:
- Sender name (linked contact)
- Subject line + body preview
- Three manually assigned tags (see **Tagging** below)
- Timestamp

A **Compose** button at the top opens the Send Message panel (see **Composing emails**).

### Tagging

Every email can carry three tags, all manually assigned by agents:

| Tag type | Purpose | Example |
|---|---|---|
| **Status** | Handling state of the email | Pending |
| **Assignee** | Agent the email is assigned to | Agent name |
| **Priority** | Importance flag | Not Priority (default) / Priority |

"Not Priority" is the default state for all emails that have not been explicitly flagged as priority.

### Individual email view

Selecting an email opens the full email content. The layout includes:

- **Top action bar**: Move to Inbox · Assign to Specific Person · Mark as Read · Not Priority
- **Email body**: full content displayed in the centre
- **Right panel** — contact context:
  - Linked contact details
  - Linked subscription
  - **History**: a log of events on this email — priority changes and assignment changes

### Mass actions

Multiple emails can be selected via checkboxes. The same actions available on individual emails apply in bulk:
- Move to Inbox
- Assign to Specific Person
- Mark as Read
- Not Priority

### Filtering

The funnel icon opens a **Set Communication Filters** modal. Filters include at minimum a date range. Filtered views can be submitted to narrow the email list.

---

## Composing emails

The **Compose** button opens a **Send Message** panel on the right side of the screen. Fields:
- **To** — recipient email address
- **Subject**
- **Body** — rich text editor (bold, italic, underline, strikethrough, lists, etc.)
- **Template** — optional: opens the Send Email Template modal

### Send Email Template modal

When inserting a template, agents select:
1. **Template** — dropdown of available templates
2. **Language** — e.g. Greek

The body is pre-filled with the selected template content. Agents can edit before sending.

---

## Templates

The **Templates** sub-section is a separate management page. It lists all reusable email templates with the following columns:

| Column | Notes |
|---|---|
| Template ID | Internal identifier (UUID) |
| Template Name | Human-readable name (in English) |
| Created At | Date of creation |
| Created By | Agent who created the template |
| Status | Active / Inactive |

### Individual template view

Each template has:
- **Template Content** section:
  - Subject (GR): supports dynamic variables, e.g. `[VEHICLE_PLATE]`
  - Body (GR): rich text editor with the template email body (in Greek)
- **Template Details** sidebar:
  - Template Name
  - Created At
  - Created By
- Actions: **Reset All** (revert changes) · **Edit**

Templates are primarily written in Greek and are created by agents or the Dreamteam.Agents account.

---

## Related pages

- [[navigation]]
- [[subscriptions]]
- [[booking]]
- [[arm]]
