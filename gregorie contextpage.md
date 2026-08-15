# Sage Advanced Practice Healthcare — Project Context

Read this before doing anything else in this repo. This is a client website build for LeadSite Consulting (Duke's agency). You're picking up mid-project.

## Client
- **Business:** Sage Advanced Practice Healthcare LLC ("Sage APH")
- **Contact:** Gregorie Acceus (referred to Duke by his friend Marcus)
- **What they do:** Nurse practitioner practice — personalized, whole-person primary care
- **Domain:** sageaph.com (registered on Namecheap, not yet connected)
- **Deal terms:** One-time build payment + $10/month hosting fee Duke charges the client. Landing page + Calendly-style booking interaction scoped at $600.

## Brand
- **Palette:** Sage green `#6E7A64` (primary), deep sage `#4C5745`, soft sage `#8E997F`, cream `#FAF9F5`, warm cream `#F3F0E8`, taupe `#A89E8C`, tan `#C7B8A6`, ink `#2F342A`. Pulled directly from the client's logo — do not deviate without checking with Duke.
- **Typography:** Cormorant Garamond (serif, headings — matches logo wordmark), Jost (sans, body), Pinyon Script (script accent, used for the tagline only — sparingly).
- **Tagline:** "Compassionate Care. Advanced Expertise. Whole Person Health."
- **Logo:** Watercolor botanical "S" monogram with a Rod of Asclepius (medical symbol) woven through it, olive branch. File: `logo.png` in this repo.
- **Voice:** Warm but clinical-credible. Not corporate, not overly casual. See LeadSite's `straight-line-web-copy` skill for the persuasion structure already applied to this page (hero hook → pain → solution → trust → booking).

## What's already built
`index.html` — single-file static site (HTML/CSS/JS inline, no framework, no build step). Sections in order:
1. Sticky nav
2. Hero (headline + tagline + dual CTA)
3. Pain/bridge section (dark sage background)
4. Offerings grid (3 placeholder service cards)
5. Provider/about section (photo + bio placeholders)
6. First-visit 3-step explainer
7. Testimonials grid (3 placeholders)
8. Booking form section (sage background, form posts to a Google Apps Script endpoint)
9. Location/contact section (map embed placeholder + contact list)
10. Footer

The booking form is wired to POST to a Google Apps Script Web App URL (placeholder `SCRIPT_URL` constant near the bottom of the file, currently `"PASTE_APPS_SCRIPT_URL_HERE"`). It is NOT yet functional — needs the actual Apps Script deployed and the URL pasted in.

**Two integrations pending, both waiting on info from Duke/Gregorie (as of 2026-08-14):**
- **Google Maps embed** — needs the office address. Placeholder lives at `id="mapSlot"` in the location section.
- **Calendly link** — a separate "Schedule Appointment" button/link pointing to a Calendly scheduling page, distinct from the on-page form. Needs the actual Calendly URL from Gregorie.

## What's still needed from Gregorie (not yet received)
See placeholder markers in `index.html` — every one is commented or bracketed like `[Service 1 — e.g. Primary Care]`. Full list:
- Mission statement (exact wording)
- Real service/offerings list with descriptions
- Provider full name, credentials, bio, headshot photo
- 2-3 testimonials
- What to bring to a first visit
- Office address, phone, business email, hours
- Insurance/payment info
- Actual appointment types for the booking dropdown
- Approval workflow specifics (who reviews requests, turnaround time)
- Which Google Calendar to connect
- Office/exterior photos, any videos she wants included
- Confirmation she has (or needs) a Google Business Profile

**Do not invent or finalize any of the above.** Leave placeholders in place until Duke provides real content from the client. Flag clearly if you're about to guess at something client-specific.

## Technical plan / decisions already made
- **Hosting:** Vercel, deployed via GitHub — push to `main` auto-deploys. Using Vercel Pro (not Hobby/free tier — free tier ToS excludes commercial client use).
- **DNS:** sageaph.com is on Namecheap. Will point A/CNAME records to Vercel once the project is live. If Gregorie wants Google Workspace email on the same domain, plan those MX record changes at the same time as the Vercel DNS change (do in one pass, not two).
- **Booking form → email (UPDATED 2026-08-14, supersedes the Sheets/Calendar plan below):** Duke decided the on-page form should just send an email with the submitted info — no Google Sheets, no Apps Script, no automatic Calendar blocking, no approval workflow. Much simpler than originally planned. Still needs an actual mechanism to send that email (e.g. a lightweight Apps Script `doPost` that emails instead of writing to a Sheet, or a form-to-email service like Formspree) — not yet built.
- **Calendly (separate from the form):** a second, distinct booking path — a "Schedule Appointment" button/link to a Calendly page. Calendly handles its own availability and calendar sync; this is not merged with the on-page form. Waiting on the actual Calendly URL from Gregorie.
- ~~Original plan (superseded): booking form → Google Sheets via Apps Script `doPost`, with columns Timestamp | Name | Email | Phone | Type | Date | Time | Notes | Status, plus manual approval before blocking Google Calendar (client names not publicly visible, only the time block). Keeping this struck through for history — do not build this version.~~
- **No framework, no build step currently** — it's plain HTML/CSS/JS in one file. Fine to keep it that way for a single landing page. Only split into multiple files if it starts getting unwieldy — check with Duke before restructuring.

## Style rules (apply to all copy you write or edit)
- No em dashes
- No emojis
- Direct, confident, plain language — no corporate jargon or "committed to excellence" filler
- Benefit-first phrasing (what the patient gets, not just the feature)
- Third person for this client site (it's not Duke's own brand voice)

## Next steps
1. Get remaining client info from Gregorie (see list above), including office address and Calendly URL
2. Fill in placeholder content in `index.html`
3. Build the form-to-email mechanism for the booking form (not Sheets/Calendar — see updated technical plan above)
4. Add the Google Maps embed once the address is confirmed
5. Add the Calendly "Schedule Appointment" link once Gregorie provides it
6. Point sageaph.com DNS at Vercel via Namecheap
7. Set up the business email (Google Workspace) if that's the route Gregorie wants
8. Add real photos/videos once received

## Status log
- 2026-08-14: GitHub repo (`ybsdavidcharlesii-cmd/Sage-Site`) connected and pushed to; Vercel is live and auto-deploying from `main`. Logo and Gregorie's headshot added. Nav logo cropped to emblem-only (`emblem.png`). Booking form direction changed from Sheets/Calendar to simple email send. Calendly added as a second, separate booking path. Still waiting on: office address, Calendly URL, bio copy, mission statement, services list, testimonials, hours/contact info.
