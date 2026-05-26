# Antonis Landscaping — Website Deployment

## Files in this folder

- `index.html` — the full one-page site (mobile-first, single file, embedded CSS, no build step)
- `vercel.json` — security headers + clean URLs for Vercel

## Fastest path to a live URL (~60 seconds)

1. Go to **vercel.com/new**
2. Click **Deploy** → **Other** (skip the Git template flow)
3. **Drag this `website` folder** onto the upload area
4. Vercel will auto-detect it as a static site and assign a `*.vercel.app` URL
5. Done. Paste the URL anywhere — GBP profile, job postings, footer.

## Alternative: give me a Vercel token

If you'd rather I deploy it from here:

1. Go to **vercel.com/account/tokens**
2. Create a token (any name, no expiry needed for a one-shot deploy — you can revoke after)
3. Paste it back to me in chat — I'll run the CLI and report the URL

## Before going live — one-time configuration

**Form backend (Formspree, 2 min, free):**
1. Sign up at **formspree.io** with `antonislandscaping@yahoo.com`
2. Create a new form, name it "Antonis quote requests"
3. Copy the form ID (looks like `mzbqkxgr`)
4. Open `index.html`, search for `YOUR_FORM_ID`, replace with the real ID
5. Save & redeploy

Without this step, the quote form will show "success" to visitors but won't actually deliver submissions.

**Photos:** All photos now reference real Antoni's job shots pulled from the existing `antonislandscaping.com` site (hosted on GoDaddy's `wsimg.com` CDN). **Caveat:** if the old GoDaddy site is ever shut down, these URLs will break. To future-proof, download each `DSC00XXX.jpg` into `assets/photos/` and update the URLs to relative paths. Affected files (search `wsimg.com` in `index.html`): hero, og:image, schema, 4 service cards, drought ribbon, final CTA, 6 portfolio tiles. Available photos: DSC00042, 00044, 00049, 00102, 00118, 00122, 00416, 00423, 00425.

**Testimonials:** The three customer quotes are placeholders from the canonical website copy. Replace with real quotes once GBP reviews start rolling in. Search for `<!-- TODO: replace placeholder testimonials` in `index.html`.

## After it's live

- Add the URL to the **Website** field in your Google Business Profile draft
- Put the URL in the footer of the Indeed / Craigslist / Facebook job posts
- Drop it into the Antonis Marketing Strategy doc as the canonical web home
- Submit the URL to **Google Search Console** (`search.google.com/search-console`) to speed up indexing

## To edit later

It's one HTML file. Open `index.html` in any editor, change copy, redeploy by dragging the folder back to vercel.com (or `vercel --prod` from the CLI).
