# Rockgate Academy — Production Website

Live site: **[rockgateacademy.co.uk](https://rockgateacademy.co.uk)**

Static HTML site for Rockgate Academy Ltd (company no. 17153023), a CeMAP training
provider. No build step, no framework, no backend — plain HTML/CSS/JS, deployed via
Cloudflare Pages watching this repo. Pushing to `main` deploys automatically.

## Files

| File | Purpose |
|---|---|
| `index.html` | The homepage — diagnostic-first hero, "Sound familiar?", "How it works", 6-card pricing grid, hidden proof section, founder section, "Your whole journey" gates, FAQ, enquiry form — Release 3B |
| `cemap-diagnostic.html` | Free CeMAP Diagnostic landing page (Calendly booking) — Release 3B |
| `module-rescue.html` | Module Rescue landing page (£345) — Release 3B |
| `case-study-clinic.html` | CeMAP 3 Case Study Clinic landing page (£175) — Release 3B |
| `privacy.html` | Privacy policy (data collection, GDPR rights, ICO contact) |
| `terms.html` | Terms and conditions (enrolment, cancellation/refunds, IP, liability, complaints) |
| `naveed-mirza-founder.jpg` | Founder photo, shared with the Rockgate Capital site |
| `libf-badge.png` | Naveed's personal LIBF Certified Mortgage Adviser badge (Credly) |
| `_redirects` | Cloudflare Pages redirect rules — `/mortgage-career-discovery` → `/cemap-diagnostic` (301) |
| `_headers` | Cloudflare Pages cache headers — forces `no-cache, must-revalidate` on every HTML page |

`mortgage-career-discovery.html` (the Release 2 £50 Career Discovery page) was retired in Release 3B — see release notes below. The file is no longer in this deploy repo; the old URL 301s to `/cemap-diagnostic` instead.

Each page is fully self-contained (styles and script inline) — open any `.html` file
directly in a browser to preview, no server required for a quick look. `index.html`'s
enquiry form and mobile nav do need to run from an actual page load (not `file://`) to
behave identically to production, since a couple of things (smooth-scroll anchors, the
mailto handler) are easiest to sanity-check from a served page.

## Editing

There's no build process — edit the HTML directly, then commit and push to `main` to
deploy. If you're changing something that touches layout (grids, forms, mobile nav),
check `document.documentElement.scrollWidth` against `clientWidth` at a phone width
before pushing; this site has previously shipped a CSS grid sizing bug that caused
horizontal scroll on mobile, so it's worth a quick check each time.

## Brand

Shares Rockgate Capital's gate-mark logo and core palette (deep green `#0F241F`,
brass gold `#B98A46`, cream `#F5F1E7`) to signal the same people are behind both,
while keeping its own bolder, course-sales layout and voice. Typefaces: Fraunces
(display), Archivo (body), IBM Plex Mono (prices, credential labels).

## Compliance

Rockgate Academy Ltd is **not authorised or regulated by the FCA** and is **not
affiliated with, endorsed by, or approved by LIBF**. These points are stated
explicitly in the footer, FAQ, and terms.html — check that new content doesn't
contradict them before publishing (e.g. avoid language that implies exam fees are
included, that case support replaces a CAS supervisor, or that the course itself
carries LIBF accreditation).

## Release Notes

Source plan: `Releases/Rockgate_Academy_Website_Releases/` (Naveed's own original
4-release roadmap docs). Releases 1 and 2 follow that roadmap directly. Release 3B is
a separate, later strategy pivot — a full repositioning brief delivered outside the
original roadmap docs — kept under its own "3B" label specifically so it doesn't
collide with or get confused for the original roadmap's own Release 3 (Training,
Mentoring & Founder Credibility), which remains a distinct, still-outstanding piece of
work in its own right (see below).

### Release 1 — Homepage & Navigation (shipped 2026-10-18)
- Hero rewritten: new headline, "Explore. Qualify. Develop." tagline, updated CTAs.
- Primary nav relabelled: About Us / CeMAP Training / Adviser Mentoring (new) / FAQs / Contact.
- "Three Gates" cards reworked into Explore / Qualify / Develop pathways, each with
  its own price line and CTA. Gate One/Two/Three numbering kept deliberately (ties to
  the arch-icon brand mark) — Naveed's call after seeing the draft without it.
- "Why Rockgate Academy" expanded from 3 to 5 proof points.
- Header buttons (Book a Call / Enquire Now) left unchanged — Book a Call still routes
  to the existing free 30-min Calendly intro call, kept distinct from the new paid
  Career Discovery Consultation (see Release 2).

### Release 2 — Career Discovery Consultation (shipped 2026-10-18, retired 2026-10-22 by Release 3B)
- New page `mortgage-career-discovery.html`: £50 / 30-min / 1:1 consultation landing
  page (hero, what's covered, who it's for, £50 CeMAP training credit, request form,
  FAQ, booking/cancellation terms). Styled identically to the main site; mailto-based
  request form, same pattern as the homepage enquiry form (no backend).
- Homepage's hero secondary CTA and the Explore pathway card now link here instead of
  the temporary `#enquire` anchor. "Career Discovery Consultation — £50" added to the
  homepage enquiry form's programme dropdown.
- Decisions confirmed by Naveed (2026-10-18), all per his original brief's "before
  publishing" checklist:
  - **Cancellation/refund**: free reschedule ≥24h notice; full refund if cancelled
    >24h before; <24h notice or no-show is non-refundable but gets one free
    reschedule instead. Consumer Contracts Regulations 2013 cooling-off wording
    included, explaining early-start consent.
  - **£50 training credit**: eligible against CeMAP Core or Complete Pathway only,
    within 30 days of the consultation, one-time, non-combinable, not cash.
  - **Payment turnaround**: Monzo link sent within 1 business day of request; slot
    held 48 hours; Naveed confirms personally by email once payment is received.
  - **URL**: kept as `mortgage-career-discovery.html` (matches the rest of the site's
    file-based URLs) rather than a clean `/mortgage-career-discovery` slug — clean
    URLs are explicitly Release 4 (SEO/launch QA) scope.
- Post-launch corrections (2026-10-18 to 2026-10-21): real Web3Forms submission
  (replacing mailto), corrected statutory cancellation wording with an explicit
  early-service consent checkbox, "Career Discovery" promoted to a header nav button,
  `no-cache` headers + canonical URLs to fix a version-consistency bug.
- **Retired in Release 3B** (2026-10-22): the whole £50 paid-consultation premise was
  dropped in favour of a free diagnostic as the funnel's single entry point. The page,
  its form, and its Calendly-adjacent plumbing no longer exist on the live site — see
  Release 3B below for why and what replaced it.

### Release 3B — Diagnostic-first repositioning (shipped 2026-10-22)
A full strategic pivot, delivered as a standalone brief outside the original 4-release
roadmap (see note above on why this is "3B" and not "3"). Rebuilds the site around
learners already stuck on CeMAP (failed a unit, resit booked, mocks below 70%) rather
than people broadly "considering" the career, with a free diagnostic as the one way in.
- **Site-wide**: single primary CTA ("Book your free CeMAP Diagnostic") everywhere,
  replacing Enquire Now / Career Discovery / Explore a Mortgage Career as the main
  buttons. Nav rebuilt: Home · Free Diagnostic · Module Rescue · Case Study Clinic ·
  Programmes · About · FAQs · Contact, with "Free Diagnostic"/"Diagnostic" pinned
  outside the mobile menu. WhatsApp pre-fill text updated to the new "stuck on CeMAP"
  framing. `/mortgage-career-discovery` 301s to `/cemap-diagnostic` via `_redirects`.
- **Homepage**: new hero (headline switchable via one `ACTIVE_HEADLINE` config value
  for a sequential A/B test — Headline A weeks 3–7, Headline B weeks 8–12, per brief),
  new "Sound familiar?" and "How it works" sections, 6-card pricing grid (Free
  Diagnostic / Module Rescue £345 "Most popular" / Case Study Clinic £175 / CeMAP Core
  £1,250 or 3×£425 / Complete Pathway £1,950 / Beyond CeMAP £395), hidden `#proof`
  section (stays hidden until a real testimonial is added — never fabricate one),
  founder's first quote replaced, "Three Gates" retitled "Your whole journey" and
  reframed around Explore (diagnostic) / Qualify (Rescue, Clinic or Core) / Develop
  (Beyond CeMAP + mentoring), 4 new FAQs added above the existing ones, enquiry form
  gained "Which module?" and "Exam or resit date" fields.
- **New pages**: `cemap-diagnostic.html` (Calendly embed, same click-to-load consent
  pattern as before), `module-rescue.html` (4-session plan breakdown), 
  `case-study-clinic.html` (next-clinic-date shown from one editable config value,
  falls back to "Next dates on request" when unset).
- **Tracking**: `?src=` query param captured and passed as `utm_source` into the
  Calendly embed and as a `Source:` line in the enquiry email — no new analytics tool
  added, per brief ("if the site has none, don't add cookie-based analytics").
- **Calendly** (done live via the Calendly MCP connector once Naveed connected it):
  renamed the event type to "Free CeMAP Diagnostic (30 min)" — URL slug unchanged,
  confirmed no £50 event type existed to delete. The 4 invitee questions (Which
  module? / Exam or resit date? / Latest mock or exam score? / What's the hardest
  part for you right now?, all required) were added by Naveed directly in the
  dashboard — Calendly's API exposes custom questions as read-only, so this step
  can't be done via the connector.
- **Compliance**: all FCA/LIBF/CAS/exam-fee wording carried over unchanged; the
  bespoke case-support section (and its CAS disclaimer) was deliberately left
  untouched, per brief.
- **Not done, still Naveed's own task**: confirming the £345/£175/£395/3×£425 Monzo
  payment links are created (not embedded in the site — sent manually post-enquiry,
  same pattern as the rest of the site).

### Release 3 — Training, Mentoring & Founder Credibility (not started)
Original roadmap scope, distinct from Release 3B above. Still outstanding: renaming
the bespoke case-support section into "Mortgage Adviser Mentoring" with clearer
professional boundaries, and adding founder trust evidence. Partially pre-empted by
Release 3B (founder quote already updated, Beyond CeMAP already repriced to £395).

### Release 4 — Operations, Forms, SEO & Launch QA (not started)
Original roadmap scope. Still outstanding: true server-backed submission for the main
enquiry form (currently mailto-based; the Release 2 Career Discovery form did get a
real Web3Forms backend before being retired — same approach would carry over), SEO
page titles/meta descriptions, technical SEO, full launch test plan. Release 3B's
"Tracking" section is a lighter version of this, not a replacement for it.

## Contact

hello@rockgateacademy.co.uk &middot; +44 7424 707984
