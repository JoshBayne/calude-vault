---
type: source
title: "Practical workflow for reducing token usage in Claude Code while preserving session continuity"
author: "GitHub user artemgetmann (from the gist URL; the clipped author field holds only a number)"
ingested: 2026-11-01
source_path: "raw-sources/Practical workflow for reducing token usage in Claude Code while preserving session continuity. Includes compacting strategies, CLAUDE.md structure, modular context management, and prompt engineering.md"
url: "https://gist.github.com/artemgetmann/74f28d2958b53baf50597b669d4bce43"
tags: [source, clipping, claude, tokens, workflow]
---

# Practical workflow for reducing token usage in Claude Code

## Summary
A short personal gist, clipped on 2026-10-30, on keeping token use low in Claude Code without losing context between sessions. Its idea is to hold project memory in small files and load only what a session needs — [[concepts/llm-token-economics]].

## Key points
- **`CLAUDE.md`:** Claude loads it at session start, so keep it under 5k tokens. Include the project summary, tech stack, conventions, known bugs, next TODOs and open test scenarios. Move less critical detail into files under `docs/`.
- **End of session:** run `/compact` with a stated focus, append the summary to `docs/progress.md`, and save a standalone `session_summary.md`.
- **Do not `/clear`** unless you want to reset everything. The author says to exit or start a new chat instead, because the session stays available.
- **Start of session:** open a new chat and load `@CLAUDE.md`, `@docs/progress.md` and, optionally, `@session_summary.md`.
- **Every ~40 messages:** run `/compact` again and save the summary.
- **Modular context:** keep reusable material such as command syntax, API docs and configs in separate files, and load them with `@filename` instead of pasting.
- **Prompts:** write like a spec, with the file, line, input and output. Group questions and drop needless background.

## Evidence and methods
The author's own working routine. No measurements, token counts or comparisons are given. The 5k and ~40-message figures are rules of thumb.

## Limitations and caveats
- Personal reference note, not vendor documentation. Nothing was checked against Anthropic's documentation.
- It names "Sonnet 4", so it describes an older version of Claude Code. Commands and session behavior may have changed.
- No publication date in the clipping; only the clip date, 2026-10-30.
- The clipping damaged some of the formatting: headings run into the following text, and the emoji are not meaningful.

## Entities and concepts
- [[concepts/llm-token-economics]] — adds Claude Code session tactics
- [[topics/obsidian-mcp-integration]] — another route for reaching this vault from Claude (context only)

## Related sources and topics
- [[sources/claude-usage-limits-guide-hassid]] — the other clipped token guide; agrees on short `CLAUDE.md` files, differs on when to compact or restart
- [[sources/wiki-build-and-restructure-chat-summary]] — this wiki uses a similar pattern: a short contract plus files loaded on demand (inference)
