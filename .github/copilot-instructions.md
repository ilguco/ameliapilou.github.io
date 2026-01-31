# GitHub Copilot instructions for this repository ✅

## Quick summary
- Small static portfolio site for "Amélia Pilou" (BTS SIO portfolio). Served as a GitHub Pages site (username.github.io). Mostly plain HTML, CSS and Bootstrap (no build system).
- Primary content files: `index.html`, `pages/cv.html`, `css/cv.css`, `css/realisations.css`, images in `images/` and `images/cv/`.

## Goals for an AI coding agent 🔧
- Make safe, minimal PRs that improve HTML correctness, fix broken links/paths, and improve accessibility and responsiveness without changing tone/content (French). Prefer focused commits per issue.
- Avoid large refactors (e.g., upgrading Bootstrap major version) unless requested and tested manually.

## Where to start (files to inspect) 📁
- `index.html` — homepage, top-level links and `jumbotron` content.
- `pages/cv.html` — detailed CV; references `../css/cv.css` and `../images/*`.
- `css/cv.css` and `css/realisations.css` — page-specific styling. Prefer editing CSS here rather than inline styles.
- `images/` and `images/cv/` — assets and social icons used by pages.
- `README.md` — project purpose and constraints (exam requirements E5/E6).

## Common, discoverable issues to check and fix ✅
- Relative paths: verify correctness from file location. Example: `index.html` (at repo root) should link to `css/cv.css` (not `../css/cv.css`).
- HTML syntax errors: look for stray/mismatched tags (e.g., `</<p>` in `pages/cv.html`) and duplicate `<html>` tags; fix to pass basic HTML validators.
- Navbar behaviour: Bootstrap toggler markup has typos — `data-tarfet` should be `data-target`; ensure the toggler button includes an element with `navbar-toggler-icon` and the collapse container includes `collapse navbar-collapse` classes.
- Accessibility: add `alt` text already present for images but ensure buttons and links include discernible labels and `aria-*` attributes where appropriate.
- CDN usage: site uses Bootstrap 4.6 and jQuery via CDN. If changing versions, test for breaking markup differences (dropdown/collapse behavior changed between v4 and v5).

## Local preview & quick checks 🧭
- To preview locally, run a static server from repo root and open `http://localhost:8000`:
  - Python: `python -m http.server 8000` (recommended for quick testing)
  - Or use VS Code Live Server extension.
- Quick checks:
  - Open pages in browser, toggle mobile menu, check images load and links work.
  - Run pages through W3C HTML validator or an HTML linter (HTMLHint) to catch markup errors.

## PR & commit guidance ✍️
- Make small focused PRs (one fix per PR): e.g., "Fix navbar toggler attribute and collapse classes", "Correct relative path in `index.html`", "Fix malformed HTML in `pages/cv.html`".
- Keep commit messages short and descriptive, reference affected file: `Fix: data-target typo in navbar (index.html, pages/cv.html)`.
- Maintain French content and exam-related section structure (E5/E6) — do not alter copy meaning unless asked.

## When to ask the repo owner / reviewer ⚠️
- Before changing or removing any content related to E5/E6 (exam artifacts, documentation, or source links).
- Before upgrading Bootstrap or switching to a different CSS framework.
- For permissions or credentials (none stored here) or hosting changes to GitHub Pages.

## Example fixes (concrete snippets) 💡
- Fix toggler attribute:
  - Before: `<button ... data-toggle="collapse" data-tarfet="#navbar" ...>`
  - After:  `<button ... data-toggle="collapse" data-target="#navbar" ...>`
- Fix relative path in `index.html`:
  - Before: `<link href="../css/cv.css" rel="stylesheet">`
  - After:  `<link href="css/cv.css" rel="stylesheet">`
- Fix malformed tag in `pages/cv.html`:
  - Before: `</<p>` → After: `</p>`

---
If anything here is unclear or you want more automation (linting, pre-commit hooks, GH Actions to run HTML validation), tell me which direction you prefer and I will iterate. 🚀