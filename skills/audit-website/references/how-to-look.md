# How to actually open the site

The point of this skill is that it looks. Everything here is about getting real evidence before writing a word.

## Order of preference

1. **A browser tool** (Claude in Chrome, the built-in browser, or Playwright). Best, because it renders JavaScript. Many small business sites are page builders where most of the content only exists after JS runs, and a plain fetch sees an empty shell.
2. **Fetch the HTML** if no browser is available. Workable for titles, meta, headings, links. Not reliable for content, and useless for schema.
3. If neither works, say so and stop. Do not audit a site you could not open.

## The two screenshots

Take both. They are frequently different websites.

- Desktop: 1440 x 900
- Phone: 390 x 844

Take them **above the fold**, not full page. The first screen is what the five second test is about. A full page screenshot hides the actual problem by showing content the visitor never scrolled to.

Wait for fonts and images before shooting, or you will report layout problems that do not exist.

## What to pull from the page

With a browser, in the page context:

```js
({
  title: document.title,
  desc: document.querySelector('meta[name=description]')?.content || null,
  canonical: document.querySelector('link[rel=canonical]')?.href || null,
  robots: document.querySelector('meta[name=robots]')?.content || null,
  viewport: document.querySelector('meta[name=viewport]')?.content || null,
  h1: [...document.querySelectorAll('h1')].map(h => h.textContent.trim()),
  h2: [...document.querySelectorAll('h2')].map(h => h.textContent.trim()).slice(0, 12),
  tel: [...document.querySelectorAll('a[href^="tel:"]')].map(a => a.href),
  mailto: [...document.querySelectorAll('a[href^="mailto:"]')].map(a => a.href),
  forms: document.querySelectorAll('form').length,
  formFields: [...document.querySelectorAll('form input, form select, form textarea')]
                .filter(i => i.type !== 'hidden').length,
  imgs: document.querySelectorAll('img').length,
  imgsNoAlt: [...document.querySelectorAll('img')].filter(i => !i.alt).length,
  schema: [...document.querySelectorAll('script[type="application/ld+json"]')]
            .map(s => { try { return JSON.parse(s.textContent)['@type']; } catch(e){ return 'unparseable'; } }),
  overflow: document.documentElement.scrollWidth > window.innerWidth,
  scrollW: document.documentElement.scrollWidth,
  bodyFont: getComputedStyle(document.body).fontSize,
  nav: [...document.querySelectorAll('nav a')].map(a => a.textContent.trim()).slice(0, 20),
  words: document.body.innerText.trim().split(/\s+/).length
})
```

Run the overflow and font checks **at 390 wide**, not at desktop. That is where they fail.

## Weight and requests

If the browser exposes network data, total the transferred bytes and count requests. Call out any single image over 500KB by name.

Without network data, list the `<img>` sources and check the big ones with a HEAD request. Report what you measured, not an estimate.

## robots.txt and sitemap

Fetch `/robots.txt` and whatever sitemap it names (or try `/sitemap.xml`). Check:
- Is anything important disallowed?
- Is a sitemap referenced?
- Does the sitemap load, and roughly how many URLs?

A `Disallow: /` on a live site is a five alarm finding. Lead with it.

## The pages to check beyond the homepage

Pick two or three from the nav that a buying customer would actually open. Usually services or pricing, then contact. Run the same extraction. You are looking for whether the homepage was the only page anyone ever finished.

## Schema, carefully

`WebFetch` and `curl` strip `<script>` tags, and plugins like Yoast, RankMath and AIOSEO often inject JSON-LD with JavaScript. So:

- In a rendered browser page, the query above is reliable.
- From a plain fetch, it is not. Say "could not verify schema without a rendered browser" instead of reporting it missing.

Reporting "no schema" from a plain fetch is the single most common false finding in automated audits. Do not produce it.

## When the site will not load

- Timeout or 5xx: note it, retry once, and if it fails again that is itself the top finding. A site that does not load has no other problems worth discussing.
- Cloudflare or bot challenge: try the browser tool. If it still blocks, say the audit is partial and name what you could not check.
- Redirects: follow them and note where you landed. An http page that never redirects to https is a finding.
