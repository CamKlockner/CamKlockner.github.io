# Project context for Claude

## What this is

Cam Klockner's personal site and writing portfolio — a bio page plus a
growing list of his articles. Plain static HTML/CSS, hosted free on GitHub
Pages.

**Live at:** https://camklockner.github.io/

This is the real, published site. Because the repository is named
`camklockner.github.io`, GitHub serves it at that bare address with no path
after it.

## Who you're working with

Cam is 72, retired from a career in construction dewatering, now writing
(including a novel, *WOLF Awakens*). He was competent in BASIC and FORTRAN
~50 years ago (punch-card era) and is learning modern tooling as he goes.

How to work with him:
- Explain what the code does in plain language as you write it — he wants to
  understand the pieces, not just receive them.
- He often works from his **phone**, so he may not be able to drag files
  around or run commands locally. Files reach this repo by being attached in
  chat.
- Show rendered results (screenshots) rather than only describing them.
  Playwright + Chromium are available in the session:
  `NODE_PATH=$(npm root -g)` and
  `chromium.launch({ executablePath: '/opt/pw-browsers/chromium' })`.

## Structure

```
index.html                  homepage: bio, article list, copyright footer
style.css                   shared styling for every page
images/profile.jpg          his photo (circular frame on the homepage)
published/articles/*.html   the articles, one file per article
```

Conventions:
- Filenames lowercase-with-dashes (`carrying-a-story-for-33-years.html`).
- `published/` means "ready for the world."
- Articles are **HTML only** in this repo. Cam keeps the Markdown/source
  masters on his own computer under `Documents > Writing > Articles`; those
  are the editable originals, this repo holds the published rendering.

## Adding an article

1. Cam supplies the article (attached file, or pasted text).
2. Create `published/articles/<slug>.html` following the existing pages:
   - `<link rel="stylesheet" href="../../style.css">`
   - `<a class="back" href="../../index.html">&larr; Back to home</a>`
   - `<header>` with `<h1>` title and
     `<p class="subtitle">Topic &mdash; Cam Klockner, MON DD, YYYY</p>`
   - `<article>` with the body, closing with the italic line
     *R. Campbell Klockner writes about engineering, technology, and tools
     that reshape how we work.*
3. Add an `<li>` link to the Articles list in `index.html` (newest first).
4. Commit and push to `main`. GitHub Pages redeploys within a minute or two.

## Deployment

GitHub Pages serves the `main` branch, root folder. The repo must stay
public for free Pages hosting. Pushing to `main` updates the live site.

## Known rough edges

- The homepage has a `<footer>` copyright line but `style.css` has no
  `footer` rule, so it renders with browser defaults. Article pages have no
  footer at all. Worth unifying if Cam wants it.
- There is no build step: each article is hand-written HTML. Generating the
  HTML from Markdown automatically would be a sensible future improvement.

## Discussed but not done yet

- **Meta description / SEO** — deliberately deferred until there are more
  articles to write descriptions against. The obsolete
  `<meta name="keywords">` approach is understood to be dead; what matters is
  real page content, `<title>`, and a meta description.
- **Google Search Console submission** — deferred until the site is more
  substantial. This is the actual lever for getting indexed.
- **Subscribe form** — needs a third-party service (Buttondown, Mailchimp);
  a static site cannot store email addresses itself.
- **Likes / comments** — same constraint; giscus (comments stored in GitHub)
  is the natural fit for a site hosted this way.
- **Custom domain** (e.g. `cam-klockner.com`) — would need DNS records at a
  registrar plus the "Custom domain" field in Pages settings. Not bought yet.
- **Auto-posting new articles** to X/Twitter, Facebook, Medium — a longer-term
  goal. Would use GitHub Actions or a service like Zapier.

## History

An earlier practice repo, `Cam_Test-2026-07-24`, is where the site was first
built and is now retired. Everything live comes from this repository.
