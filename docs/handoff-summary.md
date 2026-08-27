# White-Label Pro Profile Page — Handoff Summary

**For:** Chris Mejia / Aash Srikar (product)
**From:** Lauren Palma (design)
**Due:** 2026-08-27
**Full context:** [project-context.md](./project-context.md)
**Updated:** 2026-08-27 — corrects the 2026-08-24 version below on delivery model and booking widget placement; see the notes inline.

## Problem

Pros won't drive traffic to their marketplace profile because a visitor there can get poached by a competing provider also listed on the page. Separately, Reserve with Google's only remaining integration lane requires a landing page that meets Google's eligibility rules — the current marketplace profile fails several of them (services, address, and Book all below the fold on mobile).

**Corrected 2026-08-27:** this is **not** a Yourgi-hosted page a pro presents as their own (the 2026-08-24 framing below). It's an **embeddable booking widget/section** a pro drops into their own existing business website (e.g. `updogdenver.com`) — their domain, their design, their site. Yourgi supplies the booking component; the pro's site stays theirs. See `project-context.md` §1 and §6 for what this changes.

## Deliverables

**Current sales-facing prototype:** [`demo/sales-widget-demo.html`](../demo/sales-widget-demo.html) — a single, git-committed, self-contained HTML file (no build step, no server) that a seller opens directly in a browser to pitch a pro. Built from the **Marisol Vega — Mobile Dog Grooming** artifact (a real, fully responsive single-pro marketing site), it lets a seller:
- Switch between the three style presets — Earthy, Modern, Luxury (accent color, neutral family, typeface, corner radius per Section 6's four-variable cap)
- Type any hex code into an **Accent color** field to preview a pro's own brand color live, layered on top of whichever style preset is active — scoped to the booking widget only, not the surrounding page
- Click "Book Now," which always opens the booking flow as a **popup** (see Decisions below)

**Internal QA comp (separate, not this file):** [Inline Book Widget](https://claude.ai/code/artifact/c2fe7103-10a3-4fb2-a2f7-dedf5bb76e46) — a BARK! Denver-based device-frame comp with extra debug toggles (viewport, widget-unavailable state, page-deactivated state) used for internal review, not for pitching pros. Progressive 6-step flow: Service → Date & Time + Pets → Add-ons → Your Info → Payment → Review, ported from the real embedded booking widget's flow logic where confirmed against that codebase.

**Superseded/frozen (2026-08-27):** the original four style-option artifacts — Trailhead (Earthy), Meridian (Modern), Aldine (Luxury), and the home-based variant Reyes Dog Walks — are frozen at their last-applied state and are no longer the active deliverable. The Inline Book Widget artifact above absorbed their style-switching purpose; the sales demo file is now the pitch-ready output.

## Decisions locked 2026-08-24 (see corrections below)

- **Trust marks:** keep all three — "Book Now powered by Yourgi," "Yourgi Pro" badge, "Covered by the Yourgi Guarantee." Guarantee copy should describe the mechanic only ("if it's not right, we make it right"), no specifics — **flag for legal/brand review before ship**, since remedy terms and eligibility aren't documented.
- ~~**Booking widget placement:** inline in the page, never a modal/popup.~~ **Reversed 2026-08-27:** the booking widget now opens as a popup/modal from a "Book Now" button in all cases — it is never rendered inline by default. This is a deliberate second reversal (inline → popup was the 08-24 call; popup is now standing direction again), confirmed while reviewing the Marisol Vega placeholder site. Apply this to any new comp going forward.
- **Style palette:** none of the three options reuse Yourgi's own brand colors (Sunshine Yellow/Spot Black/Bone) — deliberate, so the widget doesn't read as marketplace chrome.

## Open for product

- **Indexability** (Open Question 1 in project-context.md) — reframed by the 08-27 delivery-model correction: if the widget lives on a page the pro already owns and indexes, this may no longer be Yourgi's call to make.
- **Embed mechanism** — script tag, iframe, copy-paste block, or CMS plugin? Needs Chris Mejia / Aash Srikar and an eng estimate.
- **Reserve with Google "above the fold" compliance** — now depends on what a pro puts above the widget on their own page, which Yourgi doesn't control. Needs Chris Mejia / Aash Srikar.
- **Style-matching intent** — are the three style presets meant to approximate a pro's existing site, or a fixed set picked regardless of fit? Needs Chris Mejia / Aash Srikar or a design call.
- **Success metrics** — no conversion target, Reserve with Google adoption goal, or pro opt-in rate defined yet.
- **Launch scope** — whether every existing Pro is eligible at launch or this rolls out to a subset first.
- **Add-ons step** in the booking widget is a speculative interpretation (BARK's live profile has no Add-Ons category today) — flag before treating as confirmed behavior.

## Known bug (pre-existing, not introduced by this work)

The Marisol Vega source's booking-unavailable fallback state still shows "BARK! Denver" copy and phone number instead of Marisol Vega's own — carried over from whatever that artifact was cloned from. Flag before this ships anywhere real.

## Cleaned up

Three superseded explorations were removed from the artifact gallery as part of the 2026-08-24 handoff: an early "Highbeam" style option (rejected for reusing Yourgi's own brand palette), two popup-over-the-page booking widget comps (superseded at the time by the inline pattern — since reversed again, see Decisions above), and "Overlook," a richer editorial full-page layout exploration.
