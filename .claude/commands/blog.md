---
description: Generate a new SEO-optimized Insight/blog post in the firm's voice
argument-hint: <topic or target keyword>
---

You are writing a new **Insight (blog) article** for Christopher Conwell, CPA PC.
Read `CLAUDE.md` first for brand, voice, and SEO conventions.

Topic / target keyword: **$ARGUMENTS**
(If empty, propose 3 informational long-tail topics relevant to business owners or
high-income individuals and ask which to write.)

## Steps

1. **Pick the keyword.** Choose ONE primary informational long-tail keyword and 2–4
   related "cluster" intents. Favor specific questions owners actually search over
   competitive head terms. State the keyword and cluster before writing.

2. **Outline.** Propose an H1 and 4–7 H2 sections that fully answer the search
   intent. Match the depth of strong ranking content (roughly 900–1,400 words).

3. **Write the page.** Create `insight-<slug>.html` by copying the structure of an
   existing post (e.g. `insight-s-corp-election.html`) — same header, footer, and
   `<head>` boilerplate. Then:
   - Put the body inside `<div class="prose">` using `h2`, `h3`, `p`,
     `ul.bullets`, and `blockquote`.
   - Unique `<title>` (~55 chars, includes the keyword), `<meta name="description">`
     (~155 chars), `<link rel="canonical">`, Open Graph + Twitter tags, and
     `<meta name="theme-color" content="#0b1f3a">`.
   - Include **`Article`** and **`BreadcrumbList`** JSON-LD.
   - Work the primary keyword into the title, H1, the first paragraph, and at least
     one H2 — naturally, never stuffed.
   - Add 2–3 internal links to `advisory.html`, `services.html`, and `contact.html`.
   - End with a short CTA section linking to `contact.html` ("Book a Strategy Call").

4. **Voice check.** Plain, confident, specific. No clichés, no fabricated numbers,
   no invented testimonials. Include a genuine point of view. If you don't have a
   real anecdote, leave a clearly-marked `<!-- TODO: Christopher add a client story -->`
   rather than inventing one.

5. **Wire it in.**
   - Update the matching card on `insights.html` to link to the new post and change
     its link text from "Article coming soon" to "Read insight →".
   - Add the new URL to `sitemap.xml` (`priority` 0.6, `changefreq` yearly).

6. **Verify.** Confirm internal links resolve, tags are balanced, and the JSON-LD is
   valid. Summarize the keyword targeted and the changes made. Do not commit unless
   asked.
