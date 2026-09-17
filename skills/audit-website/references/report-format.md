# The report

The report is the product. Everything before this was research. If the report looks thrown together, the findings do not get acted on, no matter how good they are.

**Start from `report-template.html`.** Read it, copy it, fill every `{{TOKEN}}`, delete the blocks you have nothing for. Do not design a new layout each time. The template is already checked for mobile, for print, and for the case where a lens comes back clean.

---

## Hard rules for the file

- **One self-contained HTML file.** No external stylesheets, scripts, fonts or images. It has to open with no internet, from an email attachment, five months from now.
- **Both screenshots embedded as base64 data URIs**, desktop and phone. Not linked. Resize to about 1200px wide and compress before encoding so the file stays under roughly 5MB.
- **Print works.** The template has a print stylesheet. Do not break it. People forward these to a web developer who prints them.
- **Name the file** `[business-name]-website-audit-[YYYY-MM-DD].html`.

---

## The design is not yours to change

The palette, the type, the spacing and the structure are already set in `report-template.html`. Use them.

White background. Black text. One orange accent, `#FF4500`. That is it.

Do not invent a dark theme, a different accent colour, a gradient, a card shape or a font. A report that looks different every time looks improvised, and an improvised-looking report does not get acted on. The tokens are at the top of the template:

```
--ink:#0D0D0D  --body:#3A3A3A  --soft:#505050  --faint:#909090
--line:#E8E2D9  --bg:#FFFFFF  --panel:#F8F6F2
--accent:#FF4500  --good:#0E7A4A  --warn:#B8860B  --bad:#CC3600
```

If you find yourself writing new CSS, stop. Fill the tokens, repeat the blocks, delete what you do not need.

## Screenshots

The screenshots section is optional and it is all or nothing.

Keep it only if both images are embedded as base64 data URIs inside the file. If you could not capture them, or the tool saved them to disk instead of giving you the bytes, **delete the whole section** and put one line in the caveats box saying the screenshots are not embedded and why.

Never ship empty frames, a file path, or a link to an image on your own machine. The person opening this file cannot see your disk.

---

## Order, which is not negotiable

1. **Masthead** — business, URL, date, score ring, verdict box.
2. **Fix these three this week.** The whole value of the report. Nothing above it.
3. **The two screenshots**, desktop and phone, side by side.
4. **The seven lenses** — score table first, then the findings under each lens.
5. **What I couldn't check.** Never silently omit a failed check.
6. **The later pile**, honestly labelled as not urgent.
7. **What to do next** — the named handoff.

The reason "the three" sits above the detail: an owner reads the top of a report and skims the rest. Put the money at the top.

---

## How a finding is written

Three parts, always, in this order. The template enforces the shape.

**What's there.** Quote it. Actual text from the actual page, in the monospace box. `Your title tag currently reads "Home | Welcome"`.

**What it costs.** In enquiries or money, not in rules. "That is the line Google shows in search results. Right now it tells someone searching for a mobile detailer in Edmonton nothing at all, so they click the next result."

**The fix.** Write the replacement, do not describe it. `Change it to: "Mobile Car Detailing in Edmonton | Star Wash"`. If it is code, give the code.

A finding with no fix is not a finding, it is a complaint. Cut it.

### Severity
Every finding gets `sev-high`, `sev-med` or `sev-low`. Use them honestly. If everything is high, nothing is.

- **High** — costing enquiries right now.
- **Med** — costing some, or will as they grow.
- **Low** — worth doing, nobody is losing money over it today.

---

## The score

Show the breakdown table so the number is not a black box. Set `{{SCORE_DASH}}` to `SCORE × 3.39` then a space then `339`, so the ring matches the number. A 62 is `210 339`.

Bar colour classes: leave the class off above 70%, use `mid` between 40 and 70, `low` below 40.

Do not be generous. A 54 that leads to three real fixes beats a flattering 85.

---

## Tone

Write to the owner, not to a developer. Second person. Short sentences.

No "leverage", "unlock", "game-changer" or "supercharge". No em dashes.

Translate every technical term on first use, in the same sentence: "your H1, which is the one big headline at the top of the page".

Be direct about bad news and immediately constructive. "This site is invisible to Google right now, and here is the one line that fixes it" is the shape.

Do not pad. If a lens found nothing wrong, use the "Nothing to fix here" line and move on. That is a good result and it makes the findings that do matter more believable.

---

## What not to put in it

- No made-up traffic numbers, load times, rankings or conversion rates. If you did not measure it, it goes in the caveats box.
- No "best practices" with no specific change attached.
- No thirty item list presented as equally urgent.
- No praise that is not true. If the design is dated, do not open with "great looking site".
- No placeholder left in. Search the finished file for `{{` before you hand it over.
