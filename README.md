# CloudCore Global — ccglobal.ai
## Cloudflare Pages Deployment Guide

### Files in this package
- `index.html` — Full single-page website (no dependencies, no build step)
- `_headers` — Cloudflare Pages security & cache headers
- `_redirects` — www → apex and HTTP → HTTPS redirects
- `README.md` — This file

---

### Deploy to Cloudflare Pages (3 steps)

#### Option A: Direct Upload (Fastest)
1. Go to [Cloudflare Dashboard](https://dash.cloudflare.com) → **Pages** → **Create a project** → **Direct Upload**
2. Name your project `ccglobal` (or any name)
3. Drag and drop all files in this folder → **Deploy site**

#### Option B: GitHub (Recommended for ongoing updates)
1. Push these files to a GitHub repo (e.g. `cloudcoreglobal/website`)
2. In Cloudflare Pages → **Create a project** → **Connect to Git**
3. Select your repo
4. Build settings:
   - **Framework preset:** None
   - **Build command:** *(leave empty)*
   - **Build output directory:** `/` (root)
5. Click **Save and Deploy**

---

### Connect Your Domain (ccglobal.ai)
1. In your Cloudflare Pages project → **Custom domains** → **Set up a custom domain**
2. Enter `ccglobal.ai`
3. Cloudflare will auto-configure DNS since the domain is registered through Cloudflare Registrar
4. Also add `www.ccglobal.ai` → it will redirect to apex via `_redirects`

---

### Post-Deploy Checklist
- [ ] Verify site loads at https://ccglobal.ai
- [ ] Test contact form submission (shows success message)
- [ ] Enable Cloudflare **Web Analytics** (free, privacy-friendly)
- [ ] Enable **Bot Fight Mode** under Security
- [ ] Set SSL/TLS mode to **Full (strict)**
- [ ] Enable **Always Use HTTPS**
- [ ] Enable **HTTP/3 (with QUIC)**

---

### To add form backend (capture real submissions)
The contact form currently shows a client-side success message. To capture submissions:

**Option 1 — Cloudflare Workers (free)**
Add a Worker to POST form data to your CRM or email via API.

**Option 2 — Formspree (easiest)**
1. Sign up at formspree.io
2. Create a form → get your endpoint URL
3. Change `onclick="submitForm()"` to a proper form POST to your Formspree endpoint

**Option 3 — Cloudflare Email Routing + Worker**
Route form submissions to hello@ccglobal.ai using Cloudflare Email Routing.

---

Built for ccglobal.ai · CloudCore Global © 2025
