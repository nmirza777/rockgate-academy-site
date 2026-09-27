# Rockgate Academy — Production Website

Live site: **[rockgateacademy.co.uk](https://rockgateacademy.co.uk)**

Static HTML site for Rockgate Academy Ltd (company no. 17153023), a CeMAP training
provider. No build step, no framework, no backend — plain HTML/CSS/JS, deployed via
Cloudflare Pages watching this repo. Pushing to `main` deploys automatically.

## Files

| File | Purpose |
|---|---|
| `index.html` | The homepage — hero, three-gates journey, programmes/pricing, bespoke case support, founder section, FAQ, enquiry form |
| `privacy.html` | Privacy policy (data collection, GDPR rights, ICO contact) |
| `terms.html` | Terms and conditions (enrolment, cancellation/refunds, IP, liability, complaints) |
| `naveed-mirza-founder.jpg` | Founder photo, shared with the Rockgate Capital site |
| `libf-badge.png` | Naveed's personal LIBF Certified Mortgage Adviser badge (Credly) |
| `rockgate-academy-logo.png`, `naveed-founder.png` | Legacy assets, no longer referenced by any page — safe to delete |

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

## Contact

hello@rockgateacademy.co.uk &middot; +44 7424 707984
