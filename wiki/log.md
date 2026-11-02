# Log

Append-only chronological record of wiki activity. Entry format: `## [YYYY-MM-DD] operation | Title`

## [2026-10-26] setup | Wiki initialized
- Read `CLAUDE.md` (LLM Wiki schema: raw sources → wiki → schema; operations: ingest, query, lint).
- Confirmed `wiki/index.md` and `wiki/log.md` were empty.
- Created `index.md` skeleton.
- Surveyed `raw-sources/`: ~450 markdown notes plus PDFs and many extracted `.png` images (directory listing exceeds the 1MB connector limit, so discovery was done via filtered search).
- Raw sources are treated as immutable; nothing in `raw-sources/` was modified.

## [2026-10-26] ingest | Economics (ECON 2301/2302)
- Read ~32 files: intro concepts, PPF, trade, Ch. 4 supply/demand, Ch. 5 elasticity, Ch. 11 public goods, exam notes, plus `Chapter 15 notes` and `Chapter 16-17` (found to be microeconomics, not accounting).
- Created [[economics]]. Flagged: three Ch. 5 application notes are empty stubs.

## [2026-10-26] ingest | Financial accounting (ACCT 2301)
- Read ~23 files: Ch. 1–2 notes, journalizing, trial balance, spreadsheet exercise, certifications list, two AP Q&A transcripts.
- Created [[financial-accounting]]. Flagged: NetSolutions trial balance credits sum to 42,690 vs stated 42,600 (likely Fees Earned 16,430 vs 16,340 transposition); inventory T-account vs journal mismatch; `2-3` is an unfinished stub.

## [2026-10-26] ingest | Managerial accounting (ACCT 2302)
- Read Ch. 15–17 accounting notes; `Lean-Accounting-Notes` has no extractable text (ink images only).
- Created [[managerial-accounting]]. Ch. 24–27 and class-exercise files not read.

## [2026-10-26] ingest | Networking and information systems
- Read four networking notes, `Module 1`, `Module 2`, `Domain-1-Security-Principles` (empty stub).
- Created [[networking]] and [[information-systems-and-security]]. Corrected an early wrong claim about `3-0`/`4-0 Lecture Notes` (unread).

## [2026-10-26] ingest | Statistics, math, finance, speaking
- Read Modules 6–7 (DSCI 3321; all worked examples recomputed and verified), MATH 1324 Ch. 1.2–1.3 (minor typos noted), finance stubs and `Loan-Structuring-Presentation`, COMM 1315 notes.
- Created [[statistics]], [[math-1324-business-math]], [[corporate-finance]], [[public-speaking]]. `Gardner's---Ch.-14-15.pdf.md` (~190 KB textbook extract) not summarized.

## [2026-10-26] ingest | D&D campaign and sci-fi setting
- Read `LMoP`, `_Party`, `Delrun`, `Disciples of Null`, `Locations`, `Warp Gates`, `UINSC Montauk`, `Desert Between Worlds`, and Sessions 1–13.
- Created [[dnd-campaigns-and-worldbuilding]] with session timeline. ~80 NPC/location/monster pages unread.

## [2026-10-26] ingest | Business, work and personal notes
- Read princess-party site plans, Bulma snippets, six AI transcripts (heads only for the three large ones: `dynamic pricing`, `lightbox`, `investor portal`), daily/weekly notes, and hobby files.
- Created [[princess-party-business-smpp]], [[work-and-web-projects]], [[daily-notes-2022]] (themes only), [[personal-and-hobbies]]. Private personal lists intentionally skipped.

## [2026-10-26] ingest | Hub and index
- Created [[uhcl-coursework]] hub; rewrote [[index]] as the full catalog with a "not yet covered" table.

## [2026-10-26] lint | Self-check after first pass
- Fixed three inaccuracies introduced while drafting (stray self-link, filename-only guesses on the D&D page, an unverified claim about a Domain-1 variant file).
- Open items: read remaining course files (Ch. 24–27, Brigham decks, hyphenated OneNote chapters, quizzes/exams), individual D&D NPC/location pages, and decide whether to summarize private personal lists.

## [2026-10-27] ingest | Remaining course materials
- Read hyphenated OneNote chapters, `Chapter 1.1`–`2.1`, Chapter 3/4/9/10/11 (public speaking), Chapter 13–14 (economics), DSCI modules and QA slides, quizzes, exam reviews, Ch-24, presentation notes.
- Created [[intermediate-accounting]], [[energy-and-environmental-economics]], [[business-law]].
- Updated [[economics]], [[statistics]], [[math-1324-business-math]], [[managerial-accounting]], [[public-speaking]], [[corporate-finance]], [[uhcl-coursework]], [[index]].
- Corrected: statistics course numbers (DSCI 3321 and 3331 confirmed); removed a nonexistent `Speech 2` row; Presentation files reassigned to environmental economics.
- Flagged errors in source notes: MATH 1324 `Chapter 1.6` (break-even x > 12, P(200) = 56,400), plus minor slips in `1.1`, `1.6`, `2.1`.
- Image-only or empty: `Ch-25/26/27`, `Lean-Accounting-Notes`, most hyphenated chapters, most Brigham decks.

## [2026-10-27] move | Processed files to `raw-sources/processed/`
- Created `raw-sources/processed/` (verified: the connector moves one file per call, and the vault is not reachable from the shell, so moves were done individually).
- **Moved so far: 146 files**, in passes:
  - Pass 1 (48): all economics notes (39; `5-1f`, `5-2`, `5-2b`, `5-2c`, `5-3`, `5-4` were not read and stay) and the first nine accounting files (`_ACCT 2301` through `2-1a Chart of Accounts`).
  - Pass 2 (48): the rest of financial accounting (`2-2` through `2-5`, `First Spreadsheet Notes`, `Types of Accounting Certifications`, `ap-ar`, `ap-ar files`, `Untitled`, `3rd Exam Review`); managerial accounting (Ch. 15–17, the sync-conflict copy, `Lean-Accounting-Notes`, `Ch-24` to `Ch-27`, `Ch-10`, `Ch-11`, `Ch9`, `Intangible-Assets-Class-Exerc`); intermediate accounting (`Chapter-1` to `Chapter-11` and `Chapter-22` PowerPoint shells, the four `Chapter-N-PowerPoint_*` PDFs, Quizzes 1–2).
  - Pass 3 (50): intermediate accounting Quizzes 3–6, `Ex1-Review-Questions`, `Exam3-Review-Handout`; MATH 1324 (`_MATH 1324`, `Chapter 1.1`–`1.6`, `2.1`); public speaking (`_COMM 1315`, `Chapter 2`/`3`/`4`/`9`/`10`/`11`, `Final Notes`, `Speech 1`, `Speech 3`, `Cap Paper`); statistics and QA (Modules 6–8, `Houston-Module-7`, `Z-chart-formal`, `T-chart`, `Chapter-1---Intro-to-QA`, both Decision Analysis files, `Chapter 1`); finance (`Loan-Structuring-Presentation`, `Brigham_IFM_14e_PPT_CH01`, `Risk and Return`, both FINC syllabi, `Syllabus`, `Syllabus-Day-Notes`, `Chapter-2` and four `Chapter-2_*` files).
- Not moved because unread or only partly read: Gardner's extract, `dynamic pricing`, `lightbox`, `investor portal`, `Homework-2---Questions(2)`, D&D and character pages, and other unread files.
- Earlier statements in this log that said moves stopped at `2-1a Chart of Accounts` were true only at the time of the earlier entry.

## [2026-10-27] ingest | Remaining economics, Arian gazetteer, sci-fi setting
- Read the six remaining ECON 2302 Chapter 5 files (two file names I had guessed did not exist; real names found by search). Updated [[economics]] with the linear-demand-curve table and supply-elasticity example (both recomputed and correct). Moved those 6 files to `processed/` (**152 files moved in total**).
- Read ~60 D&D and setting files. Created [[arian-and-belotria-gazetteer]] and [[sci-fi-setting-uic]]; updated [[dnd-campaigns-and-worldbuilding]], [[personal-and-hobbies]] (guitar `Level-List`) and [[index]].
- Notes: `Wave Echo Cave` contains long text from the published adventure, so it is only briefly summarized. Five player-character files (`Petals Lillydew`, `Taegan Sungem`, `Arturas Azzakod`, `Elaineki St. Germain`, `Ginevieve Ginny Hallowisp`) are empty. About 15 sci-fi pages are ink drawings only.
- Deliberately not summarized: `Cady Jarman` and `Will Jarman` (private details about real people). Not yet read: `_Monsters`, `_Initiative Tracker`, princess character pages, `Contact`, Brigham chapters 2+.
- **Not moved yet** (processed but still in `raw-sources/`): the networking, information-systems, environmental economics, business law and history/operations files, the remaining finance shells, and all D&D, sci-fi, business, work and journal files read in this and earlier rounds.

## [2026-10-28] ingest | Existing notes re-ingested into the session-contract layout
- Source: [[sources/uhcl-economics-notes]], [[sources/uhcl-accounting-notes]], [[sources/uhcl-quantitative-notes]], [[sources/uhcl-finance-notes]], [[sources/uhcl-it-notes]], [[sources/uhcl-communication-and-misc-notes]], [[sources/uhcl-environmental-economics-and-law-notes]], [[sources/delrun-campaign-notes]], [[sources/sci-fi-setting-notes]], [[sources/business-and-work-notes]], [[sources/personal-notes]]
- Updated: all 20 earlier flat pages were moved into `wiki/topics/` and given contract frontmatter (type, name, updated, sources, source_pages); body text was left unchanged. New: [[topics/cross-domain-connections]], concepts ([[concepts/opportunity-cost]], [[concepts/decision-analysis-and-regret]], [[concepts/break-even-and-profit-functions]], [[concepts/time-value-of-money]], [[concepts/price-elasticity-and-total-revenue]], [[concepts/market-power-and-cartels]], [[concepts/externalities-and-public-goods]], [[concepts/statistical-inference]], [[concepts/error-detection-and-controls]]), entities ([[entities/aronoc]], [[entities/delrun]], [[entities/golgum]], [[entities/nezznar-the-black-spider]], [[entities/disciples-of-null]], [[entities/united-interstellar-coalition]], [[entities/the-clan]], [[entities/dr-harrison-nguyen]], [[entities/sophias-magical-princess-party]]), [[overview]], and a rewritten [[index]] (50 pages).
- Summary: the user restored all files to the top of `raw-sources/` (the `processed/` folder no longer exists) and moved images to `raw-sources/assets/`; this entry corrects the earlier "move" entries above, which describe moves that were later reversed. Source pages are per note-group rather than per file because of volume. Connections across domains are recorded with each link marked as stated or inferred.
- Open issues: topic page bodies do not yet follow the topic template sections; earlier log entries use operation names (`setup`, `move`) and layouts outside the contract and were not edited; unread files remain (princess character pages, `_Monsters`, `_Initiative Tracker`, MKTG 3301 syllabus, Brigham chapters 2+, full bodies of three large transcripts).

## [2026-10-28] lint | Index, links and orphan check after restructure
- Source: none
- Updated: [[index]], [[overview]]
- Summary: inventoried `wiki/` (11 sources, 9 entities, 9 concepts, 21 topics; `queries/` empty) and matched it to the index with no missing or duplicate entries. Every new page has at least one inbound link from the index and related pages, so no orphans were found. Links to the 20 relocated topic pages are flat names (for example `[[economics]]`) that Obsidian resolves by file name; they were checked against the file inventory by name, not with an automated link scanner, and were not rewritten to folder paths. The overview was created because it did not exist.
- Open issues: no contradictions between pages beyond the documented source errors (trial balance, math break-even), which are preserved on the topic and source pages; recommend converting topic bodies to the template, adding a one-page-per-source split for important individual documents, and filling `queries/` as questions arise.

## [2026-10-29] ingest | Unread files, including private items
- Source: [[sources/smpp-and-sharepoint-ai-transcripts]], [[sources/gardners-art-history-ch14-15]], [[sources/personal-private-notes]], [[sources/empty-stub-and-unreadable-files]]
- Updated: [[topics/princess-party-business-smpp]], [[topics/work-and-web-projects]], [[topics/daily-notes-2022]], [[topics/personal-and-hobbies]], [[entities/sophias-magical-princess-party]], [[sources/business-and-work-notes]], [[sources/delrun-campaign-notes]], [[sources/personal-notes]], [[index]], [[overview]]. New: [[entities/sophia-bayne]], [[entities/bayne-homeworks]], [[topics/people-private]], [[topics/art-history-late-medieval-europe]].
- Summary: read the three large AI transcripts in full (pricing rates are assistant-invented placeholders; lightbox images are placeholders; investor-portal Q&A and two templates). Read the Gardner's OCR extract, all 18 princess stubs, Brigham shells, `_Monsters`, `_Initiative Tracker`, `Contact`, and all daily and weekly notes. Owner approved private items, so people pages, wishlists, the firearm and game lists, and the saved Reddit post are now included and marked `privacy: private`. Earlier entries that said private files were skipped are superseded.
- Open issues: PDF/DOCX/PPTX files and the two `.save` files could not be read through the connector (listed on the empty-and-unreadable page); `uhcl-coursework` hub not yet updated with ARTS 1304 and MKTG 3301; SBA loan outcome unknown; log and index not link-checked by script.

## [2026-10-29] ingest | Chat record of the unread-files ingest
- Source: [[sources/chat-2026-10-29-unread-files-ingest]]
- Updated: [[index]], [[overview]]
- Summary: saved a summary of the 2026-10-29 chat as a private source page (what was read, findings, pages made and changed, open items). No other page changed.
- Open issues: same as the entry above.

## [2026-10-29] ingest | Claude Desktop to self-hosted Obsidian vault via MCP over SSH
- Source: [[sources/claude-desktop-obsidian-mcp-setup]]
- Updated: [[index]]. New: [[topics/obsidian-mcp-integration]].
- Summary: converted a chat session about connecting Claude Desktop to this vault into a raw note (`raw-sources/claude-desktop-obsidian-mcp-setup.md`, host and user names replaced by placeholders), then added a source page and a topic page covering the container design, SSH key setup on Windows and the three errors hit. `overview.md` was not changed.
- Open issues: the source does not confirm that the final config connects successfully; read-only vs read-write vault access and a remote HTTPS connector for web and mobile are undecided; links not checked by script.

## [2026-10-29] ingest | Remote Vault Clipper: build a web clipper that writes to a self-hosted Obsidian vault
- Source: [[sources/remote-vault-clipper-chat-summary]]
- Updated: [[topics/obsidian-mcp-integration]], [[index]]. New: [[topics/remote-vault-clipper]].
- Summary: converted the chat session that built the Remote Vault Clipper extension (fork of Obsidian Web Clipper that writes through the Local REST API plugin) into a raw note (`raw-sources/remote-vault-clipper-chat-summary.md`, domains and addresses as placeholders), then added a source page and a project topic page covering the design, save behaviors, verification and the SWAG subdomain fix. The MCP topic got a cross-link and an open question about whether both routes use the same vault folder. `overview.md` was not changed.
- Open issues: the owner has not confirmed that the SWAG correction works; nothing was tested against the real Local REST API plugin or the real SWAG instance; links not checked by script.

## [2026-10-29] ingest | Remote Vault Clipper: SWAG route confirmed
- Source: [[sources/remote-vault-clipper-chat-summary]]
- Updated: [[topics/remote-vault-clipper]], [[sources/remote-vault-clipper-chat-summary]]
- Summary: the owner reported that the SWAG route works after two changes: the proxy file calls the host IP, not the container name, and port 27124 is published on the Obsidian container. This closes the open item in the earlier entry. The cause (container name not resolved) is an untested inference. The raw note was not edited.
- Open issues: whether port 27124 is LAN-bound and not forwarded on the router; no logs were seen.

## [2026-10-29] ingest | Chat summary: building the wiki and restructuring it to the session contract
- Source: [[sources/wiki-build-and-restructure-chat-summary]]
- Updated: [[index]]
- Summary: summarized the 2026-10-26 to 2026-10-28 chat into a raw note (`raw-sources/wiki-build-and-restructure-chat-summary.md`, no host paths or personal details) and added a source page. It records the connector limits, the build sequence, the switch to the stricter `CLAUDE.md` contract, the restructure result (50 pages on 2026-10-28), findings about the notes and the assistant's own corrections. No topic, concept or entity page changed, and `overview.md` was not changed.
- Open issues: the page counts in the summary are as of 2026-10-28 and are older than the index total; links were not checked by script.

## [2026-10-30] ingest | Daily note 2026-10-29, TikTok safe-zones guide, Claude usage-limits guide
- Source: [[sources/journal-2026-10-29]], [[sources/tiktok-safe-zones-guide-zeely]], [[sources/claude-usage-limits-guide-hassid]]
- Updated: [[entities/sophia-bayne]], [[entities/bayne-homeworks]], [[topics/daily-notes-2022]], [[index]]. New: [[entities/urnet]], [[concepts/tiktok-safe-zones]], [[concepts/llm-token-economics]].
- Summary: ingested three raw files from 2026-10-29. The journal entry (private) added marriage, the Eras Tour TikTok show, the store's closure around 2022 and the URNET job and funding situation. The other two are web clippings: a vendor guide to TikTok overlay layout and a newsletter on cutting Claude token use. `Module-8---Hypothesis-Test-an.md` was also dated 2026-10-29 but was already covered in [[topics/statistics]], so it was not re-ingested. `overview.md` was not changed.
- Open issues: the journal's money, investor and health details are unverified and private; the link between the clipped TikTok guide and Sophia's streaming is inference; the clippings' figures are vendor or author claims; links not checked by script.

## [2026-10-30] lint | Full health check of wiki/ against raw-sources/
- Source: none (audit of all 70 content pages plus overview, index and log; spot checks against `raw-sources/`)
- Updated: [[index]] (added a Maintenance line). New: [[lint-report]]. No content page was edited.
- Summary: index matches the 70 files and there are no orphans or missing link targets. Findings: the "corrected" break-even values for MATH 1324 `Chapter 1.6` are probably the wrong diagnosis (the raw notes use fixed cost 36000 in the working line, which makes 24,000 and x > 120 correct); the overview is stale (22 source pages not sixteen, 419 raw notes, tooling cluster missing); `3-0` and `4-0 Lecture Notes` are readable ACCT 2301 notes, not unread networking; ARTS 1304 and Gardner's statements were not updated; the D&D page's filename-only list is stale; undated present-tense personal facts; five suggested new pages; 107 flat-name wikilinks in topic pages. Verified correct: the trial-balance 42,690 vs 42,600 and the inventory T-account flags.
- Open issues: all recommended fixes in [[lint-report]] are unapplied; the overview was not rewritten because H1 and M1 touch the same section; original textbooks and unreadable binaries are still needed for the evidence gaps.

## [2026-10-30] lint | Applied high and medium fixes from the lint report
- Source: none
- Updated: [[overview]], [[index]], [[lint-report]], [[topics/math-1324-business-math]], [[concepts/break-even-and-profit-functions]], [[concepts/error-detection-and-controls]], [[topics/cross-domain-connections]], [[sources/uhcl-quantitative-notes]], [[topics/financial-accounting]], [[topics/networking]], [[sources/uhcl-it-notes]], [[topics/uhcl-coursework]], [[topics/public-speaking]], [[topics/dnd-campaigns-and-worldbuilding]], [[entities/bayne-homeworks]], [[entities/sophia-bayne]], [[entities/sophias-magical-princess-party]], [[topics/people-private]], plus small edits to several other pages. New: [[entities/josh-bayne]], [[concepts/sovereigns-and-apostles]], [[entities/wave-echo-cave]], [[concepts/warp-gates-and-montauk-events]].
- Summary: corrects the earlier claim (log 2026-10-27, math notes) that the `Chapter 1.6` break-even answers were wrong: the source writes fixed cost as 3600 and 36000, and its answers fit 36,000, so it is recorded as internally inconsistent. Also: Chapter 3–4 accounting notes added; ARTS 1304/MKTG 3301 hub rows; undated 2022 facts dated; 107 flat wikilinks in topic pages rewritten to folder paths; overview refreshed (22 source pages, about 420 notes, tooling cluster); index now lists 74 pages.
- Open issues: Redbrands page not created; spelling variant Elaineki/Elaineke and the unreadable MBA 6035/ACCT 2301 syllabus unresolved; evidence gaps (textbook originals, binaries, `.save` files) unchanged; the owner should decide on the people-private third-party content.

## [2026-10-31] ingest | Daily notes 2026-10-30 and 10-31, and six phone notes
- Source: [[sources/journal-2026-10-30-and-31]], [[sources/phone-inbox-notes-2026-10-31]]
- Updated: [[entities/urnet]], [[entities/sophia-bayne]], [[entities/josh-bayne]], [[topics/personal-and-hobbies]], [[overview]], [[index]]. New: [[topics/film-and-video-ideas]], [[topics/phone-capture-workflow]].
- Summary: two journal entries (investor and payroll wait, vault hosting move, phone-to-git problems) and six Samsung Notes files pushed from the phone on 2026-10-31 (gift ideas, MTG artists and cards, three film and video premises, a book title). The overview got small count and link updates only. The phone route was checked against git history, which shows the pushes arrived.
- Open issues: investor named Steve Trauber on 10-29 but Doug Trauber on 10-30; "Veda drive" unexplained; whether the desktop pull problem is fixed; what the original *The Doll* is; links not checked by script.

## [2026-11-01] ingest | Daily note 2026-11-01 and 17 old phone notes
- Source: [[sources/journal-2026-11-01]], [[sources/phone-old-notes-batch-2026-10-31]]
- Updated: [[topics/film-and-video-ideas]], [[topics/phone-capture-workflow]], [[topics/personal-and-hobbies]], [[topics/people-private]], [[topics/sci-fi-setting-uic]], [[topics/work-and-web-projects]], [[concepts/warp-gates-and-montauk-events]], [[entities/sophia-bayne]], [[entities/josh-bayne]], [[entities/urnet]], [[overview]], [[index]]. New: [[topics/story-ideas]].
- Summary: moved all 17 `Inbox/` files to `raw-sources/` under their original names and ingested them with the new `11-01-2026` journal note. The batch holds fiction, video and meme ideas, a gift list for Sophia, an art list, a book title and a dream. `Fathers Love` and `story idea Fathers Love` are the same note. Corrected the description of raw `youtube ideas`: it is mostly a *Dear Evan Hansen* session, not only a *Home Movies* prompt. Bristol Bend and Rampart were matched to the old and new houses from earlier notes. The overview got small count and link updates only.
- Open issues: Alexey, Seth, Kori, Lydia and Pop are unidentified; "officially behind" is read as late pay by inference; links between the story notes and the sci-fi setting are inference; `created` timestamps give the share time, so writing dates are unknown; the art and book attributions on the source page come from outside knowledge and were not checked.

## [2026-11-01] ingest | Video-essay series plans
- Source: [[sources/video-essay-series-plans]]
- Updated: [[topics/film-and-video-ideas]], [[topics/work-and-web-projects]], [[entities/josh-bayne]], [[overview]], [[index]]. New: [[topics/video-essay-series]].
- Summary: ingested 12 new raw files planning five essays: *Home Movies*, *Seinfeld*, *Ed, Edd n Eddy*, *RENT* and *Dear Evan Hansen*. All 12 were read in full and share one source page. All five are at framework stage with no scripts. Conflicts inside the plans are listed on the topic page and not resolved, including carjacking against mugging in *Seinfeld*. The raw `youtube ideas` file gained only a trailing newline since the last ingest. The overview got small count and link updates only.
- Open issues: show facts were not checked against the episodes or cited articles; URLs were not kept; citation tags in the raw files are broken; *Dear Evan Hansen* has no framework or citation file of its own; whether the essays form one series or two is not stated.

## [2026-11-01] lint | Health check after the phone-note and video-essay ingests
- Source: none (script over all 83 content pages; full read of the 2026-10-31 and 11-01 pages and [[lint-report]]; spot checks against `raw-sources/`)
- Updated: [[overview]], [[index]], [[topics/video-essay-series]], [[topics/film-and-video-ideas]], [[topics/phone-capture-workflow]], [[topics/work-and-web-projects]], [[topics/arian-and-belotria-gazetteer]], [[entities/josh-bayne]], [[sources/journal-2026-11-01]], [[sources/phone-inbox-notes-2026-10-31]], [[sources/empty-stub-and-unreadable-files]]
- Summary: index matches all 83 pages; no broken links, no orphans; `Inbox/` is empty. Fixed: the street number removed from a journal source page, which had contradicted the rule in [[sources/journal-2026-10-29]] that addresses are left out; [[topics/video-essay-series]] marked private because it cites the private journal; three missing "(private)" index labels; index wording that said URNET is run with Josh's father, where the journal says only that Josh works for the father; index order; "written" corrected to "shared" for the phone notes, since `created` is the share time; test-commit count; *Dear Evan Hansen* framework and citation wording; spelling variant Elaineki/Elaineke (L6 in the lint report); frontmatter on four pages; a missing comma in the overview. The overview's unread-material line was updated: 13 of the 17 PDF, DOCX and PPTX files hold extractable text and four PDFs are scans. Their contents were sized, not read. This corrects the view in earlier entries that all of them need a text export or OCR.
- Open issues: the clipping `Practical workflow for reducing token usage in Claude Code…` (created 2026-10-30) was never ingested, and the overview's "two clipped articles" excludes it; 13 readable binaries await ingest, four PDFs need OCR and the `.save` files are undecoded; `updated` dates predate the 2026-10-30 lint edits on about 40 pages; whether [[topics/story-ideas]], [[concepts/tiktok-safe-zones]] and [[sources/tiktok-safe-zones-guide-zeely]] should be private; the people-private judgment call and L7 are unchanged. Claims on older coursework and campaign pages were not re-read this pass.

## [2026-11-01] ingest | Claude Code token-saving gist
- Source: [[sources/claude-code-token-saving-guide]]
- Updated: [[concepts/llm-token-economics]], [[sources/claude-usage-limits-guide-hassid]], [[overview]], [[index]]
- Summary: ingested the clipping that the lint pass found uncovered. It adds a Claude Code routine: a `CLAUDE.md` under about 5k tokens, `/compact` about every 40 messages, progress files, and files loaded on demand. It differs from the Hassid guide on how often to reset (about 40 messages against 15–20); the difference is recorded, not resolved. The overview now says three clipped articles.
- Open issues: no measurements behind either guide's numbers; the gist names Sonnet 4, so it may be dated; not checked against Anthropic's documentation.

## [2026-11-01] ingest | UHCL syllabi and course files (13 PDF, DOCX and PPTX files)
- Source: [[sources/uhcl-syllabi-and-course-files]]
- Updated: [[topics/uhcl-coursework]], [[topics/corporate-finance]], [[topics/public-speaking]], [[topics/energy-and-environmental-economics]], [[topics/math-1324-business-math]], [[topics/financial-accounting]], [[topics/information-systems-and-security]], [[concepts/time-value-of-money]], [[sources/uhcl-finance-notes]], [[sources/uhcl-communication-and-misc-notes]], [[sources/uhcl-environmental-economics-and-law-notes]], [[sources/uhcl-quantitative-notes]], [[sources/uhcl-accounting-notes]], [[sources/empty-stub-and-unreadable-files]], [[overview]], [[index]]
- Summary: text was extracted to a temporary folder and all 13 files were read in full; raw files were not changed. Five syllabi fill in instructors, texts and grading. Corrects the Brigham deck title on [[topics/corporate-finance]] from *Intro to* to *Intermediate Financial Management*. FINC 4331 is a commercial-credit course built on the RMA Credit Essentials material. "LT" is Lewis and Tietenberg and "D" is Dahl. `Cap Paper` is probably the COMM 1315 analysis paper, and several title-only finance files probably belong to FINC 4331 (both inference). The final review shows MATH 1324 went far beyond the notes. The overview got count and status updates only.
- Open issues: the energy syllabus and `Exam-2-Review` disagree on Exam 2's chapters; the rest of the Exam 1 and Exam 2 study guides is still not summarized; equations in the math review were lost in extraction; four scanned PDFs still need OCR, so L7 stays open; the FINC 4351 and 4331 schedules are not in the extracted text; the course behind the Brigham decks is unknown; `Blackboard Homework 1` contains a shared FASB login, kept out of the wiki but still in the raw files.
