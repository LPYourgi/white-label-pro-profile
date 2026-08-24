# White-Label Pro Profile Page — Handoff Summary

**For:** Chris Mejia / Aash Srikar (product)
**From:** Lauren Palma (design)
**Due:** 2026-08-27
**Full context:** [project-context.md](./project-context.md)

## Problem

Pros won't drive traffic to their marketplace profile because a visitor there can get poached by a competing provider also listed on the page. Separately, Reserve with Google's only remaining integration lane requires a landing page that meets Google's eligibility rules — the current marketplace profile fails several of them (services, address, and Book all below the fold on mobile). This page is a walled-off, Yourgi-hosted page a pro can present as their own business page, with Book as the only action, built to pass Google's rules.

## Deliverables

**Three style options**, same content model, differing only in accent color, neutral family, typeface, and corner radius:

- [Trailhead](https://claude.ai/code/artifact/2052dee8-7633-418a-b636-a215bf2a0633) — Earthy (forest green, warm stone, slab serif)
- [Meridian](https://claude.ai/code/artifact/b7716885-2998-47ce-a7cd-eea9910cfb67) — Clean/Modern (teal, cool neutrals, geometric sans)
- [Aldine](https://claude.ai/code/artifact/039ee23d-b96a-4dcd-9ca7-b789f74979d2) — Luxury/Premium (deep wine, ivory, refined serif)

**Home-based variant:** [Reyes Dog Walks](https://claude.ai/code/artifact/fa9a1592-ff42-44d7-8999-3abdc8b95ff3) (Aldine style) — shows the conditional layout when a pro has no street address.

All four verified above the fold at 390×844 mobile and at desktop width, with services, prices, and Book all visible without scrolling.

**Booking widget pattern:** [Inline Book Widget](https://claude.ai/code/artifact/c2fe7103-10a3-4fb2-a2f7-dedf5bb76e46) — the widget lives directly in the page layout (sticky sidebar on desktop, under the header on mobile), not a popup or modal. Progressive 4-step flow: Service → Date & Time + Pets → Add-ons → Review, matching the real embedded booking widget's flow logic (date-picking mode, pet form, login) where confirmed against that codebase.

## Decisions locked 2026-08-24

- **Trust marks:** keep all three — "Book Now powered by Yourgi," "Yourgi Pro" badge, "Covered by the Yourgi Guarantee." Guarantee copy should describe the mechanic only ("if it's not right, we make it right"), no specifics — **flag for legal/brand review before ship**, since remedy terms and eligibility aren't documented.
- **Booking widget placement:** inline in the page, never a modal/popup — confirmed direction after two earlier popup explorations were tried and rejected.
- **Style palette:** none of the three options reuse Yourgi's own brand colors (Sunshine Yellow/Spot Black/Bone) — deliberate, so the page doesn't read as marketplace chrome.

## Open for product

- **Indexability** (Open Question 1 in project-context.md) — should this page be search-engine indexable? Affects SEO/duplicate-content handling relative to the marketplace profile and whether pet parents can find it outside the marketplace.
- **Success metrics** — no conversion target, Reserve with Google adoption goal, or pro opt-in rate defined yet.
- **Launch scope** — whether every existing Pro is eligible at launch or this rolls out to a subset first.
- **Add-ons step** in the booking widget is a speculative interpretation (BARK's live profile has no Add-Ons category today) — flag before treating as confirmed behavior.

## Cleaned up

Three superseded explorations were removed from the artifact gallery as part of this handoff: an early "Highbeam" style option (rejected for reusing Yourgi's own brand palette), two popup-over-the-page booking widget comps (superseded by the inline pattern), and "Overlook," a richer editorial full-page layout exploration.
