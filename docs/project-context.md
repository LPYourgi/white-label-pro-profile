# Project Context: Pro Profile Page (White-Label)
**Date:** 2026-08-24
**Source:** Written brief — "Pro Profile Page Mockup Brief" (draft, dated 2026-08-21), by Lauren Palma (design), for Chris Mejia / Aash Srikar (product), due 2026-08-27.
**Version:** 1.5 — cleanup pass 2026-08-27: reconciled this doc, `handoff-summary.md`, and the project's memory with the current state after two more decisions landed the same day — the booking-widget-placement reversal (inline → popup, see the "Decisions: booking widget placement" section) and the move of the sales-facing prototype off the BARK! Denver comp onto the Marisol Vega artifact (see the new "Sales-facing prototype" section near the end). No new open questions were resolved in this pass; it's a consistency cleanup, not new product decisions.

**Version 1.4 note (2026-08-27):** the delivery model was wrong in v1.3. This is **not** a page Yourgi hosts at a `yourgi.com` path — it's an embeddable booking widget/section that a pro drops into their own existing website (e.g. `updogdenver.com`), which keeps its own domain, brand, and design. See Section 6 for what changed and what's open as a result. Prior version's resolved-questions history (1.3, 2026-08-24) is preserved below for reference.

**Version 1.3 note (2026-08-24):** trimmed for PM handoff; see [handoff-summary.md](./handoff-summary.md) for the one-page version. Resolved Open Questions 1, 2, 4, 5 on 2026-08-24 (due date, Ariel alignment, trust marks, third style direction). Third style direction was revised same-day: an initial "Bold/Confident" pass built directly from Yourgi's own brand palette (Sunshine Yellow, Spot Black, Bone) was rejected on review for reusing Yourgi's own look on a page whose whole premise is that it must not read as Yourgi/marketplace chrome. Replaced with a Luxury/Premium direction (deep wine accent, ivory neutrals, refined serif) that doesn't borrow Yourgi's palette.

---

## 1. Problem Statement
Pros will not spend their own money or effort driving traffic to a marketplace profile page, because a visitor there can get distracted and book a competing provider instead ("great, now I'm directing somebody to a place where they can get distracted and pick an alternative dog walker"). Separately, Reserve with Google's only remaining integration lane — Appointments Redirect — requires a merchant landing page that meets Google's eligibility rules, and the current marketplace profile page fails several of them today (see Pain Points). Yourgi needs a booking experience a pro can embed directly into their **own** existing business website — no marketplace chrome, no cross-sell — that also clears Google's landing-page bar so the Reserve with Google "Book online" button can appear for eligible pros.

**Corrected 2026-08-27:** earlier framing described this as "a page Yourgi hosts" that a pro presents as their own. That's wrong — the target is an **embeddable widget/section** a pro adds into their existing site (example: [updogdenver.com](https://www.updogdenver.com/), a fully independent dog-walking business site with its own domain, brand, and layout — nothing Yourgi-hosted about it today). The pro's site stays theirs; Yourgi supplies the booking component that drops into it. This changes the technical constraints in Section 6 and reopens the Reserve with Google compliance question — see Open Questions.

## 2. ICP (Ideal Customer Profile)
**Side:** Providers (primary)

Pros who already have a Yourgi Pro marketplace profile with services and prices filled in, and who are being asked whether they want a page they can present externally as their own business page rather than a marketplace listing. They range from home-based individuals with residential addresses to businesses with a commercial address and a Google Business Profile. Only the latter group is currently eligible for Reserve with Google (it requires a Places ID and a commercial address; each booking also needs the pro to accept it before it's confirmed).

**Cross-side impact:** Pet parents who land on a given pro's white-label page get a deliberately walled-off experience: no marketplace nav, no cross-sell copy, no path to another provider, and booking available only through the embedded widget (Requirement 3). Sign-in returns them to this same provider's page, not the marketplace (Requirement 6). This is intentional per the brief, not a side effect. What's unresolved: whether the page is search-indexable — if it is, pet parents could discover a pro's white-label page directly via search rather than through marketplace discovery, which the brief flags as an open question rather than a decision (see Open Questions). Separately, pet parents who reach a home-based pro's Google Business listing will not see a Reserve-with-Google "Book online" button at all, since that pro is out of scope for the integration and their page renders with no address block.

## 3. Pain Points
- Pros are reluctant to promote a marketplace page because it risks losing the customer to a competitor also visible there (quote, 8/17 Connect grooming session).
- The current marketplace profile page (`www.yourgi.com/app/business-profile/bark`, revalidated live 2026-08-21) fails Google's Reserve with Google landing-page rules on multiple counts:
  - Services above the fold: fails — zero services clear the fold at 390×844; at 1366×768 only "Grooming" does; the service picker sits behind a "Request to Book" click rather than being pre-selected.
  - Address above the fold: fails — the street address renders at 3769px on mobile.
  - Off-site link: fails — a link to `dp-colorado.gingrapp.com` at 81px (a DP4W artifact not expected on a white-label page).
  - Login wall: now passes as of the 8/21 check — this changed from the 8/14 check, when Book routed anonymous users through an `isUserLoggedIn` gate.

## 4. Proposed Solution
- Users can view a pro's bookable services with prices without scrolling, on a 390×844 mobile viewport.
- Users can start the booking flow directly from the page — the service picker is on-page and pre-selected, not hidden behind a "Book" click.
- Users can book only through the embedded booking widget; there is no contact button, message action, or phone/email link on the page.
- Users can see the provider's street address above the fold, but only when the provider has one — home-based pros never publish a street address, so this block is conditional.
- Users can sign in with Yourgi from the page; doing so returns them to this same provider's page, never the marketplace.
- Providers can be shown one of three visual style options for the embedded widget, differing only in look and feel (accent color, neutral family, typeface, corner radius), as part of a sales conversation about whether they want it on their site.
- Staff (design/product) can build each style option on top of the existing marketplace Pro profile's data structure and fields — the template differs per style, the content model does not.
- **Open as of 2026-08-27:** whether the three style options are meant to visually match a pro's existing site (so the widget blends in) or are a fixed, self-contained Yourgi-branded component a pro embeds as-is regardless of their site's own design. Not yet decided — see Open Questions.

## 5. Success Metrics
Not defined in source material. The brief states goals (pass Google's landing-page policy, avoid losing pros' traffic to marketplace cross-sell) but sets no measurable target — no conversion rate, no Reserve with Google adoption number, no pro opt-in rate for the white-label offering.

## 6. Design Constraints
**Platform:** Web. Explicitly evaluated at mobile (390×844) and desktop (1366×768); mobile is the binding constraint since Google evaluates "above the fold" on mobile.
**Geography:** Not defined in source material, beyond the note that Reserve with Google currently scopes to DP4W centers only — marketplace Pros (the presumed majority of the white-label audience) are out of scope for the Google integration today.
**Accessibility:** Not defined in source material.
**Technical:** Built on the existing marketplace Pro profile's content model/fields (Requirement 1) — same fields, different template. Booking runs through the Connect Embeddable Booking Widget. Reserve with Google integration uses the Appointments Redirect lane (Google withdrew Appointments End-to-End documentation, closing the in-Google completion lane). **Corrected 2026-08-27:** the widget is embedded into a pro's own existing website (their domain, their surrounding page) rather than hosted at a `yourgi.com` path — the exact embed mechanism (script tag vs. iframe vs. something else) is not yet decided; see Open Questions. Style customization is capped at four variables: accent color, neutral family, typeface, corner radius.
**Brand:** Follows the `yourgi-brand` skill. Three style options, finalized 2026-08-24: **Earthy** (forest green accent, warm stone neutral, slab serif), **Clean/Modern** (teal accent, cool neutrals, geometric sans), and **Luxury/Premium** (deep wine accent, ivory neutral, refined serif, hairline sharp corners) — none of the three reuse Yourgi's own brand palette (Sunshine Yellow / Spot Black / Bone), since a style built from Yourgi's own look undercuts the requirement that the page not read as Yourgi/marketplace chrome. Different imagery/copy per option remains nice-to-have, not required.
**Trust & liability:** Decided 2026-08-24 — keep all three trust marks: "Book Now powered by Yourgi," the "Yourgi Pro" badge, and the "Covered by the Yourgi Guarantee" block. Per the `yourgi-brand` skill, the Guarantee's legal boundaries (remedy terms, timeframes, eligibility) are undocumented — write the Guarantee block around the mechanics ("if it's not right, we make it right") without stating specifics, and flag it for legal/brand review before the copy ships.
**Other:** Reserve with Google eligibility requires a commercial address, a Google Business Profile with a Places ID, and per-booking pro acceptance before confirmation — none of which apply to home-based marketplace Pros, who make up part of the white-label audience but are excluded from the Google integration regardless of how the page is built.

## 7. Open Questions
1. Whether the white-label page's URL should be indexable by search engines. No position is recorded; Reserve with Google works from a Business Profile link rather than from search, so indexability isn't required for that integration, but it bears on whether pet parents can find a pro's page outside the marketplace and on SEO/duplicate-content handling relative to the marketplace profile. Not the designer's call — needs Chris Mejia or Aash Srikar. **Partly reframed by the 2026-08-27 correction below** — if the widget lives on a page the pro already owns and indexes, indexability may no longer be Yourgi's decision to make at all.
2. **Added 2026-08-27 — embed mechanism.** How does a pro actually put this on their site: a script tag, an iframe, a copy-paste code block, a CMS plugin (e.g. a Squarespace/Wix/WordPress block)? Determines how much of the pro's surrounding page (fonts, CSS resets, z-index stacking) the widget has to defend itself against. Needs Chris Mejia / Aash Srikar and likely an eng estimate.
3. **Added 2026-08-27 — Reserve with Google "above the fold" compliance.** Google's landing-page rules (services/address above the fold, no off-site links) were evaluated against a page Yourgi fully controls. If the widget instead sits inside a pro's own page, Yourgi doesn't control what's above it — a pro could put a hero image or nav above the widget and push services below the fold. Does compliance now depend on the pro's placement choices, or does Yourgi need placement guidance/validation as part of onboarding a pro to Reserve with Google? Needs Chris Mejia / Aash Srikar.
4. **Added 2026-08-27 — style-matching intent.** Are the three style options meant to approximate a pro's existing site design, or are they a fixed set a pro picks from regardless of fit? See Section 4. Needs Chris Mejia / Aash Srikar or design call.

**Resolved 2026-08-24:**
- Due date: 2026-08-27 confirmed as authoritative (was ambiguous between 8/26 and 8/27 across two action items).
- Ariel alignment: mockups follow the shared visual direction agreed with Ariel on 2026-08-19 for the DP4W+Connect design.
- Trust marks (Requirement 8): keep all three. See Section 6, Trust & liability.
- Third style direction: Bold/Confident, built from Yourgi's core brand system. See Section 6, Brand.

## 8. Gaps
1. **Success Metrics** — no conversion target, Reserve with Google adoption goal, or pro opt-in rate is defined for this page. Matters because it determines whether the mockups should optimize for "a pro says yes to using this" (a sales-enablement goal) versus "a pet parent completes more bookings" (a demand-side goal) — those can pull the design in different directions. Ask Chris Mejia or Aash Srikar (product).
2. **Cross-side impact — indexability** — the brief itself raises this (see Open Question 1) but never resolves whether search-engine discovery of the white-label page is intended. Matters because it changes whether the page is a pure Reserve-with-Google/direct-link destination or an SEO surface competing with (or duplicating) the marketplace profile. Ask Chris Mejia or Aash Srikar.
3. **Accessibility** — no stated requirement (e.g., WCAG level) for a customer-facing booking page. Ask design/eng leads before mockups are treated as build-ready.
4. **Geography / launch scope** — not stated whether every existing Yourgi Pro is eligible for a white-label page at launch, or whether this rolls out to a subset first. Ask Chris Mejia or Aash Srikar.

---

## Color selection method (2026-08-24)

Accent colors were originally chosen for emotional register per style (earthy calm, modern trust, quiet luxury) and checked for legibility by eye. Cross-checked against CRO research afterward: contrast ratio between the CTA and its surroundings predicts conversion far more than which hue is used (~3.2x more, per industry data), and a 6–7:1+ ratio is the real threshold — not "which color converts best" in the abstract. Measured ratios: Meridian ~7.6:1 and Aldine ~9.3:1 already cleared it; Trailhead's original `#3F5D45` measured ~5.2:1, the weakest of the three, so it was deepened to `#2E4633` (~8.3:1). No change to Meridian or Aldine. Sources: contrast-vs-hue findings from buildgrowscale.com and cxl.com color-conversion research (see chat for full citations).

## Mockups (2026-08-24, frozen 2026-08-27)

Placeholder pro used throughout: Ortiz Mobile Grooming, Denver, CO (commercial address) for the three main style options; Reyes Dog Walks (home-based, no address) for the conditional-layout check. All four verified at 390×844 with services and prices above the fold, and at desktop width.

**Frozen as of 2026-08-27:** these four are no longer under active edit. The Inline Book Widget comp above absorbed their style-switching purpose for internal QA, and the sales-facing prototype (see "Sales-facing prototype" section below) is now the pitch-ready output. Left listed here for reference only.

- [Trailhead](https://claude.ai/code/artifact/2052dee8-7633-418a-b636-a215bf2a0633) — Earthy
- [Meridian](https://claude.ai/code/artifact/b7716885-2998-47ce-a7cd-eea9910cfb67) — Clean/Modern
- [Aldine](https://claude.ai/code/artifact/039ee23d-b96a-4dcd-9ca7-b789f74979d2) — Luxury/Premium
- [Reyes Dog Walks](https://claude.ai/code/artifact/fa9a1592-ff42-44d7-8999-3abdc8b95ff3) — Aldine style, home-based/no-address variant

A superseded fourth option ("Highbeam," built directly from Yourgi's own brand palette) was published and then rejected — see Version 1.2 note above. Removed from the artifact gallery 2026-08-24 as part of PM handoff cleanup.

## Decisions: booking widget placement (2026-08-24)

Two earlier explorations were tried and superseded before landing on the current pattern, and were removed from the artifact gallery 2026-08-24 as part of PM handoff cleanup:

- **"Overlook"** — a richer editorial full-page layout (photo hero, gallery, reviews) built on Trailhead's tokens, with Book running the target instant + priced + paid flow. Requirement-4 compliant but a separate exploration from the three approved style options.
- **Popup/modal over the existing marketplace page** — two iterations (an initial comp recreating the live BARK! Denver page as backdrop with a modal on top, then a refresh matching the live page's nav/banner/button text exactly). Brought to full 2026 modal-dialog accessibility standards (focus trap, `inert` backdrop, swipe-to-dismiss) before being dropped.

**Why superseded (at the time):** Lauren corrected this more than once in the same work session — the booking widget must live inline in the page layout, in the same spot the real Book button occupies, never as a modal/popup. Reference point: Rikki's white-label mockup (https://yourgiprofilepage.netlify.app/, cited in the brief's own Reference section), which keeps a persistent service/date/pet selector inline in the page. Confirmed against the real embedded booking widget's flow logic (`dateMode`/`pickDate()`, login, add-a-pet form) at `/Users/laurenpalma/Documents/Yourgi Projects/Emedded booking` rather than invented — see that repo before guessing at any flow detail.

**Reversed again 2026-08-27:** while reviewing the Marisol Vega placeholder site, Lauren reversed this a second time — the booking widget must now open as a popup/modal from a "Book Now" button, and must NOT be rendered inline in the page by default. Confirmed as a standing rule "everywhere, going forward," not a one-off for that comp. This is the current direction; treat the "why superseded" paragraph above as historical context for the 08-24 decision, not the live rule.

Also found and flagged separately (not part of this design work): a live bug on staging where selecting any Grooming tier for one test listing ("Bark Hotel for Dogs") leads to a "Select a Specialist — none available" dead end with a non-functional Continue button.

## Booking widget flow/QA comp (2026-08-24, placement superseded 2026-08-27)

All flow/QA work landed in one continuously-revised comp: **[Inline Book Widget](https://claude.ai/code/artifact/c2fe7103-10a3-4fb2-a2f7-dedf5bb76e46)** — still the reference for the step-by-step flow logic below, and still used for internal QA (viewport/widget-state/page-state toggles), but **its "Inline" placement is no longer the live rule** — see the popup reversal noted in the "Decisions: booking widget placement" section above. See "Sales-facing prototype" below for the pitch-ready artifact, which is a separate, simpler file.

- **Placement (historical, at time this comp was built):** one CSS Grid with named areas relocates the same widget markup between breakpoints — under the header on mobile, a sticky sidebar column on desktop — rather than duplicating it per layout.
- **Progressive, 6 steps:** Service → Date & Time + Pets → Add-ons → Your Info → Payment → Review. Each completed step collapses to a one-line recap with "Change," and Add-ons was deliberately placed as its own step near the end rather than folded into Service selection. A pet must be added before Continue unlocks past the Date & Time + Pets step.
- **Service-dependent date-picking**, ported from the real embedded booking widget's `dateMode`/`pickDate()` (source: `/Users/laurenpalma/Documents/Yourgi Projects/Emedded booking/app/lib/yourgi-ui.js` and `app/booking-widget-v2/page.js`, not invented): Daycare is multi-day (tap any number of days, each adds to the price), Boarding is a check-in/check-out range with a continuous highlighted span, Bath+Brush is a single day. Total is base rate × units, not a flat per-service price — a change from the earlier popup comp's flat pricing.
- **Add a Pet** is itself progressive (Type/Photo → Basic Info → Additional Details, including the real form's 7 behavioral yes/no questions), nested under Pets rather than a popup or separate page.
- **Inline login** ("Don't see your pets? Log In") is an accordion under Pets — email-or-phone, then a 6-digit code — ported directly from the embedded widget's `loginIdKind()`/`formatPhone()` logic and copy, not invented. Success pulls in mock saved pets.
- **Add-ons are speculative:** BARK's real live profile has no Add-Ons category today, and the `Booking Flow - Price upfront` audit already on file flags whether add-ons even feed price as an open question. What's built (Nail Trim/Teeth Brushing/Extra Playtime, each a flat one-time charge) is one reasonable interpretation, not a confirmed real behavior — flag before treating as ground truth.
- **Your Info step (step 4):** Name/Email/Phone, then a 6-digit code sent to that phone, ported from the embedded widget's `DetailsStep` (`contactFieldsValid`/`showContactCode`/`formComplete` logic). A guest who already logged in during step 2 sees a read-only identity card instead and skips the code. First tried on an earlier revision, reverted as a mistake, then explicitly re-requested — re-added 2026-08-24 as the standing direction.

- **Payment step added 2026-08-27 (step 5, between Your Info and Review):** Yourgi's real booking flow and the pro's actual payment system (Gingr, linked from the live page's "classic booking website" banner) both collect payment as a *separate* step after the pro accepts the request — not at booking time. Confirmed against Gingr's own support docs (customer portal invoices, saved-card/Add-Credit-Card checkout, convenience fees). Lauren explicitly chose **single-phase instead**: card entry is collected inside this same 5-step flow rather than mirroring Gingr's two-phase (request now, pay later) pattern, so the total is charged when the customer books. The step still borrows Gingr's real UI pattern — a saved card on file (with a "+ Use a different card" toggle) for a logged-in guest, or an Add Credit Card form (number/expiration/CVC/billing ZIP) for a guest — and shows a 3% card processing fee on the total from this step onward, mirroring Gingr's convenience-fee behavior. Review and the confirmation screen both show a Payment row (card ending in ####, amount charged).

This is now the current direction for the flow logic; see below for placement (popup) and for the file sellers actually use to pitch.

## Sales-facing prototype (2026-08-27)

Sellers pitch pros using **[`demo/sales-widget-demo.html`](../demo/sales-widget-demo.html)** — a single, git-committed, self-contained HTML file, not a claude.ai artifact. It requires no build step or server; open it directly in a browser.

- **Source:** built from the **Marisol Vega — Mobile Dog Grooming** claude.ai artifact (private, updated 2026-08-27) — a real, fully responsive single-pro marketing site (hero, photo gallery, testimonials), not the BARK! Denver device-frame QA comp above. The BARK comp was the initial (incorrect) source for this file; it was rebuilt from Marisol Vega once flagged.
- **Widget style toggle:** Earthy / Modern / Luxury, same three presets as everywhere else in this project.
- **Accent color hex override:** a seller can type any hex code to preview a pro's own brand color live on top of whichever style preset is active. Scoped to the booking widget only — the surrounding page's own accent (hero CTA, etc.) stays fixed as a backdrop example, per explicit instruction not to tie the two together.
- **Placement:** "Book Now" always opens the flow as a popup, matching the current standing rule above. There is no inline mode and no placement toggle in this file.
- **Viewport toggle (added 2026-08-27):** Mobile/Desktop, next to the style and accent controls. Mobile mode loads this same file into a phone-shaped iframe with `?embed=1` appended, which hides the toolbar for that inner load — necessary because the page's real `@media` breakpoints only respond to an actual browser viewport, so a resized container div alone wouldn't have triggered true mobile layout.
- **What's deliberately not here:** QA-only affordances like widget-unavailable/page-deactivated states (out of place in front of a pro).
- **Fixed 2026-08-27:** the widget's identity header, login copy, confirmation card, and both fallback states originally still showed "BARK! Denver" name/initials/phone/email, carried over from the Marisol Vega source — replaced with Marisol Vega's own identity (placeholder phone/email, since the source never defined one).

---
*Generated by yourgi-project-context. Update as decisions are made and questions are resolved.*
