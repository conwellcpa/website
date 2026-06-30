# Christopher Conwell, CPA PC — Website

A fast, premium, fully responsive website for **Christopher Conwell, CPA PC** — a **tax strategy and advisory** practice for **business owners and high-income individuals**. The site is positioned to establish credibility, differentiate from commodity tax preparers, pre-qualify leads, and drive serious prospects to a strategy call.

Built as a zero-dependency static site (plain HTML, CSS, and JavaScript) so it loads instantly, costs almost nothing to host, and is easy to maintain.

## Positioning

- **Audience:** business owners (S-corps, partnerships, multi-entity), high-income individuals, founders preparing to exit.
- **Tone:** premium, calm, confident, advisory-led — not a low-cost prep shop.
- **Conversion goal:** qualified discovery calls ("Book a Strategy Call"), with soft qualification ("see if we're a fit") to filter low-value leads.

## Pages

| File | Purpose / conversion goal |
|------|---------------------------|
| `index.html` | Home — positioning, preparer-vs-strategist contrast, services, fit/qualification, process preview, client words, insights preview, CTA |
| `services.html` | The three disciplines (planning, preparation, bookkeeping) as one integrated engagement + supporting capabilities |
| `advisory.html` | The differentiator — proactive, multi-year tax strategy and the quarterly planning cycle |
| `process.html` | The engagement path from strategy call to ongoing partner; reduces risk/objection |
| `insights.html` | Authority-building article listing (placeholder articles ready to fill in) |
| `about.html` | Firm philosophy, principles, and credentials |
| `contact.html` | Strategy-call request with light qualification fields + FAQ |
| `404.html` | Friendly not-found page |

## Project structure

```
.
├── index.html
├── services.html
├── advisory.html
├── process.html
├── insights.html
├── about.html
├── contact.html
├── 404.html
├── css/styles.css      # Design system + all styles (serif display headings, premium components)
├── js/main.js          # Mobile nav, scroll reveal, form handling
├── assets/
│   ├── logo.svg        # Header logo
│   └── favicon.svg     # Browser tab icon
├── robots.txt
└── sitemap.xml
```

## Viewing it locally

It's just static files — open `index.html` in a browser, or run a tiny local server:

```bash
# Python 3
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploying

Because it's static, you can host it almost anywhere for free or near-free:

- **Netlify** — drag-and-drop the folder, or connect this repo. Auto-deploys on push.
- **Vercel** — import the repo; no build settings needed.
- **GitHub Pages** — enable Pages on this repo (serve from the branch root).
- **Cloudflare Pages / Amazon S3 + CloudFront** — upload the files.

No build step is required.

## Before you go live — replace the placeholders

The site is fully functional but uses **placeholder business details**. Search and replace these across the `.html` files:

| Placeholder | Replace with |
|-------------|--------------|
| `(555) 014-2025` and `tel:+15550142025` | Your real phone number |
| `hello@conwellcpa.com` | Your real email |
| `72 Bronson Ln, Palm Coast, FL 32137` | Currently the home address (temporary). Swap to the virtual-office address when it's set up, and update the `geo` coordinates in `index.html` JSON-LD to match |
| `https://www.conwellcpa.com` | Your real domain (already set; verify in canonical, OG, sitemap, robots) |
| CPA licensure (`New York State`) | Update if/when you transfer your license to another state (e.g. Florida) |
| Client quotes on Home ("Business owner", "High-income individual") | Real, anonymized client quotes (with permission) |
| Insight article titles on `insights.html` | Your real articles, or trim the list until you publish |

> ⚠️ The client quotes and credentials are **illustrative**. Confirm every credential is accurate and only publish testimonials you have permission to use. There are deliberately **no fabricated statistics or dollar figures** anywhere on the site — keep it that way.

## Making the contact form actually send email

Right now the form shows a confirmation message but does **not** deliver email (it's a static site with no backend). Pick one of these no-code options:

### Option A — Formspree (easiest)
1. Create a free form at [formspree.io](https://formspree.io).
2. In `contact.html`, change the form tag's `action` to your endpoint:
   ```html
   <form class="form" data-contact-form action="https://formspree.io/f/YOUR_ID" method="POST">
   ```
   (When a real `action` is set, `js/main.js` lets the browser submit it normally.)

### Option B — Netlify Forms (if hosting on Netlify)
1. Add `netlify` to the form tag:
   ```html
   <form class="form" data-contact-form name="contact" method="POST" data-netlify="true">
   ```
2. Add a hidden field inside the form: `<input type="hidden" name="form-name" value="contact" />`
3. Netlify captures submissions automatically — view them in your dashboard.

## Customizing the look

All colors, fonts, spacing, and shadows are defined as CSS variables at the top of `css/styles.css` under `:root`. Change the brand colors there and the whole site updates:

```css
--navy-900: #0b1f3a;   /* primary brand color */
--gold-500: #c8a24a;   /* accent color */
```

## Accessibility & performance notes

- Semantic HTML, ARIA labels on nav and icons, keyboard-focus styles.
- Respects `prefers-reduced-motion`.
- No external JS dependencies; fonts load from Google Fonts with preconnect + `display=swap`.
- SVG logo/favicon and inline icons keep the page lightweight.

## SEO & growth playbook

This site is built to rank and convert. Here's what's already in place and what's
left to you (the parts that need your accounts or paid tools).

### Already implemented (on-page & technical)
- Unique, keyword-aware `<title>` and meta description on every page.
- Canonical URLs, Open Graph + Twitter cards, and `theme-color` on every page.
- **Structured data (JSON-LD):** `AccountingService` with services, service area, and
  founder credentials (home); `FAQPage` (contact); `Article` + `BreadcrumbList`
  (insight posts).
- `sitemap.xml` and `robots.txt`, with the sitemap referenced from robots.
- Internal linking between services ↔ advisory ↔ insights ↔ contact.
- Fast, dependency-free pages aimed at a high Lighthouse score.

### The content engine — "blog posts at scale"
- The **Insights** section (`insights.html`) is the blog hub. One full post is live
  (`insight-s-corp-election.html`) as the template; the other cards are stubs ready
  to become real posts.
- A reusable **`/blog` command** lives in `.claude/commands/blog.md`. In a Claude Code
  session, run `/blog <topic or keyword>` and it will draft a new, SEO-optimized post
  in the firm's voice, wire it into `insights.html`, and add it to the sitemap.
- `CLAUDE.md` holds the brand voice and SEO rules so every post stays consistent and
  avoids "AI slop." Edit it to add Christopher's real anecdotes and turns of phrase —
  the more specific the voice, the better the content.

### Keyword strategy
- **Informational keywords → Insight posts.** Target long-tail questions owners
  search ("when does an s corp election make sense," "reasonable compensation s
  corp"). Avoid competitive head terms.
- **Transactional keywords → service/landing pages** ("tax advisor for s-corp
  owners"; once you have a city, "[city] cpa for business owners").
- Use a keyword tool (SEMrush, Ahrefs, or the free Google Keyword Planner) to find
  low-competition terms, then feed them to `/blog` or build a targeted landing page.

### What you need to set up (external)
1. **Google Business Profile** — create/claim it; keep Name, Address, Phone (NAP)
   identical to the site's footer. Biggest lever for local search.
2. **Google Search Console** — verify the domain and submit
   `https://www.conwellcpa.com/sitemap.xml`. Watch for indexing/coverage issues.
3. **Google Analytics 4** — create a property, then add this just before `</head>`
   on each page (replace `G-XXXXXXXXXX`):
   ```html
   <script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
   <script>window.dataLayer=window.dataLayer||[];function gtag(){dataLayer.push(arguments);}
   gtag('js',new Date());gtag('config','G-XXXXXXXXXX');</script>
   ```
   (Tell me your measurement ID and I'll add it to every page for you.)
4. **Off-page / backlinks** — pursue legitimate links only: guest posts on finance/
   small-business sites, HARO/journalist requests, local business directories, and
   reclaiming/repairing broken links. Avoid paid link schemes.

### Before launch — also do these for SEO
- Replace the placeholder NAP (phone, email, address) so it's consistent everywhere
  and matches your Google Business Profile.
- Add a real OG share image (1200×630) and point the `og:image` tags at it.
- Add real `lastmod` dates to `sitemap.xml` as you publish/update pages.
