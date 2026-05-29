# Changelog

Notable changes to the *Money, Mastered* series. Newest first.

The most rapid growth has been in **Book 5 (Technical Analysis)** — see its own progression below.

---

## 2026 — Book 5 expansion timeline

The single-session growth of Book 5, captured for the record. Each entry below was one batch of commits.

| Milestone | Pages | Chapters | Words | Real charts | Notable additions |
|---|---:|---:|---:|---:|---|
| Scaffold + front matter | — | front only | — | — | Cover, copyright/risk, roadmap, 18-chapter TOC, welcome |
| Parts I–V complete | 88 | 18 | ~17,400 | 13 SVG cartoons | Foundations through risk management + honest truth |
| Real charts retrofit | 88 | 18 | ~17,400 | **14** real | Replaced every SVG cartoon with real OHLC charts (golden cross, Meta gap, scanned candlestick patterns…) |
| Part VI — Schools of Thought | 146 | 26 | ~32,500 | 18 | Dow / Wyckoff / Elliott / Fibonacci / Ichimoku / P&F / Breadth & Sentiment / Intermarket |
| Part VII — Case Studies | 213 | 32 | — | 24 | 1929 · 1987 · 2000 · 2008 · 2020 · 2022 — each on real S&P 500 data |
| Part VIII — Specialised Techniques | — | 35 | — | — | Harmonic patterns · Volume & Market Profile · Heikin-Ashi / Renko |
| Part IX — Practice & Code | — | 38 | — | — | Backtesting properly + Python · Workbook (60+ exercises) · Python Companion |
| Part X — Specialised Markets | 240 | 42 | ~51,700 | 29 | Trade Campaign · Crypto · Futures · Statistical Foundations + Strategy table |
| Wyckoff / Elliott / breadth charts | 250 | 42 | ~53,300 | 32 | Real Wyckoff schematic on COVID bottom, real Elliott impulse on 2020-21 SPY, real breadth divergence pre-2022 top |
| Case-study TA overlays | 264 | 45 | ~56,100 | 38 | 50/200-MA overlay on every Part VII chart + RSI on 1987; Common Mistakes appendix; Quick Reference Card |
| **Current** — Reader Paths + Concept Index | **~275** | **47** | **~58,500** | **38** | Reader Paths preface (six goal-based reading paths); proper alphabetical Concept Index |

---

## Other books

### Book 1 — Money, From Zero
- Added the compound-interest formula `FV = P(1+r)^n` with a worked numeric calculation.
- Replaced the SVG hockey-stick with the real growth of $1 in the S&P 500 from 1927 → today (log scale).
- Added Fisher real-return calculation; Rule of 72 verified against ln(2)/ln(1.08); annuity formula proving the Anya-vs-Ben example.

### Book 2 — Where to Put Your Money
- Added worked total-return calculation (income + growth).
- **The expense-ratio drag calculation** — a sub-1% fee costs ~22% of a 30-year portfolio, worked numerically.
- Bond current-yield see-saw calculation.
- Dollar-cost averaging proof: average cost ($7.62) beats average price ($8.25).

### Book 3 — How the Market Works (India edition)
- Itemised ₹50,000 trade cost calculation (brokerage / STT / exchange / SEBI / stamp / GST = ~₹59.32).
- Real Reliance Industries candle anatomy in ₹ (bullish 31 May 2021, bearish 24 Jan 2022).
- Real Nifty 50 Q1-2024 candlestick chart with volume.
- Free-float index-construction worked example.

### Book 4 — Fundamental Analysis
- Already had real Apple FY2023 SEC data; left unchanged in the recent expansion rounds.

### Repo infrastructure
- Landing page (`index.html`) in broadsheet editorial style listing every book with cover thumbnail and Read/Download buttons.
- Per-book cover thumbnails rendered from each PDF's first page.
- `netlify.toml`, `_headers`, `_redirects` — deployment configs for Netlify and Cloudflare Pages.
- `DEPLOY.md` — step-by-step deployment guide for all four options (Cloudflare Pages recommended).
- `PROMPT-TEMPLATE.md` — reusable Claude prompt for setting up the same publishing layer on any HTML-book repo.

---

## Methodology notes

**Real data sources.** All US-market charts are pulled from the Nasdaq.com chart API (no key required, browser-User-Agent header). Indian-market charts and long-history S&P 500 (1927+) come from `yfinance`. The IBM-only Alpha Vantage demo key is available as a backup. Yahoo Finance's `query1` API was blocked from this IP throughout (HTTP 429); Stooq's daily-history endpoint started requiring a captcha API key in mid-2025.

**Chart rendering.** All charts in Book 5 are rendered with `mplfinance` (custom market-colour palette: bullish = ink `#1E1A15`, bearish = gold `#8A6A23`, white background, DejaVu Serif). The chart-generation scripts live in `charts/` and the data CSV cache in `chartdata/`. Both directories are `.gitignore`'d because the data is reproducible from the API calls.

**Verification.** Every figure in Book 5 is listed in the **Charts Index** back-matter with its instrument and date range. Readers with the Python Companion (Ch 38) can reproduce every chart from scratch using the same data sources.

---

*Updated at the end of each major commit batch. For the full commit log see `git log --oneline`.*

## 2026 — Book 8 first release (series complete)

| Milestone | Pages | Chapters | Parts | Notable additions |
|---|---:|---:|---:|---|
| Book 8 — Building &amp; Protecting Wealth initial release | 90 | 18 | 5 | The capstone of the series |

**Coverage**: Part I — The Wealth Equation (income/savings rate/time with the dominance-of-savings-rate worked table, net worth and the ratios that matter, debt as accelerator or destroyer with Arun's mortgage-payoff vignette, the emergency fund). Part II — The Big Decisions (buy vs rent with the 5% rule and a worked 10-year comparison, insurance against ruin with a complete stack, career capital as the largest asset, children &amp; education with the "your retirement before their college" principle and the empirical research on private K-12). Part III — Building Through the Life Cycle (the 20s with Ravi's systems-establishment vignette, the 30s/40s accumulation playbook with glide-path table, the 50s consolidation decade, the 60s+ decumulation with Arun's three-bucket COVID test). Part IV — Protecting &amp; Transferring (the four documents every adult needs, the Williams-Preisser generational-wealth causes, philanthropy via DAFs and CRTs, the three legacies). Part V — The Examined Financial Life (the question of enough with the Vonnegut-Heller story, and a closing one-page synthesis across all eight books).

**Series complete**: 8 books, ~1,170 pages, ~210,000 words, all real data, all original prose, all hosted publicly on GitHub Pages.

---

## 2026 — Book 7 first release

| Milestone | Pages | Chapters | Parts | Notable additions |
|---|---:|---:|---:|---|
| Book 7 — Derivatives, Tax, Psychology &amp; Safety initial release | 89 | 18 | 5 | The defensive volume of the series |

**Coverage**: Part I — Derivatives Without the Mystique (forwards, futures, options calls/puts, options strategies, how derivatives go wrong — with Vikram options-income disaster vignette and Barings 1995 disaster sidebar). Part II — Tax Without the Headache (income streams, short-term vs long-term capital gains with worked deferral calc, tax-advantaged accounts revisited, TLH in practice with wash-sale traps, international and estate including PFICs and step-up in basis). Part III — Psychology, Your Real Adversary (the dozen biases with Barber-Odean evidence, the nine-stage emotional cycle, the IPS-driven anti-fragile habit stack — with Ravi's March-2020 vignette). Part IV — Safety, Recognising the Cons (the five universal markers applied to Madoff, Ponzi vs. pyramid mechanics with Saradha/PACL/Sahara case studies, modern variants from rug pulls to pig-butchering to FTX, the salesperson-disguised-as-advisor problem with Priya's ULIP vignette). Part V — A Defensive Framework (the eight-question checklist, two-minute monthly review, annual review, written prohibitions).

**Cross-references** to Books 1-6 throughout: Seven Principles card revisited from Book 1; Book 5 Chapter 18 Vikram vignette echoed in Chapter 5; Book 6 asset-location framework re-grounded in Chapter 8.

---

## 2026 — Book 6 first release

| Milestone | Pages | Chapters | Words | Real charts |
|---|---:|---:|---:|---:|
| Book 6 — Funds, SIPs & Portfolios initial release | 93 | 18 + appendices | ~17,500 | 4 |

**Coverage**: Portfolio Foundations (MPT, risk-adjusted return) · Asset Allocation (three-fund, glide paths, international) · Implementation (ETFs, factor investing, SIPs, rebalancing) · Tax-Efficient Investing (asset location, tax-loss harvesting) · Decumulation (4% rule, dynamic withdrawal, sequence-of-returns risk) · A Complete Worked Retirement Plan.

**Real charts**: real IBM-vs-S&P concentration risk, computed efficient frontier from real US data, sequence-of-returns simulation (Retiree A vs Retiree B), savings trajectory of the worked plan.

**Cross-references** to Books 1-5 throughout: compound math in Book 1 Ch 8, indexing evidence in Book 2 Ch 14, intermarket regime in Book 5 Ch 32, risk management in Book 5 Ch 17.
