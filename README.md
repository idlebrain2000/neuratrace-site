# NeuraTrace — website

Static site. No build step. Everything the page needs is in this folder.

## Deploy to Vercel (first time)

**Option A — drag and drop (no terminal)**
1. Go to https://vercel.com/new
2. Drag this whole folder onto the page.
3. Project name: `neuratrace`. Framework preset: **Other**. Click Deploy.
4. Live in ~30 seconds at `https://neuratrace.vercel.app`.

**Option B — command line**
```
npm i -g vercel
cd neuratrace-site
vercel --prod
```

## Redeploy after a change
Drag the folder again (Option A) or run `vercel --prod` (Option B). Vercel keeps every previous deploy; you can roll back from the dashboard.

## Custom domain
Vercel project → Settings → Domains → Add `neuratrace.co` (and `www.neuratrace.co`).
Vercel shows two records to add at your registrar:

| Type  | Name | Value                 |
|-------|------|-----------------------|
| A     | @    | 76.76.21.21           |
| CNAME | www  | cname.vercel-dns.com  |

HTTPS is issued automatically within a few minutes of DNS resolving.
Then set `www` → redirect to apex (or the reverse) in the same Domains panel.

## Files
- `index.html` — the whole site
- `assets/hero.mp4`, `assets/hero-poster.jpg` — homepage video and its first frame
- `assets/icon-256.png`, `icon-512.png`, `favicon.ico`, `favicon-32.png`, `apple-touch-icon.png` — brand mark
- `assets/og.jpg` — the preview image shown when the link is shared (WhatsApp, LinkedIn, iMessage, Slack)
- `vercel.json` — caching + security headers
- `robots.txt`, `sitemap.xml`, `site.webmanifest` — search engine + PWA metadata

## Before you publish the domain
- `hello@neuratrace.co` is referenced in the Contact section and in `index.html` structured data. Set up mailbox/forwarding for it at the registrar or via Google Workspace.
- The absolute URLs in `index.html` (`canonical`, `og:url`, `og:image`) and `sitemap.xml` / `robots.txt` assume `https://neuratrace.co`. If you buy a different domain, find-and-replace `neuratrace.co` in those four files.
