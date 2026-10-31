---
type: topic
name: "Phone capture workflow"
updated: 2026-10-31
sources: 2
tags: [topic, tooling, workflow, obsidian, git]
privacy: private
---

# Phone capture workflow

## Current synthesis
On 2026-10-30 and 2026-10-31 the owner set out to write notes on an Android phone and push them to this git-backed vault. By the evening of 2026-10-31 it partly worked: six Samsung Notes files arrived as git commits "Inbox: add … from phone" ([[sources/phone-inbox-notes-2026-10-31]]), after about four commits for "test" notes. The owner's own account that day says the desktop git plugin was not pulling the pushed files ([[sources/journal-2026-10-30-and-31]]). Whether that was fixed is not recorded; the commits exist, so the remaining problem is on the desktop side.

## Major themes
- **Goal:** write on the phone "on the fly" and have it appear in the vault — [[sources/journal-2026-10-30-and-31]]
- **Route (from git history, not from a design note):** note written in Samsung Notes (frontmatter `source: samsung-notes`, with a `created` timestamp), committed to `Inbox/` with a message "Inbox: add <file> from phone", then the file ends up in `raw-sources/`. Who or what moves it from `Inbox/` is not documented — [[sources/phone-inbox-notes-2026-10-31]]
- **Duplicates:** one note was pushed three times, with timestamps added to the later names. Only one copy is in `raw-sources/`.
- **Hosting change:** on 2026-10-30 the owner also planned to move the vault off the Docker container to "the Veda drive", with everything syncing from there — [[sources/journal-2026-10-30-and-31]]

## Points of agreement
Both the journal and git history agree that the phone route exists and was in use on 2026-10-31.

## Tensions and contradictions
The 10-31 journal says no uploaded files showed up on the desktop; git shows the commits. These can both hold if the pull step failed while the push succeeded (inference).

## Implications
When ingesting, new phone notes land in `Inbox/` first, and the wiki's source path may need to point at wherever the file ends up. Treat repeated near-duplicate names as the same note.

## Open questions
- What the "Veda drive" is, and whether the move is complete.
- Which tool does the phone commit (not stated) and what moves files from `Inbox/` to `raw-sources/`.
- Whether the desktop pull issue is fixed.

## Related pages
- [[topics/remote-vault-clipper]] — the browser-side input route, with its SWAG and Local REST API setup
- [[topics/obsidian-mcp-integration]] — how Claude Desktop reads the vault
- [[entities/josh-bayne]] — owner
