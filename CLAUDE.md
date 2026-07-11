# Nuhi Web Design — Project Context

## The business
I'm Nuhi. I sell one-page websites to small local service businesses in Loudoun
County, VA (Ashburn, Sterling, Leesburg) that have strong Google reviews but no
website. I find leads on Google Maps, cold call them, and pitch with a
pre-built demo mockup of THEIR business.

- Price: $500 flat per site (50% deposit upfront, balance at launch)
- Recurring: $50/mo "Care Plan" (hosting, updates, small changes)
- Turnaround promise: live within 1 week of receiving client materials
- Target niches: barbers, landscapers, auto detailers, junk removal,
  cleaning services, pet groomers, handymen

## Domain & hosting
- My domain: nuhiwebdesign.com
- Hosting: Netlify (free tier), deployed from this folder
- My site lives at the root; each prospect demo lives at
  nuhiwebdesign.com/<name> (e.g. /reza)
- ARCHITECTURE RULE: demos live under my main site, but every PAID client
  site becomes its own separate Netlify project with its own repo/folder
  and the client's own domain (registered in the CLIENT's name, not mine).
  Keeps handoffs clean and domains portable.

## Folder conventions
- `index.html` — my own business site (source: nuhiwebdesign-site.html)
- `/demos/<name>/index.html` — one folder per prospect demo
- `/templates/` — one reusable template per business category
  (barber, landscaper, junk-removal, detailer, ...)

## Demo workflow (the core loop)
When I say "new demo for <business>", do this:
1. Copy the closest category template from /templates
2. Swap in the business's real data that I provide (or that's pasted in):
   name, phone (tel: link), address, hours, star rating + review count,
   2–3 SHORT review excerpts (under 15 words each), service area
3. Prices are always placeholders labeled "sample pricing — final prices
   set by the owner"
4. Every demo MUST have: a "DRAFT preview — not a published website" banner,
   a footer disclaimer with my name/contact, and <meta name="robots"
   content="noindex, nofollow">
5. Deploy so it's live at /demos/<name> and give me the short URL to text

## Design standards
- One page, mobile-first, fast (no frameworks, single HTML file per site)
- Always include: tap-to-call button, hours, address + Google Maps link,
  services list, reviews section
- CONTACT FORMS: always use Netlify Forms — plain HTML <form> with the
  `data-netlify="true"` and `name="contact"` attributes plus a hidden
  `form-name` input. No JS form libraries, no third-party form services.
  On paid client sites, set submission email notifications to the CLIENT's
  email in the Netlify dashboard (note this as a launch-checklist step).
  Demos get the form markup but it's decorative until deployed as a real
  Netlify project.
- Each category template has its own visual identity; don't reuse my
  site's navy/amber palette for client demos
- Existing quality bar: see reza demo (bottle green/brass barber site)

## My contact info (use in footers/disclaimers)
- Phone: (347) 720-4574 · tel:+13477204574
- Email: nuhiwebdesign@gmail.com
- Calendly: https://calendly.com/nuhirath/30min

## Setup status (done 2026-07-11)
- Folder structure in place; my site is index.html, first demo at /demos/reza
- Templates built: /templates/barber, /templates/landscaper, /templates/junk-removal
  (all use [PLACEHOLDER] tokens; landscaper & junk-removal include Netlify forms)
- Git: pushed to github.com/nuhiii/nuhiwebdesign (main)
- Netlify: site "nuhiwebdesign", linked to this folder; deploy with
  `netlify deploy --prod`
- Custom domain nuhiwebdesign.com + www added on Netlify; DNS via Cloudflare
  (CNAME @ and www -> nuhiwebdesign.netlify.app, proxy OFF / grey cloud)
- Short demo URLs via _redirects file (e.g. /reza -> /demos/reza/) — add a
  line there for each new demo
- /demos/sample-barber ("Luca Moreno") is a FICTIONAL business featured on my
  site's Sample Work section — real prospect demos (like /reza) must NOT be
  shown there until the owner gives permission
- nuhi-lead-tracker.xlsx is gitignored (private prospect data)
