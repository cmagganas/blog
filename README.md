# Consulting Blog Template

Create a professional consulting blog with the MkDocs Material theme.

## Deployment Steps

1. **Install Dependencies**: Ensure all packages are installed.

   ```bash
   pip install -r requirements-doc.txt
   ```

2. **Run Locally**: Start a local server to preview your site.

   ```bash
   mkdocs serve --dirty
   ```

3. **Deploy to GitHub Pages**: Go live with:

   ```bash
   mkdocs gh-deploy
   ```

## Fastest Iteration: `mkdocs serve --dirty`

The single most impactful thing is the **`--dirty` flag**. By default `mkdocs serve` rebuilds *every* page on each file save. `--dirty` rebuilds **only the changed file(s)**, cutting rebuild time roughly in half (~0.2s vs ~0.4s — and the gap widens dramatically as you add more pages).

### The command

```bash
mkdocs serve --dirty -a 0.0.0.0:8000
```

- **Live reload is on by default.** Save a `.md` file in `docs/` and the browser refreshes automatically — no manual reload needed.
- **`navigation.instant`** is already enabled in `mkdocs.yml`. This means page transitions use XHR (no full page loads), so the live-reload reconnects faster after each rebuild.

### What to edit, and what happens

| Edit target | Rebuild behavior | Speed |
|---|---|---|
| Any `docs/**/*.md` file | `--dirty`: only that page rebuilds, browser live-reloads | ~0.2s |
| `mkdocs.yml` (config, nav, theme, plugins) | Full rebuild triggered automatically | ~0.4s |
| `docs/stylesheets/extra.css` (once created) | Triggers live-reload, no markdown rebuild | Instant |
| `docs/javascripts/*.js` (once created) | Triggers live-reload | Instant |

### Key tips

1. **Content edits (Markdown):** Just edit files under `docs/` and save. That's it — `--dirty` + live-reload handles the rest.

2. **Watch additional paths with `-w`:** If you keep assets or includes outside `docs/`, add them:
   ```bash
   mkdocs serve --dirty -w includes/ -w assets/
   ```
   By default only `docs/` and `mkdocs.yml` are watched.

3. **Avoid `--clean` during development.** It wipes the `site/` directory every rebuild, which is slower and unnecessary while iterating. Save `--clean` for final production builds (`mkdocs build --clean`).

4. **The `minify` plugin adds overhead.** For maximum dev speed you could temporarily comment it out in `mkdocs.yml` during heavy iteration, but at this site's size (~9 pages) the difference is negligible.

5. **`navigation.instant` + `navigation.instant.prefetch`** are already enabled — these make the in-browser experience feel snappy because MkDocs Material prefetches linked pages and swaps content via AJAX instead of full page loads.

### The tradeoff of `--dirty`

Cross-page links and navigation may be slightly stale (e.g., if you rename a page, other pages' nav links won't update until a full build). When you need to verify nav/link correctness, do a one-off clean build:

```bash
mkdocs build --clean
```

Then go back to `mkdocs serve --dirty` for continued iteration.

## Tasks to Complete

- [x] Customize `mkdocs.yml` with your site details.
- [x] Update `docs/index.md` with your landing page info.
- [x] Revise `docs/services.md` with your services.
- [x] Set up [Cal.com](https://cal.com) and update links in `docs/index.md` and `docs/services.md`.
- [x] Add a blog posts to `docs/blog/posts/`.
- [ ] `mkdocs gh-deploy` make site render correctly, but pushing code changes it... figure out why
- [ ] Add more blog posts to `docs/blog/posts/`.

## Crafting Effective Content

### Value Equation

Maximize content value by addressing:

- **Dream Outcome**: Reader's goal
- **Probability of Success**: Likelihood of achieving it
- **Time**: Duration needed
- **Effort**: Work required

### AIDA Framework

1. **Attention**: Capture interest
2. **Interest**: Engage with relevant info
3. **Desire**: Connect emotionally
4. **Action**: Prompt next steps

### Landing Page Essentials

1. **Hero Section**: Benefit-driven headline, pain point subheadline, strong CTA.
2. **Social Proof**: Testimonials, case studies, credentials.
3. **Value Proposition**: Outcome statements, timeframes, effort, success indicators.

### Tips for Success

- Test different versions and CTAs.
- Focus on clarity; avoid jargon.
- Build trust with specific results and testimonials.

### Common Mistakes

- Focus on benefits, not features.
- Be specific, not vague.
- Provide social proof.
- Use strong CTAs.

## Quick Start
