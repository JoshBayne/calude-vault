---
type: overview
updated: 2026-11-01
---

# Wiki overview

## Purpose and scope
A personal knowledge wiki built from the notes in `raw-sources/`: about 445 Markdown notes (plus PDFs, PPTX/DOCX files and about 15,800 images in `raw-sources/assets/`) from university coursework, a small-business website project, saved AI-assistant work conversations, two tabletop-RPG settings, a journal (2021–2022 and four 2026 entries), hobby logs, and write-ups of the owner's Obsidian/Claude tooling projects and two clipped articles. Out of scope: anything not in those notes; no outside research has been added. Many source files are empty shells or image-only, so coverage is uneven (see Open questions).

## Map of the knowledge
- **Coursework** ([[topics/uhcl-coursework]]): business-school courses, grouped by subject. Economics ([[topics/economics]], [[topics/energy-and-environmental-economics]]), accounting ([[topics/financial-accounting]], [[topics/managerial-accounting]], [[topics/intermediate-accounting]]), quantitative methods ([[topics/statistics]], [[topics/math-1324-business-math]]), finance ([[topics/corporate-finance]]), law ([[topics/business-law]]), IT ([[topics/networking]], [[topics/information-systems-and-security]]) and communication ([[topics/public-speaking]]).
- **Work and business**: [[topics/princess-party-business-smpp]] and [[topics/work-and-web-projects]].
- **Games and worldbuilding**: [[topics/dnd-campaigns-and-worldbuilding]], with the fantasy setting in [[topics/arian-and-belotria-gazetteer]] and the sci-fi setting in [[topics/sci-fi-setting-uic]].
- **Tooling and AI workflow**: [[topics/obsidian-mcp-integration]] (Claude Desktop reading this vault over SSH), [[topics/remote-vault-clipper]] (browser clipper writing into it), [[concepts/llm-token-economics]] (clipped guide to Claude limits) and [[concepts/tiktok-safe-zones]] (clipped vendor guide); [[topics/phone-capture-workflow]] covers pushing Android notes into the vault by git.
- **Personal**: [[topics/film-and-video-ideas]] and [[topics/story-ideas]] (creative premises), [[entities/josh-bayne]] (owner profile), [[topics/daily-notes-2022]], [[topics/personal-and-hobbies]] and [[topics/people-private]] (private; included with owner approval on 2026-10-29), with [[entities/sophia-bayne]], [[entities/bayne-homeworks]] (store closed around 2022) and [[entities/urnet]] (current employer, per the 2026 journal).
- **Evidence layer**: 26 source pages under `sources/` record provenance, limitations and flagged errors for each note group.

## Current synthesis
- The same few ideas recur across all domains: trade-offs under scarcity ([[concepts/opportunity-cost]], [[concepts/decision-analysis-and-regret]]), cost and profit logic ([[concepts/break-even-and-profit-functions]], [[concepts/time-value-of-money]]), pricing power ([[concepts/price-elasticity-and-total-revenue]], [[concepts/market-power-and-cartels]]), market failure ([[concepts/externalities-and-public-goods]]) and checking evidence ([[concepts/statistical-inference]], [[concepts/error-detection-and-controls]]). The links, and which are inference, are collected in [[topics/cross-domain-connections]].
- Worked numeric examples in the coursework generally recompute correctly. The exceptions are documented, not silently fixed: a trial balance whose credits sum to 42,690 against a stated 42,600 ([[sources/uhcl-accounting-notes]]), and a break-even example in the math notes whose fixed cost is written 3600 in one line and 36000 in another, so its answers (x > 120, P(200) = 24,000) fit only the 36,000 reading ([[sources/uhcl-quantitative-notes]]).
- The fantasy campaign's central antagonists, [[entities/nezznar-the-black-spider]] and [[entities/golgum]], are both Apostles of the Sovereigns ([[concepts/sovereigns-and-apostles]]; their fight site is [[entities/wave-echo-cave]]); the sci-fi setting is a separate world built around [[entities/united-interstellar-coalition]] and [[entities/the-clan]], with gate lore in [[concepts/warp-gates-and-montauk-events]].

## Key hubs
- [[topics/cross-domain-connections]] — start here for how the pieces relate
- [[topics/uhcl-coursework]] — course-by-course map and caveats about reused file names
- [[topics/dnd-campaigns-and-worldbuilding]] — campaign recap and setting overview
- [[concepts/opportunity-cost]] — the most widely connected concept

## Open questions
- **Evidence gaps:** many files hold no text (managerial accounting Ch. 25–27, Brigham finance decks, Kieso PowerPoint shells, about 15 sci-fi ink pages, empty player-character pages). Original PDFs or OCR would be needed.
- **Unread material:** PDFs, DOCX and PPTX files (syllabi, homework, exam review) and two large `.save` files cannot be read through the vault connector; see [[sources/empty-stub-and-unreadable-files]]. Text exports or OCR would fix this.
- **Placeholders:** the SMPP pricing rates and character image links are placeholders ([[sources/smpp-and-sharepoint-ai-transcripts]]).
- **Unverified assignments:** course ownership of several reused-name files (`Chapter N`) was inferred from content.
- **Private material:** now included, marked `privacy: private`; keep it out of any shared export.
