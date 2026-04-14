# Lincoln Access Screen Reader — Website

Public placeholder site for **Lincoln Access Screen Reader (LASR)**: what the project is, why it exists, and how it relates to school-friendly deployment and student privacy (including alignment with frameworks such as Illinois **SOPPA**). The desktop app itself lives elsewhere; this repository holds the static marketing and explanation page you can link from the product.

## Contents

| File | Purpose |
|------|---------|
| `index.html` | Main page copy and structure |
| `styles.css` | Layout and theme |

## Preview locally

From this directory:

```bash
python3 -m http.server 8080
```

Then open `http://localhost:8080`. Using a simple server avoids subtle issues with `file://` URLs and matches how GitHub Pages serves the files.

## GitHub Pages deployment

This repo includes a workflow (`.github/workflows/deploy-pages.yml`) that **publishes the site on every push to `main`** (and can be run manually).

### One-time repository settings

1. On GitHub: **Settings → Pages**.
2. Under **Build and deployment**, set **Source** to **GitHub Actions** (not “Deploy from a branch”).
3. Push to `main` (or run the workflow from the **Actions** tab → **Deploy to GitHub Pages** → **Run workflow**).

After the first successful run, Pages shows the live URL (typically `https://<user-or-org>.github.io/<repo>/` for a project site).

### Permissions

The workflow uses the default `GITHUB_TOKEN` with `pages: write` and `id-token: write` so GitHub Pages can accept the deployment artifact. No personal access token is required for standard hosting.

## Updating the site

Edit `index.html` and/or `styles.css`, commit, and push to `main`. The workflow copies those files into `_site` for deployment (so the live site does not ship `.git` or other repo-only files). If you add root-level assets such as `favicon.ico` or an `images/` folder, update the `cp` step in `.github/workflows/deploy-pages.yml` to include them.
