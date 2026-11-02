---
type: source
title: "How to stop hitting Claude usage limits."
author: "Ruben Hassid"
published: 2026-04-10
ingested: 2026-10-30
source_path: "raw-sources/How to stop hitting Claude usage limits..md"
url: "https://ruben.substack.com/p/how-to-stop-hitting-claude-usage"
tags: [source, clipping, claude, tokens, workflow]
---

# How to stop hitting Claude usage limits.

## Summary
A Substack newsletter listing 23 habits to cut token use in Claude, ranked from least known to most obvious. Its one core idea: each message makes Claude re-read the whole conversation, so cost grows with conversation length — [[concepts/llm-token-economics]].

## Key points
- **Core mechanism:** a token is roughly a word; message 30 re-reads 29 earlier exchanges. The author quotes about 105,000 tokens for a 20-message Cowork session and 232,000 for 30, and a developer who found 98.5% of tokens went to re-reading history. Figures are the author's and no method is shown.
- **Files:** a PDF page costs about 1,500–3,000 tokens and an uncropped screenshot about 1,300, so convert to plain text or markdown and crop images (habit 1).
- **Planning:** plan in Chat, then build the file in Cowork, since file creation uses more of the limit (2); say "ask me questions" and let AskUserQuestion gather detail (3); redo only the broken section and add "no commentary" (5); batch tasks in one message (6); keep a stable prompt structure for partial caching (7).
- **History management:** edit the earlier message instead of sending a follow-up (8); restart from an earlier message (11); summarize and start fresh every 15–20 messages (12); one chat per topic (15).
- **Model and product choice:** match product and model to the task (9, 13); Sonnet or Haiku for simple work, Opus for deep work.
- **Context hygiene:** keep about-me files under 2,000 words (10); do not load whole folders (14); turn off unused search, connectors and extended thinking (16); use Projects for recurring documents (17); use preferences and styles, with Memory off, which is the author's own choice (18); schedule recurring jobs (19).
- **Claude Code:** give a clear scope (20); keep `CLAUDE.md` short and move occasional workflows into Skills, which load on demand (21).
- **Limits and tool fit:** usage limits run on a rolling 5-hour window, so spread sessions (22); use other tools for images and live search (23).

## Evidence and methods
Personal experience plus statements the author attributes to Anthropic ("Anthropic confirmed…") without links, and a few figures with no source. Mostly interface-level tips for Claude chat, Cowork and Code as they stood on 2026-04-10.

## Limitations and caveats
- Vendor behavior, prices and limits change; the plan names, window length and product names were not checked here.
- Promotional elements (a prompt library behind a newsletter signup, share requests). The author pays for the $100 plan and says some advice matters mainly on the $20 plan.
- Some tips conflict with each other by design: habit 18 says to turn Memory off, while a persistent store of context is the idea behind habits 10 and 21.
- Screenshots and video were not viewed.

## Entities and concepts
- [[concepts/llm-token-economics]] — the mechanism and the tactics
- [[topics/obsidian-mcp-integration]] — how this vault is reached from Claude; relevant to the file-conversion and folder-scope habits (inference)

## Related sources and topics
- [[sources/wiki-build-and-restructure-chat-summary]] — this wiki's own `CLAUDE.md` contract and skills, the pattern habit 21 recommends
- [[sources/tiktok-safe-zones-guide-zeely]] — clipped the same day
- [[sources/claude-code-token-saving-guide]] — a later clip on the same subject; differs on how often to reset a session
