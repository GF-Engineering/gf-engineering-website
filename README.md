# GF Engineering website

Static site, no build step: `index.html` + `images/`. Open `index.html`
directly in a browser to preview locally, or serve the folder with any
static file server.

## Deploy on GitHub Pages (recommended — lets you edit the design yourself)

1. Create a new repository on GitHub (e.g. `gf-engineering-website`).
   It can be public — Pages needs that on a free plan, and there's
   nothing private in this folder.
2. Push this folder to it:
   ```
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
3. In the repo, go to **Settings → Pages**, set "Deploy from a branch",
   branch `main`, folder `/ (root)`, save.
4. Under **Settings → Pages → Custom domain**, enter `gfengineering.nl`
   and save (this repo already has the `CNAME` file GitHub Pages needs).
5. At your DNS provider (netcup), on the `gfengineering.nl` zone, add:
   - Four **A** records on the apex (`@`) pointing to GitHub Pages:
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - Optionally a **CNAME** for `www` → `<your-username>.github.io`
   - **Leave your existing MX records untouched** — email keeps working
     through netcup regardless of where the site is hosted; A/CNAME
     records for the web don't affect mail routing.
6. Back in GitHub Pages settings, once DNS has propagated (can take up
   to a few hours), tick **Enforce HTTPS**.

After that, editing the site is just: edit `index.html` locally, commit,
`git push` — GitHub Pages redeploys automatically in about a minute.

## Deploy on netcup directly (simpler, no GitHub involved)

Upload `index.html` and the `images/` folder as-is to your netcup web
space, in whichever directory serves `gfengineering.nl`. No build step,
no server-side requirements — it's plain HTML/CSS with two Google
Fonts loaded over HTTPS.
