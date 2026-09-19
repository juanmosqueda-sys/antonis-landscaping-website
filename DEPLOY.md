# Antoni's Landscaping — Website Deployment

## What's in this repo

- `index.html` — the home page (single file, embedded JS, no build step)
- `commercial/index.html` — the commercial & HOA landing page
- `assets/site.css` — shared stylesheet for both pages
- `assets/photos/` — all site photography, self-hosted
- `assets/logo.png`, `assets/logo-white.png` — brand marks
- `vercel.json` — clean URLs + security headers

There is no build step. Edit the HTML or CSS, commit, push — that's the whole
workflow.

## How deploys work

The repo is connected to Vercel. **Every push to `main` deploys to production
automatically.** Every pull request gets its own preview URL, posted as a
comment on the PR by the Vercel bot.

So: open a PR, check the preview, merge. The merge is the deploy.

## Going live on antonislandscaping.com

The site currently answers on its `*.vercel.app` address. To launch it on the
real domain:

### 1. Add the domain in Vercel

1. Open the project at **vercel.com** → **Settings** → **Domains**
2. Add `antonislandscaping.com`, then add `www.antonislandscaping.com`
3. Choose which one is canonical — apex (`antonislandscaping.com`) is the
   usual pick. Vercel will redirect the other one to it.
4. Vercel now shows the exact DNS records to create. Keep this tab open.

### 2. Point DNS at Vercel (at GoDaddy)

Two ways. **Prefer the first** unless you have a reason not to.

**Option A — change records only (safer, leaves email alone):**

1. GoDaddy → **My Products** → the domain → **DNS** → **Manage Zones**
2. Edit the `A` record for host `@` to the IP address Vercel showed you
3. Edit (or add) a `CNAME` for host `www` pointing to `cname.vercel-dns.com`
4. Leave every `MX` and `TXT` record exactly as-is — those carry email and
   domain verification

**Option B — move nameservers to Vercel (simpler, moves *all* DNS):**

Only do this if nothing else runs on the domain. It moves email routing too,
so if any address `@antonislandscaping.com` receives mail, Option A is the
safe choice.

### 3. Wait, then verify

DNS usually propagates in minutes, occasionally a few hours. Vercel issues the
HTTPS certificate on its own once the records resolve — no action needed.

Before moving on, load `https://antonislandscaping.com` in a browser and
confirm the new site appears with a valid padlock.

### 4. Merge the URL swap

The `canonical`, `og:url`, `og:image` and JSON-LD `url` / `@id` / `image`
fields are absolute URLs and must name the live domain. There are 13 of them
across the two pages.

**Merge that change only after step 3 passes** — pointing canonical tags at a
domain that doesn't resolve yet tells Google the real site is a dead address.

### 5. Tell Google

- **Search Console** (`search.google.com/search-console`) — add the domain as
  a property, verify it, submit the home page
- **Google Business Profile** — put `https://antonislandscaping.com` in the
  Website field
- Update the URL anywhere it's already posted: job listings, social profiles,
  the marketing strategy doc

## Before launch — check these

**The quote form.** It posts to Formspree (form ID is in `index.html`, search
`FORMSPREE_ID`). Run one real submission end to end and confirm the email
lands in the inbox. The form reports success based on Formspree's response, so
a misconfigured account loses leads silently rather than visibly.

**The commercial page placeholder.** `commercial/index.html` has a card marked
`<!-- PLACEHOLDER -->` where a board or property-manager testimonial should
go. It currently holds neutral copy about the track record, which is true and
safe to ship. Swap in a real quote when one exists — do not invent one.

## Editing later

Change the file, open a PR, look at the preview URL the Vercel bot posts, then
merge. Production updates within a minute or so of the merge.
