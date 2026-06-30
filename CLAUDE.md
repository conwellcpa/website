# CLAUDE.md — Project guide for Christopher Conwell, CPA PC

This file trains Claude Code on how to build, maintain, and grow this website.
Read it before making changes.

## What this is

A fast, zero-dependency **static website** (plain HTML, CSS, JS — no framework, no
build step) for **Christopher Conwell, CPA PC**, a premium **tax strategy and
advisory** firm for **business owners and high-income individuals**.

The site's job: establish credibility, differentiate from commodity tax preparers,
pre-qualify leads, and drive serious prospects to a **strategy call**.

## Brand & positioning

- **Audience:** business owners (S-corps, partnerships, multi-entity), high-income
  individuals (equity comp, K-1s, real estate), founders preparing to exit.
- **Tone:** premium, calm, confident, advisory-led. Authoritative, not salesy.
- **Primary CTA:** "Book a Strategy Call" (→ `contact.html`). Soft qualification
  ("See if we're a fit") is a feature, not a bug — we filter low-value leads.

### Voice rules (important — avoid "AI slop")
- Plain English, written for intelligent clients. Confident, not verbose.
- **No clichés.** Banned: "maximize your refund," "peace of mind," "save big,"
  "one-stop shop," "we've got you covered," exclamation hype.
- **No fabricated numbers.** Do not invent statistics, dollar figures, client
  counts, or testimonials. Every claim must be true and defensible.
- Specificity over adjectives. "S-corp election and reasonable compensation" beats
  "we handle all your tax needs."
- When writing in Christopher's first-person voice, keep it measured and candid —
  he'd rather tell a prospect the truth than win every client.

### Facts of record (keep accurate everywhere)
- Name: **Christopher Conwell, CPA PC**
- Credentials: **CPA licensed in New York State** (transfer to Florida planned —
  update licensure copy when it happens). **M.S. in Taxation & B.S. in Accounting,
  SUNY Old Westbury.** **10+ years advising business owners.**
- NOT an AICPA member — do not claim it.
- Domain: `https://www.conwellcpa.com`
- Phone/email/address in the footer are **placeholders** — see README.

## Tech & conventions

- Pages are standalone `.html` files at the repo root. No templating — the header,
  footer, and `<head>` boilerplate are **duplicated** in each page. When you change
  the nav or footer, change it in **every** page to keep them in sync.
- All styling is in `css/styles.css`, driven by CSS variables in `:root`. Reuse
  existing components (`.card`, `.split`, `.checklist`, `.compare`, `.fit-grid`,
  `.timeline`, `.insight`, `.prose`, `.statement`) before inventing new ones.
- Headings (`h1`, `h2`) use the serif display font (Source Serif 4); body and
  `h3/h4` use Inter.
- JS is one vanilla file, `js/main.js` (mobile nav, scroll-reveal, form). Keep it
  dependency-free.
- Animated sections use class `reveal`; a `<noscript>` block in each page makes them
  visible without JS. Keep both.
- Match the existing code's structure, indentation, and comment style.

## Navigation (must stay identical across all pages)

`Services · Advisory · Process · Insights · About` + CTA button "Book a Strategy Call".
The logo links home; Contact lives in the footer + the CTA.

## SEO conventions (apply to every page)

Every page's `<head>` must include:
- Unique, keyword-aware `<title>` (~50–60 chars) and `<meta name="description">`
  (~150–160 chars).
- `<link rel="canonical">` with the absolute URL.
- Open Graph (`og:title`, `og:description`, `og:url`, `og:image`, `og:type`) and
  `twitter:card`.
- `<meta name="theme-color" content="#0b1f3a">`.
- Relevant **JSON-LD**: `AccountingService` (home), `BreadcrumbList` (interior
  pages), `FAQPage` (pages with an FAQ), `Article` (blog/insight posts).

Other rules:
- Descriptive, keyword-aware `alt` text on meaningful images (decorative SVGs use
  `alt=""`).
- Internal links between related pages (services ↔ advisory ↔ insights ↔ contact).
- Add every new page to `sitemap.xml` with a sensible `priority`/`changefreq`.
- Keep it fast: no heavy dependencies, inline SVG icons, fonts via preconnect with
  `display=swap`. Aim to preserve a ~100 Lighthouse score.

## Keyword strategy (from the growth playbook)

- **Informational keywords → Insights/blog posts.** Long-tail questions owners
  actually search ("when does an s corp election make sense," "reasonable
  compensation s corp"). Avoid head terms.
- **Transactional keywords → service/landing pages** ("tax advisor for s corp
  owners," and once a city is set, "[city] cpa for business owners").
- Target one primary keyword + a small cluster of related intents per page. Work it
  into the title, H1, first paragraph, and an H2 — naturally, never stuffed.

## Adding a blog / Insight post

Use the `/blog` command (`.claude/commands/blog.md`) or follow it manually:
1. Create `insight-<slug>.html` from an existing post as the template.
2. Use the `.prose` container for body copy; keep the standard header/footer.
3. Include `Article` + `BreadcrumbList` JSON-LD, unique title/description/canonical.
4. Add 2–3 internal links (to `advisory.html`, `services.html`, `contact.html`).
5. Replace the matching card on `insights.html` so it links to the new post.
6. Add the URL to `sitemap.xml`.
7. Keep the firm's voice; weave in a real, specific point of view — not generic
   filler.

## Deploying

Static files — host on Netlify, Vercel, GitHub Pages, or Cloudflare Pages. No build
step. See README.md for details and the pre-launch placeholder checklist.
