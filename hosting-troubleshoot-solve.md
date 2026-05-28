# Hosting & Domain Setup Guide

## Deploying to Vercel

### Requirements
Vercel needs one of these at the **root** of your repo:
- `index.html` — for plain HTML sites
- `package.json` + framework (Next.js, Vite, etc.) — for JS projects

**Common 404 cause:** your HTML file is named something other than `index.html`. Rename it, commit, and push — Vercel redeploys automatically.

### Steps to deploy
1. Go to [vercel.com](https://vercel.com) and sign in with GitHub
2. Click **Add New > Project**
3. Import your repo
4. Leave all settings default for a plain HTML site → click **Deploy**
5. Vercel gives you a free URL like `your-project.vercel.app`

---

## Connecting a Custom Domain (Squarespace, GoDaddy, Namecheap, etc.)

### Step 1 — Add domain in Vercel
1. Go to your project in Vercel → **Settings > Domains**
2. Type your domain (e.g. `sudbuster.com`) → click **Add**
3. Vercel will show you DNS records to add — keep this tab open

### Step 2 — Update DNS at your registrar

**If you bought from Squarespace Domains:**
1. Go to [account.squarespace.com/domains](https://account.squarespace.com/domains)
2. Click your domain → **DNS Settings**
3. Delete any existing A records or CNAME for `@` and `www`
4. Add the records Vercel gave you:

| Type | Name | Value |
|------|------|-------|
| A | `@` | `76.76.21.21` |
| CNAME | `www` | `cname.vercel-dns.com` |

5. Save

### Step 3 — Wait and verify
- DNS changes take **5 min to 48 hours** to propagate (usually under 30 min)
- Back in Vercel **Settings > Domains**, the domain will show a green checkmark when active
- Visit your domain — it should load the site

---

## Quick Fixes

| Problem | Fix |
|---------|-----|
| `404 NOT_FOUND` on Vercel URL | Rename your HTML file to `index.html`, commit, push |
| Domain still shows old site | DNS hasn't propagated yet — wait and refresh |
| Domain shows "not secure" | Vercel auto-provisions SSL — can take up to 10 min after DNS resolves |
| Vercel not redeploying | Check that you pushed to the branch Vercel is watching (usually `main`) |
| Changes not showing live | Hard refresh: `Cmd+Shift+R` (Mac) / `Ctrl+Shift+R` (Windows) |
