# White-Label Pro Profile Page

A white-label version of Yourgi's Pro marketplace profile page, hosted at a
`yourgi.com` path, that a provider can present as their own business page —
three style variants over the same profile data, Book as the only action, and
built to satisfy Google's Reserve with Google landing-page policy. Currently in
the mockup/design phase; no application code exists in this repo yet.

## Commands

Not applicable yet — this is a design deliverable, not a codebase. Once
implementation starts, replace this section with the real build/test/lint/dev
commands.

## Layout

- `docs/project-context.md` — problem statement, ICP, requirements, open
  questions, gaps. Read it before scoping new work.
- Nothing else exists yet.

## Conventions

- Reserve with Google's "above the fold" rule is evaluated at 390×844 mobile —
  treat that viewport as the binding layout constraint, not desktop.
- Style variation is capped at four variables: accent color, neutral family,
  typeface, corner radius. Don't add a fifth without checking with product.
- Book is the only CTA on this page. No contact, message, phone, or email
  affordances.
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
