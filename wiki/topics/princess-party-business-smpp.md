---
type: topic
name: "Princess party business website (SMPP)"
updated: 2026-10-28
sources: 1
source_pages: ["[[sources/business-and-work-notes]]"]
tags: [topic, business, website, smpp, princess-party]
status: ingested-partial
---

# Princess Party Business Website (SMPP)

Planning notes for a website for a **children's character-entertainment company** (princess parties; the pricing file references *sophiasmagicalprincessparty.com*, i.e. "SMPP", in the South Houston area). Notes are a mix of page-by-page design plans (December 2021) and later AI-assisted build sessions. Technical details and related automation live in [[topics/work-and-web-projects]]; the Bulma components used are listed there too.

## Site plan (the "mainPages")
- **Home Page** (`Home Page`): hero banner with navbar and a slideshow of cut-out princess images on a transparent background; a short "why book with us" section with review cards (Google/Facebook/Instagram); a "where can you have princesses come" section (weddings, receptions, corporate events, parades, not only birthdays); a quick-contact block (phone and socials); a mission statement; a "What's new?" section with cards for recent photos or events.
- **Gallery**: curated best photos mixing party, photoshoot and event images.
- **Contact**, **FAQ** (pre-answer common questions), **Pricing** (varied cards with price brackets; higher-priced packages with face painting or small gifts).
- **Characters** (`Characters`): index linking to bios/galleries for each character page: Tinker Fairy, Arabian Princess, Latina Princess, Bayou Princess, Snow White, Sleeping Beauty, Scottish Princess, Sailor Prince, Cinderella (and a movie-dress variant), Little Mermaid (and human form), Prince Charming, Rapunzel, Polynesian Princess, Beauty Princess, Snow Princess, Snow Queen.
- **Cast Page**: list of working team members with individual pages for experience/bios; a popup-card-with-dimmed-background pattern from a competitor's site is the inspiration.

## Design notes
- **General Design Ideas**: wants dress fabrics and textures as page backgrounds but finds the hard edge where background meets content "forced"; a white overlay washes out the fabrics. Considering a softer gradient or accepting a compromise.
- **Logo Idea**: add a subtle loop animation to the crown (a "ding" or fairy-shimmer every few seconds) as a low-bandwidth touch.

## AI-assisted build sessions (saved transcripts)
- `dynamic pricing` (~112 KB, fully read 2026-10-29): interactive pricing calculator. Types: princess, K-pop, impersonator. Durations: 30 min, 1 hr, 2 hr (3+ hr was removed). Performers: up to 4 for princess, 3 for K-pop, 1 for impersonator. Base $150 / $225 / $350; extra performer $100 / $150 / $200; K-pop +$50; impersonator +$75. **These rates were invented by the assistant** because the real pricing page would not load; they are not the business's prices. Details: [[sources/smpp-and-sharepoint-ai-transcripts]].
- `lightbox` (~170 KB, fully read): `characters.html` with 23 characters (18 princess, 3 K-pop, 2 impersonator), outfit lightbox, "featured outfit" highlight class, filter bar, imgbb image links that are still **placeholders**. Page names overlap with well-known studio characters while the footer says they are original; consider an IP check.

## Sources summarized

| Source | Summary |
|---|---|
| `Home Page`, `Gallery`, `FAQ`, `Pricing`, `Characters`, `Cast Page` | Page-by-page plans described above. |
| `General Design Ideas`, `Logo Idea` | Design reflections. |
| `navbar`, `card`, `large hero banner` | Bulma component references (CSS). |
| `dynamic pricing`, `lightbox` | AI build transcripts, fully read ([[sources/smpp-and-sharepoint-ai-transcripts]]). |
| `Contact` | One-line plan for a contact page. |
| 18 character files (e.g. `Cinderella`, `Snow White`, `Rapunzel`, `Tinker Fairy`) | Read; all are empty tag-only stubs ([[sources/empty-stub-and-unreadable-files]]). |
| `Drag Guess Who` | Unrelated to this business: a list of drag performers for a guess-who game ([[topics/personal-and-hobbies]]). |
