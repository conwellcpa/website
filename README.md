# Christopher Conwell, CPA PC — Website

A fast, professional, fully responsive marketing website for **Christopher Conwell, CPA PC**, focused on the firm's three core services: **bookkeeping, tax preparation, and tax planning**.

Built as a zero-dependency static site (plain HTML, CSS, and JavaScript) so it loads instantly, costs almost nothing to host, and is easy to maintain.

## Pages

| File | Purpose |
|------|---------|
| `index.html` | Home — hero, services overview, stats, why-us, process, pricing, testimonials, CTA |
| `services.html` | Detailed breakdown of bookkeeping, tax prep, tax planning + supporting services |
| `about.html` | Firm story, values, and credentials |
| `contact.html` | Contact form, contact details, and FAQ |
| `404.html` | Friendly not-found page |

## Project structure

```
.
├── index.html
├── services.html
├── about.html
├── contact.html
├── 404.html
├── css/styles.css      # Design system + all styles
├── js/main.js          # Mobile nav, scroll reveal, counters, form handling
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
| `100 Commerce Street, Suite 400, Springfield, IL 62701` | Your real address |
| `https://www.conwellcpa.com` | Your real domain (in canonical, OG, sitemap, robots) |
| Testimonials (Maria Reyes, James Tran, Diane Whitfield) | Real client reviews (with permission) |
| Stats ($8.4M saved, 96% retention, etc.) | Real, defensible numbers — or remove them |
| Pricing ($300/return, $450/mo) | Your real pricing — or keep "Custom" |

> ⚠️ The statistics, testimonials, and pricing are **illustrative samples**. Replace them with accurate figures before publishing — don't advertise numbers you can't back up.

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
- No external JS dependencies; fonts load from Google Fonts with preconnect.
- SVG logo/favicon and inline icons keep the page lightweight.
- SEO: per-page titles/descriptions, Open Graph tags, JSON-LD `AccountingService` schema, sitemap, and robots.txt.
