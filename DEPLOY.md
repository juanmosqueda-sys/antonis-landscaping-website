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

## After it's live

- Add the URL to the **Website** field in your Google Business Profile draft
- Put the URL in the footer of the Indeed / Craigslist / Facebook job posts
- Drop it into the Antonis Marketing Strategy doc as the canonical web home

## To edit later

It's one HTML file. Open `index.html` in any editor, change copy, redeploy by dragging the folder back to vercel.com (or `vercel --prod` from the CLI).
