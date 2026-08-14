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
- **Booking form → Google Sheets:** via a Google Apps Script `doPost` Web App. Sheet should have columns: Timestamp | Name | Email | Phone | Type | Date | Time | Notes | Status. Script not yet written — needs to be created and deployed, then its URL pasted into `SCRIPT_URL` in `index.html`.
- **Calendar logic:** appointment requests come in as pending, get manually approved, and only then get blocked on Google Calendar. Client names should NOT be publicly visible on the calendar — only the time block. This logic likely lives in the same Apps Script (on approval, calls Calendar API to create a busy event) or a lightweight admin step Gregorie does herself — needs to be decided/built.
- **No framework, no build step currently** — it's plain HTML/CSS/JS in one file. Fine to keep it that way for a single landing page. Only split into multiple files if it starts getting unwieldy — check with Duke before restructuring.

## Style rules (apply to all copy you write or edit)
- No em dashes
- No emojis
- Direct, confident, plain language — no corporate jargon or "committed to excellence" filler
- Benefit-first phrasing (what the patient gets, not just the feature)
- Third person for this client site (it's not Duke's own brand voice)

## Next steps
1. Get remaining client info from Gregorie (see list above)
2. Fill in placeholder content in `index.html`
3. Build and deploy the Google Apps Script for form submission + calendar blocking
4. Connect GitHub repo to Vercel, push to deploy
5. Point sageaph.com DNS at Vercel via Namecheap
6. Set up the business email (Google Workspace) if that's the route Gregorie wants
7. Add real photos/videos once received
