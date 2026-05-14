# Building with AI: How the Product Team Should Work
**Dimosthenis Avgeris — Head of Product, instacar**

---

## The Tools We're Using

Two AI tools. Different strengths. Both in your workflow.

- **Claude Code** — terminal-first, composable, 1M token context
- **Antigravity** — visual IDE, agent-first, browser subagent (Google DeepMind)

---

## Claude Code: Terminal + VS Code Extension

Your codebase is the context. The terminal is the interface.

- Works directly in VS Code — no context switching
- Reads your files, your tickets, your design system
- The extension is the game changer: inline chat, full file awareness

---

## Antigravity: Built for PMs and Designers

Agent-first. No terminal needed.

- Built on VS Code with Gemini 3.1 Pro
- Multi-agent parallel execution: one writes, one tests UI, one refactors — simultaneously
- Designed for people who don't live in the terminal
- Purpose-built for product managers, designers, solopreneurs

---

## The Knowledge System: LLM Wiki

Knowledge compounds. You stop researching the same thing twice.

- `raw/` — immutable source documents, never modified
- `wiki/` — compressed, interlinked knowledge maintained by Claude
- Outputs — tickets, wireframes, decisions, daily logs

---

## How Ingestion Works

Feed it once. Reference it forever.

1. Add a source to `raw/`
2. Claude summarizes key takeaways
3. You discuss and align
4. Claude creates wiki pages + cross-links
5. Index and log updated automatically

---

## Context Scoping

The right context every time. Not all context every time.

- `[instacar]` — product work and decisions
- `[blog]` — writing frameworks and publishing
- `[personal]` — side projects and experiments
- `[concepts]` — reusable frameworks across all contexts

Claude only reads what's relevant per question.

---

## Linear + MCP: The Connection

MCP turns Linear into a tool Claude can actually use.

- **MCP** (Model Context Protocol) connects Claude Code directly to Linear
- Read, create, and update tickets without copy-pasting
- Full ticket context flows both ways: wiki → ticket, ticket → wiki
- No more switching tabs to fetch issue details

---

## PM Skills Built In

Frameworks you know — now executable in one command.

- `/user-story` — Mike Cohn format + Gherkin acceptance criteria
- `/prd-development` — full PRD from problem to success metrics
- `/jobs-to-be-done` — structured JTBD with pains and gains
- `/user-story-splitting` — break epics into deliverable stories

You direct. Claude structures.

---

## The Ticket Template

Every ticket is a complete document, not a placeholder.

- **Description** — background and context
- **Current State** — what exists today
- **What to Do** — precise engineering instructions
- **Acceptance Criteria** — Given / When / Then
- **FigJam** — flowchart of implementation
- **Figma** — desktop and mobile designs
- **Metrics** — how we measure success
- **Notes** — supporting resources

---

## Live Example: INS-4808

From a vague ask to a fully specified ticket.

**The ask:** "We need calendar links in the ARM service appointment email"

**The output (INS-4808):**
- Google Calendar URL format with all dynamic parameters
- Apple .ics file spec generated server-side
- Data table: which field comes from where in the ARM ticket
- UTC offset logic for Greek timezone
- Edge case: end time defaults to start + 1 hour
- Delivery method decision: URL over attachment (avoids email client rendering issues)
- Two GitHub PRs linked, now in QA

This is what wiki context + PM skills + ticket template produces.

---

## From Figma to Machine-Readable

The design system becomes an instruction manual for AI.

1. Export design tokens from Figma (instafleet design system)
2. Structure them into a `DESIGN.md` file
3. Drop `DESIGN.md` into the project root
4. Claude reads it before generating any UI

---

## What DESIGN.md Contains

Everything a designer knows — machine-readable tokens, not narrative.

**Real example from instafleet:**

**Colors**
- Brand blue: `Primary/Blue 500 = #3B82F6`
- Button hover: `Primary/Blue 600 = #2563EB`
- Error state: `#F87171` (Red 400)
- Success state: `#22C55E` (Green)

**Typography** — Geologica font family exclusively
- Body text: `M 14` (Regular, 14px, 100% line height)
- Labels: `SM 14` (Medium, 14px)
- Field titles: `B 14` (SemiBold, 14px)

**Buttons** — 4 types × 4 states (no more design arbitrariness)
- Filled: bg `#3B82F6`, hover `#2563EB`, pressed `#1654DD`, disabled `#CBD5E1`
- Ghost: border `#3B82F6`, hover bg `#EFF6FF`
- Link: text only, state-driven color
- Plus error modifier for destructive actions

**Fields** — all inputs share identical specs
- Width: 223px (forms) or 230–400px (composite with title)
- Height: 40px
- Border: Gray 300 default, Blue 300 focused
- Error border: Red 200, error text: Red 400

---

## Prompt → High-Fidelity Wireframe

First draft in minutes. Designer reviews decisions, not syntax.

**Example: INS-4808 "ARM ticket confirmation email with Add to Calendar"**

**Prompt given to Claude:**
> "Design the service appointment confirmation email for AR&M using the instafleet design system. Include recipient field, appointment details, and an 'Add to Calendar' button. Follow our email component specs."

**Claude output (guided by DESIGN.md):**
- Recipient field: 223px width, 40px height, Geologica Regular 14px, Gray 300 border, Blue 300 when focused
- Button: 32px height, filled style, `#3B82F6` bg, `#2563EB` hover, text in white, Geologica Regular 14px
- Section headers: `B 16` (SemiBold Geologica, 16px)
- Body text: `M 14` (Regular Geologica, 14px)
- Status badge: uses Color Coding (e.g. Green 600 `#00B341` for confirmed)

**Result:** Pixel-perfect consistency with live product, zero design rework. The wireframe matches what engineers will build because the spec is atomic and reproducible.

---

## Why This Matters: Real Impact

**Without design tokens in a file:**
- Designer says "use the primary blue"
- Claude has to look at Figma (can't access it), or engineer looks up the hex code from a design doc
- Email composer gets `#2563EB` instead of `#3B82F6` because someone looked at the wrong screenshot
- Inconsistency compounds across modules (booking, subscriptions, ARM)

**With DESIGN.md (877 lines of real tokens):**
- Claude reads color definitions before generating the email wireframe
- Buttons always use the correct `#3B82F6` → `#2563EB` → `#1654DD` progression
- Every component spec is atomic: field widths are always 223px, button heights always 32px, font is always Geologica
- New designers onboard by reading one file instead of reverse-engineering Figma
- Engineers stop guessing. QA stops flagging "button color wrong" issues.

This isn't about pretty wireframes. It's about **making consistency a system property, not a willpower problem.**

---

## The Wiki Works at Scale

Proof: How Booking → Subscriptions → AR&M flows through one knowledge graph.

When you search the wiki for "subscription delivery", you discover:
1. **Booking** module — where sales begin (creation stage, financing validation)
2. **Subscriptions** module — where lifecycle tracks 8 statuses (Created → Delivery → Active → Renewal → Return → Ended/Cancelled)
3. **AR&M** module — where maintenance + accidents + repairs are logged against that subscription

Each module documents its own list view, filters, detail pages, and field structure. But because they're interlinked with `[[wiki-links]]`, Claude understands the full customer journey without rereading the same facts three times. A new team member onboards by reading one structured wiki page instead of six scattered Figma screens and tribal knowledge.

This is the compounding effect: **first ask takes research time. Next ask is instant.**

---

## The Full Stack

Everything we're working with, in one view.

| Layer | Tool | Real Example |
|---|---|---|
| Agentic IDE | Claude Code (terminal + VS Code extension) | Terminal edit → git commit → test |
| Visual IDE | Antigravity | Multi-agent parallel UI/test/refactor |
| Tickets | Linear + MCP | Read INS-4808, update its status, link related issues |
| PM Frameworks | `/user-story` `/prd-development` `/jobs-to-be-done` | Turn one idea into acceptance criteria |
| Design | Figma tokens → DESIGN.md → wireframes | Colors `#3B82F6`, typography `M 14`, buttons via token lookup |
| Knowledge | `raw/` → `wiki/` → daily logs | booking.md links → subscriptions.md links → arm.md |

---

## How Knowledge Compounds

The system gets smarter the more you use it.

- **Month 1** — First ingests, first tickets, first design outputs
- **Month 2** — Patterns emerge, wiki cross-links, no repeated research
- **Month 3** — New team member onboards using the wiki in one session
- **Month 6** — Every decision has context. Every ask has precedent.

---

## Adoption Path

Four phases. Start small.

1. **Install** — Claude Code + VS Code extension. Set up `raw/` + `wiki/`.
2. **Ingest** — Add your first project source. Run your first ticket.
3. **Design** — Extract Figma tokens. Create `DESIGN.md`. Generate first wireframe.
4. **Scale** — Add Antigravity for visual agentic work. Add PM skills.

---

## Start Here

Pick one project. Add one source. Let's run the first session together.

> "The best knowledge system is the one that makes your next decision faster than your last."
