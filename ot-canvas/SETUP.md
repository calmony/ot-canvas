# Setup guide

Step-by-step for getting this live on GitHub Pages, written for a Tuesday afternoon and a colleague who needs the link by end of day.

## Prerequisites

- A GitHub account (free is fine)
- Git installed locally, OR willingness to use GitHub's web upload
- About 5 minutes

## Option A — Web upload (no command line)

1. Go to https://github.com/new
2. Repository name: `ot-canvas`
3. Set it to **Public** (Pages free tier requires public, or upgrade to Pro for private Pages)
4. **Don't** initialize with README — we're uploading our own
5. Click **Create repository**
6. On the next page, click **uploading an existing file**
7. Drag everything from this folder into the upload area (or use the file picker)
8. Commit message: "Initial commit"
9. Click **Commit changes**
10. Go to **Settings → Pages** in the repo
11. Under **Source**, select **GitHub Actions**
12. Wait ~60 seconds, then check **Actions** tab to confirm deploy succeeded
13. Your site is live at `https://YOUR-USERNAME.github.io/ot-canvas/`

## Option B — Command line

```bash
cd /path/to/ot-canvas

git init
git add .
git commit -m "Initial commit"
git branch -M main

# Create the repo on github.com first, then:
git remote add origin https://github.com/YOUR-USERNAME/ot-canvas.git
git push -u origin main
```

Then follow steps 10–13 from Option A.

## Updating the README link

Once your repo is live, edit `README.md` and replace `YOUR-USERNAME` with your actual GitHub handle in the "Live demo" section. This makes the link clickable for anyone browsing the repo on github.com.

## Sharing with colleagues

Just send them the URL: `https://YOUR-USERNAME.github.io/ot-canvas/`

The page works on any modern browser, desktop or mobile. No login required (the repo is public, but they only see the rendered site — not the code, unless they look for it).

## Going private later

If you want to restrict access:

1. **GitHub Pro** ($4/mo) — enables private Pages with access control via repo collaborators
2. **Cloudflare Pages + Access** — free tier, supports SSO/email-allowlist gating
3. **Netlify Identity** — free tier, supports password protection on the site

## Custom domain

In **Settings → Pages → Custom domain**, enter something like `ot.yourdomain.com` and follow the DNS instructions (one `CNAME` record). HTTPS auto-provisions via Let's Encrypt.

## Troubleshooting

**404 after deploy:** Wait another minute. First deploys can take 1–2 minutes to propagate.

**Workflow fails:** Check **Settings → Pages → Source** is set to **GitHub Actions**, not **Deploy from a branch**.

**Icons not loading:** The Tabler Icons font loads from jsDelivr CDN. If your network blocks it (DoD environments sometimes do), download the font locally and update the `<link>` tag in `index.html`.
