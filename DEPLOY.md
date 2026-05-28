# Deployment — getting public preview links without making the repo public

The repo is private. To give readers a public URL to **read the books in their browser** without making the repo itself public, deploy the static site to one of the platforms below. All three are free for this use case and all three auto-deploy on every `git push`.

The repo already contains everything needed:
- `index.html` — the landing page that lists every book with View / Download buttons
- `netlify.toml`, `_headers`, `_redirects` — config that both Netlify and Cloudflare Pages pick up automatically
- All the book HTMLs and PDFs at the root

You just need to click through one of the deploy flows below.

---

## Option A — Cloudflare Pages (recommended)

**Why:** unlimited bandwidth on the free tier, very fast global CDN, no time limits, easy custom-domain support, and excellent for static sites this size.

### Setup
1. Go to <https://pages.cloudflare.com/> and sign in (create a free Cloudflare account if you don't have one).
2. Click **Create application** → **Pages** → **Connect to Git**.
3. Authorise the Cloudflare GitHub app and select the **`chethanbhatbs/money-mastered`** repo (you can grant access to just this one repo).
4. On the build configuration screen:
   - **Project name:** `money-mastered` (or whatever you want — this becomes the URL subdomain)
   - **Production branch:** `main`
   - **Build command:** *(leave blank)*
   - **Build output directory:** `/` *(or just leave as the default root)*
5. Click **Save and Deploy**.

After ~30 seconds you'll have:
```
https://money-mastered.pages.dev/
https://money-mastered.pages.dev/book5             ← short alias (via _redirects)
https://money-mastered.pages.dev/book5-technical-analysis.html
https://money-mastered.pages.dev/Book5-Technical-Analysis.pdf
```

Every future `git push` to `main` triggers a re-deploy automatically.

### Custom domain (optional)
Cloudflare Pages → Custom Domains → Set up a domain → enter your domain (e.g. `books.example.com`). Add the CNAME record they show you to your DNS. Done.

---

## Option B — Netlify

**Why:** mature, simple, generous free tier (100 GB/month bandwidth, plenty for an HTML+PDF site), and the `netlify.toml` config in this repo already targets it.

### Setup
1. Go to <https://app.netlify.com/> and sign in (create a free account if needed).
2. Click **Add new site** → **Import an existing project** → **Deploy with GitHub**.
3. Authorise the Netlify GitHub app and select **`chethanbhatbs/money-mastered`**.
4. The deploy settings are already filled in by `netlify.toml`:
   - Branch: `main`
   - Build command: *(blank)*
   - Publish directory: `.` (root)
5. Click **Deploy site**.

You'll get a URL like:
```
https://money-mastered-xxxx.netlify.app/
https://money-mastered-xxxx.netlify.app/book5
```

You can rename the site under Site settings → Site name to make the URL nicer.

Custom domain: Site settings → Domain management → Add custom domain.

---

## Option C — GitHub Pages (requires paid GitHub plan for private repos)

GitHub Pages can serve from private repos but **only on Pro / Team / Enterprise** plans (~$4/month).

### Setup
1. In the repo's **Settings → Pages**.
2. Source: Deploy from a branch.
3. Branch: `main`, folder: `/ (root)`.
4. Save.

Your site appears at `https://chethanbhatbs.github.io/money-mastered/`.

GitHub Pages doesn't read `netlify.toml` or `_headers`, but the `_redirects` short URLs will not work either — readers will need to use the full filenames. The `index.html` landing page works.

---

## Option D — Just make the repo public (simplest, free)

If you're OK with the repo being public, every existing relative link in `README.md` becomes one-click readable via:
- `https://htmlpreview.github.io/?https://github.com/chethanbhatbs/money-mastered/blob/main/book5-technical-analysis.html`
- `https://raw.githack.com/chethanbhatbs/money-mastered/main/book5-technical-analysis.html`

And the PDFs preview natively in GitHub's viewer. No deployment needed.

---

## Recommendation

For sharing the books with anyone (potential readers, friends, social posts) without making your repo public, **Cloudflare Pages** is the best path. Once configured, you'll have a permanent URL that auto-updates whenever you push changes. Total setup time: ~3 minutes.
