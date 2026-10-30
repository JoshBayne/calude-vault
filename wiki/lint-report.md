---
type: maintenance
name: "Wiki lint report"
updated: 2026-10-30
scope: "all 73 files under wiki/ (70 content pages plus overview, index, log), checked against raw-sources/"
---

# Wiki lint report (2026-10-30)

## How this was checked
- Read every file in `wiki/` in full: overview, index, log, 22 source pages, 12 entities, 11 concepts, 25 topics.
- Ran a script over all wikilinks (targets, inbound counts, index coverage, basename collisions).
- Compared wiki claims with the raw files in `raw-sources/` (419 `.md` files, 439 entries in total). Spot-checked: `Chapter 1.6`, `2-4 Trial Balance`, `First Spreadsheet Notes`, `3-0`/`4-0 Lecture Notes`, `Domain-1-Security-Principles`, `Quiz-3/4/5/6-Answers`, `Session 9`, `Wave Echo Cave`, `Delrundian Pact`, `Presentation-notes`, `Gardner's---Ch.-14-15.pdf.md`, `10-29-2026`, `2022-01-14`, the `Sophia…` page and `dynamic pricing`.
- "Newer raw files" check: only seven raw files are dated 2026-10-29 or later (`10-29-2026`, `TikTok safe zones…`, `How to stop hitting Claude…`, `claude-desktop-obsidian-mcp-setup`, `remote-vault-clipper-chat-summary`, `wiki-build-and-restructure-chat-summary`, `Module-8---Hypothesis-Test-an`). All are ingested or already covered. Everything else in `raw-sources/` is dated 2026-10-26. No raw file is newer than the wiki, so staleness below comes from the wiki not absorbing its own newer pages, not from unread newer sources.

## Status of fixes (updated 2026-10-30)
| Item | Status |
|---|---|
| H1 break-even wording | Applied on 6 pages (math topic, break-even concept, error-detection concept, cross-domain, quantitative source, overview). The 2026-10-27 log entry is unchanged. |
| M1 overview | Applied: counts, date, tooling bullet, URNET, links to new pages. |
| M2 `3-0`/`4-0` notes | Applied: networking row, IT source, new Chapter 3–4 section in the financial-accounting topic. |
| M3 ARTS 1304 / MKTG 3301 | Applied on the hub, public-speaking, and two source pages. |
| M4 D&D filename list | Applied. |
| M5 undated present tense | Applied on 5 pages. |
| M6 SMPP "since 2017" | Applied on both entity pages. |
| M7 missing pages | Created `entities/josh-bayne`, `concepts/sovereigns-and-apostles`, `entities/wave-echo-cave`, `concepts/warp-gates-and-montauk-events`; linked from related pages. Not created: Redbrands (low value). `llm-token-economics` now has more inbound links. |
| M8 flat links | Applied: 107 links in 19 topic pages rewritten to folder paths. `log.md` left alone (append-only). |
| L1, L3, L4, L5 | Applied (image count, pact name, privacy tags, duplicate bullet). |
| L2, L6, L7 | Not applied (spelling variant, unreadable syllabus). Evidence gaps and owner judgment calls are unchanged. |

## Summary
| Category | Result |
|---|---|
| Index vs files | Clean. 70 listed, 70 exist, no duplicates, no stale entries. |
| True orphans (no inbound link from any page except index/log) | None. |
| Weakly linked | 2 pages with a single inbound link (see M7). |
| Link targets that do not exist | None. But 107 links in 19 topic pages use flat names (see M8). |
| Contradictions | 1 high (H1), 2 medium (M5, M6), 3 low. |
| Stale claims | 4 medium, 3 low. |
| Missing pages | 5 recommended (M7). |

The report as first written changed only this file, an index line and a log entry. **Fixes were then applied on 2026-10-30** (see Status). The finding text below is kept as written so the evidence stays visible.

---

## High

### H1. The "corrected" break-even values in MATH 1324 `Chapter 1.6` are probably the wrong diagnosis
- **Pages that assert it:** [[topics/math-1324-business-math]] ("Errors found in the source notes"), [[concepts/break-even-and-profit-functions]] ("Conflict inside the source… the arithmetic supports the corrected values"), [[concepts/error-detection-and-controls]], [[topics/cross-domain-connections]], [[sources/uhcl-quantitative-notes]], [[overview]] ("x > 120 vs the computed x > 12"), and the 2026-10-27 log entry.
- **Evidence (raw `Chapter 1.6 Applications of Functions in Business and Economics.md`, lines 45–55):**
  - Problem statement: `C(x)=85x+3600`.
  - Next line: `P(x)=385x-(85x+36000)`. Fixed cost is **36000** here.
  - Then `P(x)=300x-3600`, `p(200)=24000`, `x greater than 120`.
  - 300 × 200 − **36,000** = 24,000 and 36,000 ÷ 300 = 120. Both of the notes' answers are exactly right if the fixed cost is 36,000.
  - So the notes disagree with themselves about the fixed cost (3600 vs 36000). The answers 24,000 and x > 120 are the ones that fit 36,000. The wiki's "correct" values (56,400 and x > 12) only follow if 3,600 is right.
- **Impact:** the wiki states a correction as fact in seven places and uses it as its headline example of "the checking technique found an error in the notes". The evidence does not support picking 3,600. The honest finding is a typo in the fixed cost of the problem statement and one working line, not wrong answers.
- **Same pattern, already handled correctly:** the equilibrium problem states supply `p=15q+20` but the solution uses `+30` throughout. The wiki reports this as a mismatch without declaring one side wrong. Treat the break-even example the same way.
- **Recommended fix:**
  1. In [[topics/math-1324-business-math]] replace the bullet with: "`Chapter 1.6` break-even example: the fixed cost is written 3600 in the problem and 36000 in the next line. The final answers (P(200) = 24,000; x > 120) match 36,000; with 3,600 they would be 56,400 and x > 12. The source is internally inconsistent; the textbook figure was not checked."
  2. Make the matching edits in [[concepts/break-even-and-profit-functions]] (Open questions), [[concepts/error-detection-and-controls]] (last Evidence bullet), [[topics/cross-domain-connections]] (two places), [[sources/uhcl-quantitative-notes]] (Limitations) and [[overview]] (Current synthesis).
  3. Keep the trial-balance example as the lead "checking technique" example. That one is confirmed (see "Verified" below).
  4. Do not edit the 2026-10-27 log entry; the new log entry records the correction.

---

## Medium

### M1. Overview is stale and partly wrong
- **Evidence:**
  - "sixteen collection pages under `sources/`": there are **22** source pages.
  - "roughly 300 Markdown notes": `raw-sources/` holds **419** `.md` files (439 entries); the log says "~450".
  - `updated: 2026-10-29`, but the index and three new pages are from 2026-10-30.
  - The map has no home for the Obsidian/Claude tooling cluster: [[topics/obsidian-mcp-integration]], [[topics/remote-vault-clipper]], [[sources/claude-desktop-obsidian-mcp-setup]], [[sources/remote-vault-clipper-chat-summary]], [[sources/wiki-build-and-restructure-chat-summary]], [[concepts/llm-token-economics]], [[concepts/tiktok-safe-zones]], [[entities/urnet]]. Those log entries each say "`overview.md` was not changed".
  - The "Personal" bullet still describes only 2022 material; the 2026 journal changes the storyline (store closed, marriage, new employer).
- **Why it fires the overview trigger:** a new source cluster (AI/tooling and the 2026 journal) changes the scope and balance of the wiki, and the "Out of scope" sentence no longer describes it.
- **Recommended fix:** add a "Tooling and AI workflow" bullet to the map linking [[topics/obsidian-mcp-integration]], [[topics/remote-vault-clipper]], [[concepts/llm-token-economics]] and [[concepts/tiktok-safe-zones]]; add [[entities/urnet]] to the Personal/work line; correct the two counts; update the date. Not applied here because H1 also changes the same section and I did not want to rewrite it twice.

### M2. `3-0 Lecture Notes` and `4-0 Lecture Notes` are described as unread with unknown subject; they are readable accounting notes
- **Pages:** [[topics/networking]] (sources table: "not read; subject… unverified"), [[sources/uhcl-it-notes]] ("never read, so their subject is unknown").
- **Evidence:** `3-0 Lecture Notes.md` (1,898 bytes) holds "3-0a Minimum Take Aways": accounting period, matching, revenue recognition, the four adjusting-entry types, depreciation, contra assets, vertical analysis. `4-0 Lecture Notes.md` (165 bytes) is three learning objectives (financial statements from adjusted balances, closing entries, the accounting cycle). Both are ACCT 2301 Chapters 3 and 4. The raw `2-4 Trial Balance` also links to `3-0 Lecture Notes` for the adjusted trial balance.
- **Impact:** a wrong "possibly networking" hint remains, and [[topics/financial-accounting]] stops at Chapter 2 although Chapter 3 material exists.
- **Recommended fix:** change the networking row to "Not networking: ACCT 2301 Chapters 3–4 (see [[topics/financial-accounting]])". Add a short "Chapter 3: Adjusting entries" and a one-line "Chapter 4" note to [[topics/financial-accounting]], and fix the matching sentence in [[sources/uhcl-it-notes]]. Source page to update: [[sources/uhcl-accounting-notes]].

### M3. Art history / ARTS 1304 statements were not updated after the 2026-10-29 ingest
- **Pages:** [[topics/uhcl-coursework]] (row "ARTS 1304 … see public-speaking (note) | Not summarized"; no MKTG 3301 row; no link to [[topics/art-history-late-medieval-europe]]), [[topics/public-speaking]] ("Related: ARTS 1304 … Not summarized here"), [[sources/uhcl-communication-and-misc-notes]] ("Gardner's… was not summarized"), [[sources/gardners-art-history-ch14-15]] ("ARTS 1304 is not yet listed there").
- **Evidence:** [[topics/art-history-late-medieval-europe]] and [[sources/gardners-art-history-ch14-15]] now exist. The 2026-10-29 log entry lists "`uhcl-coursework` hub not yet updated with ARTS 1304 and MKTG 3301" as an open issue, and it is still open.
- **Recommended fix:** in the hub, point the ARTS 1304 row to [[topics/art-history-late-medieval-europe]] with coverage "Partial (one textbook extract)", and add an MKTG 3301 row ("Summer 2022; syllabus PDF unreadable, no notes"). Remove the "not summarized" sentence in [[topics/public-speaking]]. Add a dated "Update" line to the other two source pages rather than rewriting them.

### M4. D&D page keeps a "filename-only, unverified" list that later pages verified, and one entry is misfiled
- **Page:** [[topics/dnd-campaigns-and-worldbuilding]], section 2, last bullet: "`Earth`, `Mars`, `Net`, `Soren`, `Gat`, … `The Clan`, … `Dr. Harrison Nguyen`, `TVOM(2)`, `Level-List`".
- **Evidence:** [[topics/sci-fi-setting-uic]] read `Earth`, `Net`, `The Clan`, `Dr. Harrison Nguyen` and others; `Mars`, `Gat`, `Soren` are ink-only there. `Level-List` is a guitar roadmap ([[topics/personal-and-hobbies]]), not sci-fi. The list is stale and contradicts the personal page.
- **Recommended fix:** delete `Level-List` from the sci-fi candidate list; replace the bullet with "See [[topics/sci-fi-setting-uic]] for the verified pages and ink-only files."

### M5. Present-tense personal facts contradict the 2026 journal unless the reader knows the date
- **Pages:** [[entities/bayne-homeworks]] Overview ("Family business where Josh works with his father"), [[topics/people-private]] (Will "works for Josh and his dad… since about 2019"; "Sophia: partner"), [[entities/sophia-bayne]] Overview ("Josh's partner"), [[sources/personal-private-notes]] ("spouse-to-be", "partner").
- **Evidence:** `10-29-2026.md` says the store closed "around 2022" and that Josh and Sophia "got married". The key-facts sections of the entity pages already note this; the opening lines do not.
- **Impact:** a reader of the first paragraph gets the 2022 picture as if current. Not a true contradiction, because each claim was right when written.
- **Recommended fix:** add "as of 2022" or "(until about 2022)" to those opening sentences, and change "partner" to "spouse (married since the 2022 notes; date unknown)".

### M6. The "likely" Sophia ↔ SMPP link rests on a name; a dated detail cuts against it
- **Pages:** [[entities/sophia-bayne]], [[entities/sophias-magical-princess-party]], [[topics/daily-notes-2022]] (princess-party income worry).
- **Evidence:** the website copy in `dynamic pricing` says "Making Magic Real Since 2017" and "Proudly serving South Houston families since 2017" (5 occurrences). The `Sophia…` page says they met in summer 2020. The copy was written in an AI chat and may be placeholder; the wiki does not say whether "2017" is real. The only other support is the journal's 2022-01-18 note that she worried about princess-party income, which does support some involvement.
- **Impact:** the wiki calls the link "likely" without noting the date conflict. Possible readings: Sophia joined or took over later; the 2017 is placeholder copy; or the business is not hers.
- **Recommended fix:** add one sentence to both entity pages: "The site copy says 'since 2017', before the couple met in 2020; whether that is placeholder text is unknown." Keep the link marked as inference.

### M7. Pages that are mentioned repeatedly but missing
Counts are pages (excluding `log.md`) that mention the term.

| Priority | Suggested page | Evidence | Why it adds value |
|---|---|---|---|
| 1 | `entities/josh-bayne` (private; the vault owner) | "Josh" appears on 23 pages; BS in Finance (UHCL) is on 2 pages; the job chain HomeWorks → American National → URNET is split over [[entities/bayne-homeworks]], [[entities/urnet]], [[sources/journal-2026-10-29]] | One place for the author's timeline, and a hub for the Personal cluster. Fixes the fact that the main subject has no page. |
| 2 | `concepts/sovereigns-and-apostles` | Sovereign on 9 pages, Apostle on 8; defined only inside [[topics/arian-and-belotria-gazetteer]]; [[entities/golgum]] and [[entities/nezznar-the-black-spider]] each re-explain it | The campaign's central cosmology; gives the open question "did Nezznar and Golgum coordinate?" a home. |
| 3 | `entities/wave-echo-cave` (include the Delrundian Pact) | Wave Echo Cave on 7 pages, Delrundian Pact on 6; used as evidence in [[concepts/market-power-and-cartels]], [[entities/delrun]], [[topics/cross-domain-connections]] | Resolves the naming issue in L3 and avoids four partial descriptions. |
| 4 | `concepts/warp-gates-and-montauk-events` | Warp gates and Montauk on 4–5 pages; split between [[topics/dnd-campaigns-and-worldbuilding]] and [[topics/sci-fi-setting-uic]] | The sci-fi premise is described twice with slightly different detail. |
| 5 | `entities/redbrands` | 6 pages | Low value; only if more campaign material arrives. |

Also considered and **not** recommended: SharePoint/Purview (11 pages, but all from unverified AI transcripts; leave in [[topics/work-and-web-projects]]), marginal analysis (10 pages, already the core of [[concepts/opportunity-cost]]), deadweight loss (6 pages, already inside [[concepts/market-power-and-cartels]] and [[concepts/externalities-and-public-goods]]).

Weakly connected pages (not orphans): [[concepts/llm-token-economics]] has exactly one inbound link (from its own source page); add it to the Related pages of [[topics/obsidian-mcp-integration]] and [[sources/wiki-build-and-restructure-chat-summary]]. [[sources/chat-2026-10-29-unread-files-ingest]] has one inbound link, which is fine for a record page.

### M8. Flat wikilinks conflict with the folder-path convention
- **Evidence:** 107 links in 19 topic pages use bare names such as `economics` in double brackets (26 in [[topics/uhcl-coursework]], 9 in [[topics/economics]], 8 in [[topics/dnd-campaigns-and-worldbuilding]]). `log.md` has 31 more. No two files share a basename, so Obsidian resolves all of them; the 2026-10-28 log entry already records this. `CLAUDE.md` asks for folder paths where helpful.
- **Impact:** anything that does not resolve by basename (a static export, a different link checker) would show 107 broken links. My first automated pass flagged exactly these.
- **Recommended fix:** rewrite the 19 topic pages to the `topics/<name>` form; do not touch `log.md` (append-only). Safe and mechanical; list of targets: the 19 topic page names that appear as bare links.

---

## Low

- **L1. Gardner's image count.** [[topics/public-speaking]] says "46 extracted images"; [[sources/gardners-art-history-ch14-15]] says 50 page images, and the raw file contains 50 image references. Change 46 to 50.
- **L3. Two names for one pact.** [[topics/arian-and-belotria-gazetteer]] says Wave Echo Cave is "the lost mine of the Phandelver's Pact", which is text from the published adventure (`Wave Echo Cave.md` line 5), while the campaign's own note calls the agreement the Delrundian Pact. Add "(published-adventure name; the campaign calls it the Delrundian Pact)".
- **L4. Privacy tags.** [[topics/personal-and-hobbies]] uses `privacy: personal`, every other private page uses `private`, and the page contains the firearm and game lists. [[sources/personal-notes]] summarizes journal material but has no `privacy` field. Standardize both.
- **L5. Duplicate bullet.** [[sources/personal-notes]] says the `Level-List`/practice-log one-year gap twice in the same Limitations section. Remove one.
- **L6. Name variants.** The raw files spell the PC "Elaineki" (file name, `_Party`) and "Elaineke" (`Possible Advnture Hooks`). The wiki uses both ([[topics/dnd-campaigns-and-worldbuilding]] vs [[topics/arian-and-belotria-gazetteer]]). Pick the file-name spelling and note the variant once.
- **L7. Course/term evidence.** The raw file `Managerial Accounting – MBA 6035 - Syllabus Acct 2301 Spring 2022 MWF(1).pdf` mixes course codes and a Spring 2022 term, while the hub gives ACCT 2302 as Fall 2022. Unresolved; the PDF is unreadable here.

---

## Verified (checked against raw, no problem)
- **Trial balance:** `2-4 Trial Balance` credits are 900 + 360 + 25,000 + 16,430 = **42,690**; debits sum to 42,600; Fees Earned 16,340 would balance. Wiki claim confirmed; the exact digit swap remains an inference.
- **First Spreadsheet Notes:** journal totals 31,625 balance; the Inventory T-account credit is 8,750 against the journal's 4,375. Confirmed.
- **CO₂ +5.5%** in `Presentation-notes`, **Session 9** as a one-line note, **Domain-1-Security-Principles** as a 112-byte stub, and Brigham `CH01` as 108 bytes: all match the wiki.
- **Journal 2026-10-29** claims (store closed ~2022, American National, URNET, $150k raise, $500k, Victoria) match the raw text.
- **Index:** 70 pages listed = 70 files.

## Evidence gaps (need new raw material, not more wiki edits)
- Original textbook for `Chapter 1.6` (fixed cost 3,600 or 36,000) and for the NetSolutions trial balance (Fees Earned 16,340 or 16,430).
- Unreadable binaries: syllabi (ECON 2302, MBA 6035/ACCT 2301, MATH 1324, FINC 4331/4351, COMM 1315, Env/Energy SP24, MKTG 3301), `Blackboard Homework 1` (.docx), `Brigham_IFM_14e_PPT_CH01.pptx`, `Z-chart-formal.pdf`. Text export or OCR would fix this.
- `Aronoc.save` (417 KB) and `Port of Biscayne.save` (1.9 MB): never read.
- `Quiz-3-Answers` (56 KB) and `Quiz-4-Answers` (130 KB) contain only image references; OCR needed. `Homework-2---Questions(2)` (124 KB) same. `Ch-25/26/27` and `Lean-Accounting-Notes` image-only.
- Business facts nobody can check from the vault: the SBA loan outcome, what URNET does, whether the investment closed, whether SMPP prices are real (the rates are assistant-invented placeholders).
- Claims from the clipped Zeely and Hassid pieces and the SharePoint retention figures are vendor or author statements; they are flagged on their pages and need Anthropic/Microsoft/TikTok documentation if they ever matter.

## Judgment calls for the owner
- [[topics/people-private]] records allegations about named third parties (including sexual conduct) from one person's journal. The page is tagged private. Consider whether it should be shortened or excluded from any shared copy.
- Whether to keep the wiki's habit of recomputing numbers in source notes. It is useful, but H1 shows a recomputation can also pick the wrong side of an ambiguous typo. Record both readings when the source is internally inconsistent.

## Suggested order of work
1. H1 (seven pages, one wording change).
2. M1 overview rewrite, done together with H1 and M5 so the overview is edited once.
3. M2, M3, M4 (stale "unread" claims; small edits).
4. M7 pages 1–3, then M8 link rewrite.
5. Low items in one pass.
