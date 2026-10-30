---
type: source
title: "AI transcripts: pricing calculator, character lightbox, investor portal (full read)"
author: "Josh Bayne with an AI assistant (assistant answers not independently verified)"
ingested: 2026-10-29
source_path: "raw-sources/dynamic pricing.md; raw-sources/lightbox.md; raw-sources/investor portal.md"
tags: [source, ai-transcript, smpp, sharepoint, web]
---

# AI transcripts: pricing calculator, character lightbox, investor portal

Full read on 2026-10-29. Replaces the "opening only" notes in [[sources/business-and-work-notes]].

## Summary
Three long chats that produced HTML pages (two for the princess-party site, one for a SharePoint investor portal).

## Key points
### `dynamic pricing`
- Request: add pricing to a package page. Inputs: character type (princess, K-pop, impersonator), duration, number of performers (up to 4).
- The assistant could not load the real pricing page, so it used **its own invented rates**. They are not the business's real prices.
- Final rules in code: base $150 (30 min), $225 (1 hr), $350 (2 hr). Extra performer $100 / $150 / $200 per added person. Premium: K-pop +$50, impersonator +$75, princess $0. Totals: for example, 1 princess, 30 min = $150; 3 K-pop performers, 2 hr = $350 + $400 + $50 = $800.
- Owner changes: remove "3 hours+"; K-pop max 3 performers; impersonator fixed at 1 and the stepper hidden; max time 2 hr for all.
- Inconsistency: the assistant's first summary lists four durations ($500 for 3 hr+) and extra performers up to $275; the saved code (both copies) has three durations. Treat the code as final.
- Page copy: "Making Magic Real Since 2017", South Houston, hours Mon–Sat 9–7, phone is a placeholder. Five named-customer reviews (Google, Facebook) appear on the page; names not copied here. Footer says the characters are original and unaffiliated with studios or theme parks.
- FAQ text on the page: book 2–4 weeks ahead; video messages are an add-on; performers are background-checked (a claim in page copy; not verified).

### `lightbox`
- Request: a page for **23 characters** with a click/tap lightbox showing outfit variants side by side, labels, a "featured outfit" style to drive sales, imgbb images, marketing aimed at parents.
- Result (`characters.html`, pasted twice): 23 cards = 18 princess, 3 K-pop (Luna Star, Sora Shine, Nova Beat), 2 impersonator (Pop Royalty, Diva Supreme). The assistant's summary said 16 + 2 extra princess slots, which matches.
- Filter bar: All, Princesses, K-Pop, Impersonators, Multiple Outfits. Lightbox closes with the X, outside click, or Escape. No swipe or arrow-key navigation.
- Featured outfits: add class `outfit--featured` (gold ring, glow, badge; text from `data-badge`, default "Most Popular"). Colors come from CSS variables.
- Images: all URLs are **placeholders** (`i.ibb.co/placeholder…`), lazy-loaded with fallbacks. Real photos still need upload.
- Observation: many princess names and blurbs match well-known studio characters (for example Arielle, Jasmine, Moana, Mulan, Tinker Bell, Snow White), while the site footer says the characters are original. This may be an IP risk. Not legal advice; ask a lawyer.

### `investor portal`
- Q1: SharePoint has no per-user "who viewed" for a file. Analytics show counts. Per-user detail comes from the Microsoft Purview audit log (admin rights, log must be on). The transcript says E3 keeps 90 days and E5 up to 1 year; These limits may be out of date; I did not check them.
- Q2: a segregated invite-only portal. Steps given: Communication site; break permission inheritance; SharePoint/Entra groups at Read level; external sharing "Specific people"; Entra B2B guests with MFA through Conditional Access; sensitivity labels and IRM; link expiry; audit logging; quarterly access reviews. A licensing table is included. IRM wording is dated; sensitivity labels are the newer control. Verify against current Microsoft docs.
- Then two HTML templates with placeholders (`[Firm Name]`, fake names, fake stats such as $2.4B AUM): (1) investment-fund portal, navy/gold; (2) private-tech-company portal, dark blue, with ARR, runway, cap table, board decks, milestones and a "Schedule a Demo" button pointing at Microsoft Bookings. Each section is marked as a SharePoint web-part zone.

## Evidence and methods
Saved chat text and generated code. Counts above were checked in the code.

## Limitations and caveats
- Prices are placeholders; image links are placeholders; contact data are placeholders.
- Licensing and retention details can change.

## Entities and concepts
- [[entities/sophias-magical-princess-party]]
- [[concepts/price-elasticity-and-total-revenue]] — price tiers (inference)

## Related sources and topics
- [[topics/princess-party-business-smpp]], [[topics/work-and-web-projects]]
- [[sources/business-and-work-notes]]
