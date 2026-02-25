# AGENTS.md

## Cursor Cloud specific instructions

This is a Python-based MkDocs Material static site (personal consulting blog/portfolio). There are no databases, backend services, or containers.

### Running the dev server

```
pip install -r requirements-doc.txt
mkdocs serve -a 0.0.0.0:8000
```

The site is served at `http://localhost:8000/blog/` (the `/blog/` path prefix comes from `site_url` in `mkdocs.yml`).

### Build

```
mkdocs build
```

### Gotchas

- `mkdocs` and other CLI tools install to `~/.local/bin`. Ensure `PATH` includes `$HOME/.local/bin`.
- `mkdocs.yml` references `stylesheets/extra.css`, `javascripts/mathjax.js`, and `javascripts/analytics.js` which do not exist in the repo. The build still succeeds with warnings; this is expected.
- The `mkdocs-material[imaging]` extra (social cards) requires system-level Cairo/Pango/gdk-pixbuf libraries. These are not needed for normal dev serving or building. If social card generation is needed, install `libcairo2-dev libpango1.0-dev libgdk-pixbuf2.0-dev`.
- `.gitignore` has merge conflict markers (lines 4-8). This is a pre-existing issue in the repo.
- Blog post links in the nav are configured to point to the raw markdown files in the repo, which causes them to open on GitHub via the `edit_uri`/`repo_url` settings rather than rendering locally in certain navigation contexts.
- There are no linters, formatters, or test suites configured in this repository.
