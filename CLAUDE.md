# White-Label Pro Profile Page

A white-label booking widget/section that a provider embeds into their own
existing business website (their domain, their design — e.g. updogdenver.com,
not a yourgi.com-hosted page) — three style variants over the same profile
data, Book as the only action, and built to satisfy Google's Reserve with
Google landing-page policy. Currently in the mockup/design phase; no real
application code exists yet — the one HTML file in this repo is a static,
self-contained sales/pitch prototype, not a build artifact.

## Commands

Not applicable yet — this is a design deliverable, not a codebase. Once
implementation starts, replace this section with the real build/test/lint/dev
commands. To view the prototype: open `demo/sales-widget-demo.html` directly
in a browser (no server needed).

## Layout

- `docs/project-context.md` — problem statement, ICP, requirements, open
  questions, gaps. Read it before scoping new work.
- `demo/sales-widget-demo.html` — the sales-facing prototype: a single
  self-contained HTML file (no build step; large due to embedded photos, ~1MB)
  that sellers open locally and use to pitch pros. Built from the **Marisol
  Vega — Mobile Dog Grooming** claude.ai artifact (a real, fully responsive
  single-pro marketing site — hero/gallery/testimonials — not a device-frame
  toolbar comp), with a slim top bar added on top of it: a **Widget style**
  switcher (Earthy/Modern/Luxury) plus an **Accent color** field where a
  seller types the pro's own brand hex to preview it live. Picking a style
  resets the accent hex to that style's own default color; typing a hex
  overrides it on top of whichever style is active. The override applies to
  the booking widget only — the surrounding page's own accent (hero CTA, etc.)
  is a fixed example and does not change. "Book Now" always opens the booking
  flow as a popup (matches the standing placement decision below). This file
  has no viewport toggle (the page is genuinely responsive — resize the
  window instead of simulating a device frame). The older BARK! Denver-based
  comp (device-frame toolbar, Widget/Page QA toggles) was an earlier,
  since-superseded source for this file — don't resurrect it as the basis for
  sales-demo edits. The claude.ai-hosted "Inline Book Widget" and "Marisol
  Vega" artifacts remain separate internal comps and are not this file — don't
  conflate them or assume edits to one apply to the other.
  **Known pre-existing bug carried over from the Marisol Vega source, not
  introduced here:** the widget's fallback/unavailable state still shows
  "BARK! Denver" copy and a BARK phone number (`tel:+13035550187`) instead of
  Marisol Vega's own — flag before this ships anywhere real.

## Conventions

- Reserve with Google's "above the fold" rule is evaluated at 390×844 mobile —
  treat that viewport as the binding layout constraint, not desktop.
- Style variation is capped at four variables: accent color, neutral family,
  typeface, corner radius. Don't add a fifth without checking with product.
- Book is the only CTA on this page. No contact, message, phone, or email
  affordances.
- The booking widget opens as a popup/modal from a "Book Now" button — it is
  never rendered inline in the page by default (reversed 2026-08-27; was
  inline-only before that). Apply this to any new comp or prototype.
- Follow the `yourgi-brand` skill for voice, copy, and visual system; don't
  restate its rules here.

Project context and open decisions: docs/project-context.md — read it before
scoping new work.

## Working agreement

- Lead with the change or the answer. No preamble, no recap of what you just did.
- After edits: file paths and one line each on why. Nothing more unless asked.
- Targeted reads only; delegate broad "where is X" or "how does Y work"
  questions to the `scout` subagent.
- More than two files, or a vaguely-phrased request: plan first, wait for
  approval before editing.
- Before anything irreversible (force push, delete, rewrite history, discard
  uncommitted work): stop and confirm, every time.
- When a durable fact about this project surfaces (a real command, a
  constraint, something corrected), propose one line for this file rather than
  letting it live only in conversation.

## Compact instructions

Keep: which style options exist and their current variable values (accent,
neutral, typeface, radius); decisions made on the three trust marks
(Requirement 8) and why; any Open Question or Gap from
`docs/project-context.md` that got resolved, and what it resolved to; current
task state; any real command discovered once implementation starts.

Drop: full brief text (it lives in the source file and project-context.md),
raw tool output, exploration that led nowhere.
