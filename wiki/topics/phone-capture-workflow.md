---
type: topic
name: "Phone capture workflow"
updated: 2026-11-06
sources: 5
tags: [topic, tooling, workflow, obsidian, git]
privacy: private
---

# Phone capture workflow

## Current synthesis
On 2026-10-30 and 2026-10-31 the owner set out to write notes on an Android phone and push them to this git-backed vault. By the evening of 2026-10-31 it partly worked: six Samsung Notes files arrived as git commits "Inbox: add … from phone" ([[sources/phone-inbox-notes-2026-10-31]]), after seven test commits that afternoon (`first`, `Untitled` and five `test` files). The owner's own account that day says the desktop git plugin was not pulling the pushed files ([[sources/journal-2026-10-30-and-31]]). That night a second, larger batch of 17 older notes went through the same route ([[sources/phone-old-notes-batch-2026-10-31]]), and on 2026-11-01 all of them were present in the desktop vault's `Inbox/`, so the pull now appears to work. The journal does not say what fixed it ([[sources/journal-2026-11-01]]).

**Second route (2026-11-06):** the owner began "Testing the phone obsidian with using gitsync" and wrote "So far it seems to be okay" ([[sources/journal-2026-11-06]]). Git shows the change: from 11:27 that day, commits are titled "Last Sync: <time> (Mobile)", a separate `.obsidian-mobile/` settings folder was added (its daily-notes setting puts new notes in `raw-sources/` with the `archive/Daily Note Template.md` template), and the daily note `2026-11-06.md` was created on the phone. Obsidian itself now runs on the phone, so this is a full vault sync, not the Samsung Notes push.

## Major themes
- **Goal:** write on the phone "on the fly" and have it appear in the vault — [[sources/journal-2026-10-30-and-31]]
- **Route (from git history, not from a design note):** note written in Samsung Notes (frontmatter `source: samsung-notes`, with a `created` timestamp), committed to `Inbox/` with a message "Inbox: add <file> from phone", then the wiki maintainer moves it to `raw-sources/` during ingest, as `CLAUDE.md` requires — [[sources/phone-inbox-notes-2026-10-31]]
- **Timestamps:** `created` is within seconds of the commit, so it records the share time, not the writing date. Old notes therefore look new — [[sources/phone-old-notes-batch-2026-10-31]]
- **Duplicates:** one note was pushed three times, with timestamps added to the later names. Only one copy is in `raw-sources/`. In the later batch `Fathers Love` arrived twice, under two names with identical text; both are in `raw-sources/`, unchanged.
- **Hosting change:** on 2026-10-30 the owner also planned to move the vault off the Docker container to "the Veda drive", with everything syncing from there — [[sources/journal-2026-10-30-and-31]]

## Points of agreement
Both the journal and git history agree that the phone route exists and was in use on 2026-10-31. The 2026-11-01 journal also confirms the later batch.

## Tensions and contradictions
The 10-31 journal says no uploaded files showed up on the desktop; git shows the commits. These can both hold if the pull step failed while the push succeeded (inference).

## Implications
- Notes from the Obsidian mobile app go straight into `raw-sources/`, not `Inbox/`, so a new ingest must check `raw-sources/` by git history as well as `Inbox/`.
- Phone daily notes are named `YYYY-MM-DD.md` (`2026-11-06.md`); desktop daily notes are named `MM-DD-YYYY.md` (`11-02-2026.md`). The two formats do not sort together. Aligning them is the owner's choice; raw files are not renamed.
- When ingesting, Samsung Notes files land in `Inbox/` first, and the wiki's source path may need to point at wherever the file ends up. Treat repeated near-duplicate names as the same note.

## Open questions
- What the "Veda drive" is, and whether the move is complete.
- Which tool does the phone commit (not stated).
- What fixed the desktop pull, and whether it now runs on its own.
- Whether the GitSync route replaces the Samsung Notes route, or both stay in use.

## Related pages
- [[topics/remote-vault-clipper]] — the browser-side input route, with its SWAG and Local REST API setup
- [[topics/obsidian-mcp-integration]] — how Claude Desktop reads the vault
- [[entities/josh-bayne]] — owner
