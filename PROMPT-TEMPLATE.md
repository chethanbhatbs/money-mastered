# Prompt Template — Set up a polished GitHub publishing layer for a book repo

Paste the prompt below into any Claude Code session that has access to a repo containing self-contained `.html` books and matching `.pdf` files. Claude will produce a styled landing page, a proper README, deployment configs, and a deployment guide — all committed and pushed to `main`.

The template is **topic-agnostic** — works for finance, psychology, history, science, philosophy, design, programming, cooking, music — anything published as HTML+PDF books.

Replace the bracketed `<…>` placeholders at the bottom with your actual repo's specifics before sending.

---

## Copy from here ↓

````
Build a GitHub-friendly publishing setup for my HTML book repo. The repo
contains one or more `.html` self-contained book files at the root and matching
`.pdf` files. Each book is a long-form work in a single self-contained HTML
file with embedded fonts and images.

Deliver SIX artifacts, all committed and pushed to the `main` branch:

──────────────────────────────────────────────────────────────────────────────
1. `index.html` — a styled landing page in BROADSHEET EDITORIAL design:

   • Fonts: Fraunces (display, weight 900) for the title, Spectral for body,
     Archivo for small-caps furniture, JetBrains Mono if any code/numbers
     shown. Load from Google Fonts.
   • Palette: --paper #F6F0E2, --ink #1E1A15, --ink-soft #4E483D,
     --accent #8A6A23 (single accent — choose a different accent hex if it
     better suits the subject, but use ONLY ONE), --hair #C9BFA8.
   • Layout: max-width 1200px wrap, generous padding.
   • Structure:
       (a) A broadsheet masthead (small-caps, accent colour, with a 1.5px
           black underline) showing series name on the left and a one-line
           series descriptor on the right.
       (b) A typographic hero: eyebrow "The Series" with thin rules on either
           side; big serif title with ONE word italicised in the accent
           colour; italic Fraunces strapline (max 820px); chip row with 4–5
           category words separated by accent-coloured dots; a horizontal
           row of 4–5 large numeric stats appropriate to the series
           (book count, total pages, total words, and two more honest
           selling-point numbers — e.g. "100% original prose", "0 cost",
           "verifiable sources").
       (c) An italic disclaimer or caveat block with accent left-border —
           tailor the wording to the subject matter (e.g. for finance:
           "Education, not advice"; for medicine: "Educational reference,
           not medical advice"; for philosophy: "An argument, not a creed";
           etc.). If no caveat is appropriate, replace with a brief
           positioning statement instead.
       (d) Section heading bars: small-caps accent kicker on the left,
           large serif H2 on the right, 1.5px black underline.
       (e) A book grid (1 col on mobile, 2 cols at >=780px). Each book card
           has a 140px cover thumbnail on the left and content on the right
           with: small-caps stage label in accent, large serif title, meta
           line in small-caps faint, blurb paragraph, then two buttons —
           primary "Read in browser" (filled ink) linking to the .html,
           secondary "PDF" linking to the .pdf. The flagship / newest book
           gets the full grid width and a 200px cover, slightly raised
           background.
       (f) A "feature page" preview section showing ONE full-size page
           render with an italic caption explaining what it shows.
       (g) An "About / The Design" notes section.
       (h) Footer with small-caps masthead lines.
   • Mobile responsive (single column under 560px).
   • No drop-shadows on cards, no rounded corners, no gradients — keep
     EVERYTHING ink-on-paper. The single accent is the only colour besides
     ink, paper and a few faint greys.

──────────────────────────────────────────────────────────────────────────────
2. Cover thumbnails — render the first page of each book's PDF as a PNG at
   ~600px wide using `pdf2image`. Save into `docs/images/{slug}-cover.png`.
   Also render ONE additional standout page (the strongest single page from
   any book — typically the most visually striking spread) as
   `docs/images/feature-{slug}.png` at ~1400px wide.

   Install `pdf2image` into a venv (don't pollute system Python). Use
   `dpi=160` for covers, `dpi=180` for the feature page, and
   `Image.thumbnail()` to bound the size. The render script can live in
   `scripts/render_covers.py` or be inline in a Bash heredoc.

──────────────────────────────────────────────────────────────────────────────
3. `README.md` — rewrite to include:

   • A pull-quote at the top describing the series in one sentence.
   • One centered `<p align="center">` with the feature-page image
     (640px max width) and an italic caption underneath.
   • A blockquote pointing to `index.html` for the styled landing page.
   • A short positioning / caveat statement appropriate to the subject.
   • A table of EVERY book with columns: Stage · Book Title · Pages ·
     "View HTML" link · "Download PDF" link · Status (✅ Done / Planned).
   • A separate companion-volumes / appendices table if applicable.
   • A "How to read" section explaining the three options
     (browser, PDF, mobile).
   • A "Browser preview (rendering HTML, not source)" section explaining
     the PRIVATE-REPO LIMITATION honestly: htmlpreview.github.io and
     raw.githack.com only work for PUBLIC repos. List the four paths:
       — Make the repo public (free, simplest)
       — GitHub Pages on Pro/Team/Enterprise (paid)
       — Cloudflare Pages (recommended, free, supports private)
       — Netlify (free, supports private)
     Link to `DEPLOY.md` for the step-by-step.
   • A "What's in each book" one-paragraph summary per book.
   • A "How to reproduce / How it was made" section if applicable
     (chart-generation code, source notes, dataset links, etc.).

──────────────────────────────────────────────────────────────────────────────
4. `netlify.toml` — static-site config:

   [build]
     publish = "."
     command = ""

   With three [[headers]] blocks setting Cache-Control on /*.html
   (max-age=300 must-revalidate), /*.pdf (max-age=86400), and
   /docs/images/* (max-age=604800).

──────────────────────────────────────────────────────────────────────────────
5. `_headers` — same caching headers in Cloudflare Pages / Netlify
   flat-file format (works for both).

   `_redirects` — short URL aliases for every book, e.g.:
     /book1            /book1-slug.html                    301
     /book1.pdf        /Book1-Title.pdf                    301
     ... one pair per book ...

──────────────────────────────────────────────────────────────────────────────
6. `DEPLOY.md` — a step-by-step guide for deployment. Document ALL four
   options in this order:
     A. Cloudflare Pages (recommended) — connect GitHub app, pick repo,
        blank build command, root publish dir, click Deploy; resulting URLs
        at https://{project}.pages.dev/ plus short aliases.
     B. Netlify — same flow, resulting URLs at https://{site}.netlify.app/.
     C. GitHub Pages (only on Pro/Team/Enterprise for private repos).
     D. Just make the repo public (and the htmlpreview.github.io URL
        pattern that works once public).

   End with a "Recommendation" paragraph pointing at Cloudflare Pages as
   the cleanest free path to public preview without changing repo
   visibility.

──────────────────────────────────────────────────────────────────────────────

Additional rules:

• Update `.gitignore` if needed to allow `docs/images/*.png` through any
  blanket image-exclusion rule.
• Commit with descriptive messages and end them with the trailer:
    Co-Authored-By: Claude Opus 4.7 (1M context) <noreply@anthropic.com>
• Push to `main`.
• DO NOT use third-party preview services like htmlpreview.github.io in
  README links if the repo is private — they won't work.
• Render the cover thumbnails BEFORE writing `index.html` so the
  references exist by the time the page is committed.
• Open `index.html` locally with `open` (macOS) once everything is pushed,
  for visual verification.

══════════════════════════════════════════════════════════════════════════════
FILL IN WHAT YOU HAVE
══════════════════════════════════════════════════════════════════════════════

Series name:        <e.g. "Mind & Belief" / "The Builders' Library" / etc.>
Title display:      <how the title should appear, with ONE word italicised
                     in the accent colour — e.g. "Mind &amp; <em>Belief</em>">
Strapline:          <one italic sentence describing the series>
Category chips:     <4–5 short words separated by dots, e.g.
                     "Psychology · Consciousness · Belief · Ethics · Mind">
Disclaimer/caveat:  <one sentence appropriate to the subject, or skip>
Accent colour:      <hex, if different from #8A6A23 — choose one that suits
                     the subject; otherwise leave as gold>

Files in repo (one row per book):

  Slug         | Title displayed       | HTML filename        | PDF filename            | Pages | Status
  ──────────────────────────────────────────────────────────────────────────────────────────────────────
  <slug>       | <title>               | <file>.html          | <File>.pdf              | <N>   | ✅ / Planned
  <slug>       | <title>               | <file>.html          | <File>.pdf              | <N>   | ✅ / Planned
  ...

Flagship/newest book (gets full-width featured card):  <slug>

One-paragraph blurb for each book (1–2 sentences each):

  <slug>: <blurb>
  <slug>: <blurb>
  ...

Anything else specific to this repo (chart scripts, source data, conventions):

  <…>
````

---

## How to use it

1. Open Claude Code (or any Claude session with shell + file access) inside the repo.
2. Paste the prompt above.
3. Fill the `<…>` placeholders at the bottom for your specific series.
4. Hit send. Claude will render the covers, build the landing page, write the README and DEPLOY.md, push to `main`, and open the landing page for you to verify.
5. Click through the **Cloudflare Pages** flow in `DEPLOY.md` (about 3 minutes) and you're live with a public URL while keeping the repo private.

---

## What you get

After the prompt runs:
- A single styled `index.html` listing every book with covers and one-click links
- Per-book PDF cover thumbnails under `docs/images/`
- A polished `README.md` with View HTML / Download PDF table for every book
- `netlify.toml`, `_headers`, `_redirects` — configs that work for both Netlify and Cloudflare Pages
- `DEPLOY.md` with step-by-step instructions for all four deployment paths
- Everything committed and pushed to `main`

Total artifact size: about 16 KB of HTML + the cover PNGs (each ~80–200 KB).

---

*This template was extracted from a working session that set it up for the "Money, Mastered" finance book series. It generalises cleanly to any subject — psychology, history, science, philosophy, design, programming — anything published as long-form HTML books with matching PDFs.*
