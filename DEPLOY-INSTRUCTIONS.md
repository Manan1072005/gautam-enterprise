# Deploying to GitHub Pages

This site was built with its router base path set to `/gautam-enterprise`, and it
already includes the standard GitHub Pages single-page-app trick (`404.html` is
a copy of `index.html`, so any URL falls back to loading the app). That means it
was designed to be deployed as a **GitHub Pages project site**, and the repo name
must be exactly `gautam-enterprise` or the page will load blank.

## Steps

1. **Create a new GitHub repository named exactly:**
   ```
   gautam-enterprise
   ```
   (Settings → General → repo name must match this exactly — capitalization
   doesn't matter, GitHub Pages URLs are lowercased, but spelling must match.)

2. **Upload these files to the root of that repo** (not inside a subfolder):
   - `index.html`
   - `404.html`
   - `favicon.svg`
   - `robots.txt`
   - `assets/` (folder, with its 3 files inside)

   You can do this via the GitHub web UI ("Add file → Upload files") or via git:
   ```bash
   git clone https://github.com/<your-username>/gautam-enterprise.git
   cd gautam-enterprise
   # copy all the files from this folder in here
   git add .
   git commit -m "Deploy site"
   git push
   ```

3. **Enable GitHub Pages:**
   - Go to the repo → Settings → Pages
   - Under "Build and deployment", set Source to **Deploy from a branch**
   - Branch: `main`, folder: `/ (root)`
   - Save

4. **Wait 1–2 minutes**, then visit:
   ```
   https://<your-username>.github.io/gautam-enterprise/
   ```
   (Note the trailing slash and exact path — this must match for the site to render.)

## Important — do NOT rename the repo

If you deploy under a different repo name (e.g. just naming it after your
username, or a custom name), the page will load completely blank, because the
app checks that the URL path starts with `/gautam-enterprise/`. If you need a
different name or a custom domain later, let me know and I can rebuild the
router config to remove that restriction.
