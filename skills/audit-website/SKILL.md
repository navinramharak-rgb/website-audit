---
name: audit-website
description: Audit a real website end to end and hand back a prioritized fix list plus a fix-or-rebuild verdict. Use when the user gives a URL and wants it reviewed, or says "audit my site", "review my website", "why isn't my website getting me leads", "people find me and don't call", "is my site any good", "what's wrong with my website", "my site looks dated", "check my site on mobile", "my website isn't converting", or asks what to fix first. Also use before rebuilding a site, to produce the brief. Works for any business, goes deeper for local and service businesses.
---

# Audit a website

Most website advice is a checklist somebody hands over and never applies. This is the opposite: open the actual site, look at it the way a customer does, and come back with a short list of what to fix in what order.

The person running this is usually a business owner, not a marketer. Write everything so it makes sense to someone who has never heard of a meta description. No jargon without a plain-English translation right next to it.

**The rule that matters most: never report a problem you have not seen.** Every finding quotes what you actually found on the page. If a check could not run, say so and say why. An audit full of confident guesses is worse than no audit.

---

## Step 1. Four questions, then start

Ask these together, in one message, before touching the site. Keep them short.

1. What does the business do, in one sentence?
2. Who is the customer, and what makes someone finally buy?
3. When the site works, what do you want the visitor to actually do? (call, book, buy, fill in a form, walk in)
4. Do customers come to you, or do you go to them? Which city or area?

Question 3 is the whole audit. Everything gets measured against whether the site makes that one action easy. Question 4 decides whether the local checks below apply.

If they answer only some of them, go anyway. Do not hold the audit hostage for a perfect brief.

If the user gives no URL, ask for it. If the site is behind a login or does not exist yet, stop and say so.

---

## Step 2. Actually open the site

Read `references/how-to-look.md` before this step. It has the exact browser commands, what to pull from the HTML, and how to handle sites that fail to load.

Do not audit from the URL alone or from memory. Load it.

Collect, at minimum:
- A screenshot at **desktop width** (1440) and at **phone width** (390). Both matter and they are often different sites.
- The rendered HTML of the homepage.
- The two or three pages a real customer would visit next (services, pricing, contact, about).
- Whatever is in `robots.txt` and the sitemap.

Look at the phone screenshot first. For most small businesses the majority of visitors are on a phone, and the phone version is usually the one nobody checked.

---

## Step 3. Seven lenses

Run all seven. Note what you find under each. Do not write the report yet.

### 1. The five second test
Look only at the phone screenshot. Do not read the HTML. Answer:
- What does this business sell?
- Who is it for?
- What am I supposed to do next?

If you cannot answer all three from the first screen, that is the number one finding, above everything else on this page. Say which of the three is missing and quote what the page says instead.

This one test predicts more lost enquiries than every technical issue combined.

### 2. The path to contact
Count the taps from landing to contacting the business. Then check:
- Is a phone number visible on the first screen without scrolling?
- On mobile, is it a real tap-to-call link (`<a href="tel:...">`) or just text?
- Is there one obvious primary action, or four competing ones?
- Does the contact form ask for more than it needs? Every extra field costs replies.
- Does anything say what happens after they get in touch, and how fast?

### 3. Mobile
From the phone screenshot and the rendered page:
- Does anything overflow sideways?
- Is body text under 16px?
- Are tap targets under about 44px, or crowded together?
- Is the header eating the screen?
- Are there popups or chat widgets covering the content?

### 4. Speed
Report what you can actually measure and be honest about the rest. Page weight, number of requests, uncompressed or oversized images, render-blocking scripts, fonts. Name the single biggest offender in plain terms: "your header image is 4MB, which is about forty times bigger than it needs to be."

For a real Core Web Vitals score, point them at PageSpeed Insights rather than inventing numbers.

### 5. Found in search
- Title tag: present, under about 60 characters, says what the business does and where?
- Meta description: present, under about 155 characters, reads like a reason to click?
- One H1 per page, and does it match what the page is for?
- Is the site actually indexable? Check `robots.txt` and any `noindex`.
- Is there a sitemap?
- Images: do they have alt text?
- Are page URLs readable?
- Is the same content sitting on several URLs?

Schema note: you often cannot see JSON-LD through a plain fetch, because many plugins inject it with JavaScript and fetching tools strip `<script>`. Check it in a rendered browser page or say you could not verify it. Never report "no schema found" from a plain fetch.

### 6. Trust
This is the one everybody skips and it is usually why people leave.
- Are there real reviews or testimonials, with names, or none at all?
- Are there photos of the actual work, actual premises, actual people, or only stock images?
- Is there a real address and a real phone number?
- Anything that proves they are established: years in business, licences, insurance, certifications, association memberships?
- Is there any answer to "why you and not the other guy"?
- Is there a visible price, a price range, or at least an explanation of how pricing works?

### 7. Local (only when the answer to question 4 was local)
- Is the city or service area in the title tag and on the homepage?
- Is the full address on the site, in text, matching how it appears elsewhere?
- Is there a map or directions?
- Are there separate pages for each service and each area served, or one page trying to do everything?
- Is the Google Business Profile linked or referenced anywhere?

If the business is local, flag it clearly: **the Google Business Profile is probably doing more work than the website, and it is free.** Point them at the `local-seo` skill for that half of the job. Do not attempt a full local SEO audit here.

---

## Step 4. Score it, honestly

Give a score out of 100, built from the seven lenses, and show the breakdown so it is not a black box. Weight it toward what actually costs money:

| Lens | Weight |
|---|---|
| Five second test | 25 |
| Path to contact | 20 |
| Trust | 15 |
| Mobile | 15 |
| Found in search | 15 |
| Speed | 10 |

Local findings adjust the search score rather than adding a separate bucket.

Do not be generous. A 62 that leads to four real fixes is worth more than a flattering 85. If it is bad, say it is bad, then immediately say what to do about it, in that order.

---

## Step 5. The verdict

Every audit ends with one of two calls, stated plainly.

**Fix it** when the bones are sound: the structure makes sense, it loads, it is on a platform they can edit, and the problems are copy, layout, trust and contact path. Most sites land here.

**Rebuild it** when any of these are true:
- It is not responsive at all, or mobile is fundamentally broken
- It is on a platform nobody can edit any more, or a dead builder
- The structure is wrong for the business (a shop layout for a service business)
- Speed problems are baked into the theme
- The fix list is longer than the rebuild

Say which, say why in two sentences, and give the rough effort either way. If it is a rebuild, the audit becomes the brief: hand the findings to the `build-premium-site` skill rather than starting from a blank page.

Do not hedge. The whole reason someone asks is that they cannot make this call themselves.

---

## Step 6. The report

Read `references/report-format.md` for the exact structure and tone.

Deliver it as a single HTML page, self-contained, with the two screenshots embedded. Keep it something they could forward to a web developer and have it be useful.

Lead with:
1. The score and the verdict
2. **Fix these three this week** — the three highest impact, lowest effort items, each with what to change, why it matters in money or enquiries, and roughly how long
3. Everything else, grouped, ordered by impact

Every finding carries: what you found (quoted), why it costs them, and the specific fix. No finding without a fix.

---

## What to hand off to

- Local business, or "found in search" scored badly → **`local-seo`**. Google Business Profile, service area pages, reviews, citations. Free, and usually a bigger lever than the website.
- Verdict is rebuild → **`build-premium-site`**, with this audit as the brief.
- They want the technical SEO taken much deeper (hreflang, crawl budget, international) → Corey Haines' **`seo-audit`** skill, which is excellent and goes further than this one on that axis.

---

## Things to get right

**Look before you speak.** Every claim traces to something on the page.

**Name the cost, not the rule.** Not "your meta description is missing." Say "Google is writing your search listing for you, and it picked a sentence from your footer."

**Three things, not thirty.** A list of thirty findings gets nothing done. Rank hard, put three at the top, and be clear the rest can wait.

**Say the uncomfortable thing.** If the site looks like 2011, say so kindly and concretely. They paid for this audit with their attention. A polite report that avoids the real problem wastes it.

**Never invent a number.** No made-up load times, traffic estimates, conversion rates or rankings. Measure it or say you could not.
