# Rockgate Academy — Production Website

Live site: **[rockgateacademy.co.uk](https://rockgateacademy.co.uk)**

Static HTML site for Rockgate Academy Ltd (company no. 17153023), a CeMAP training
provider. No build step, no framework, no backend — plain HTML/CSS/JS, deployed via
Cloudflare Pages watching this repo. Pushing to `main` deploys automatically.

## Files

| File | Purpose |
|---|---|
| `index.html` | The homepage — hero, Three Gates (Explore/Qualify/Develop) pathways, programmes/pricing, bespoke case support, founder section, FAQ, enquiry form |
| `mortgage-career-discovery.html` | Career Discovery Consultation landing page (£50, 30-min paid consultation) — Release 2 |
| `privacy.html` | Privacy policy (data collection, GDPR rights, ICO contact) |
| `terms.html` | Terms and conditions (enrolment, cancellation/refunds, IP, liability, complaints) |
| `naveed-mirza-founder.jpg` | Founder photo, shared with the Rockgate Capital site |
| `libf-badge.png` | Naveed's personal LIBF Certified Mortgage Adviser badge (Credly) |

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

Source plan: `Releases/Rockgate_Academy_Website_Releases/` (Naveed's own 4-release
roadmap docs). Implemented sequentially, each reviewed and approved before the next
started.

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

### Release 2 — Career Discovery Consultation (shipped — pending go-live confirmation)
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
- Not yet done (Release 4 scope per Naveed's own docs): true server-backed form
  submission, Calendly Free's single-active-event-type constraint if a self-serve
  booking step is added later, FAQ additions for the £50 credit specifically.

### Release 3 — Training, Mentoring & Founder Credibility (not started)
### Release 4 — Operations, Forms, SEO & Launch QA (not started)

## Contact

hello@rockgateacademy.co.uk &middot; +44 7424 707984
