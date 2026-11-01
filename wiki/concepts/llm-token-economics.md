---
type: concept
name: "LLM token economics"
updated: 2026-11-01
sources: 3
tags: [concept, claude, tokens, workflow]
---

# LLM token economics

## Definition
Hosted chat assistants meter use in tokens (roughly words or word pieces). Because each reply is generated from the whole conversation so far, cost and limit use depend on conversation length, attachments and enabled features, not just the latest message.

## How it works / key claims
- Every message re-reads all earlier messages, so a long chat is much costlier than the same questions in short chats. The guide's example figures: about 105,000 tokens for 20 messages and 232,000 for 30 — [[sources/claude-usage-limits-guide-hassid]]
- Attachments are expensive: roughly 1,500–3,000 tokens per PDF page and about 1,300 per large screenshot. Plain text or markdown is cheaper — [[sources/claude-usage-limits-guide-hassid]]
- Tactics follow from this: batch requests, edit instead of appending, redo only the broken part, restart or summarize every 15–20 messages, one topic per chat, match model size to task, switch off unused tools, and move recurring context into Projects, `CLAUDE.md` or Skills.
- Limits are described as a rolling 5-hour window, so spreading use across the day helps on lower plans.
- **Claude Code routine:** keep `CLAUDE.md` under about 5k tokens, compact about every 40 messages, write summaries to `docs/progress.md` and `session_summary.md`, and load files with `@filename` only when needed — [[sources/claude-code-token-saving-guide]]

## Evidence and examples
- All figures in the first group come from one newsletter's author and are unverified. The "Anthropic confirmed…" claims have no links — [[sources/claude-usage-limits-guide-hassid]]
- The Claude Code figures are one person's rules of thumb, with no measurements — [[sources/claude-code-token-saving-guide]]
- This vault already uses two of the tactics: a short `CLAUDE.md` contract plus on-demand skills, and plain-markdown notes — [[sources/wiki-build-and-restructure-chat-summary]] (inference that this matches the guide's advice)

## Related concepts
- [[concepts/opportunity-cost]] — spending a limited token budget on one task forgoes others (analogy)

## Open questions and disagreements
- Tip 18 turns Memory off while tips 10 and 21 build persistent context; the guide does not reconcile them.
- **How often to reset:** Hassid says to summarize and start fresh every 15–20 messages; the gist says to compact about every 40 and to avoid `/clear`. They may differ because the first covers Claude chat and Cowork and the second covers Claude Code (inference). Neither gives evidence for its number. Both agree on a short `CLAUDE.md` and loading context on demand.
- Plan limits, window length and product names change; re-check against Anthropic's documentation before relying on them.

## Sources
- [[sources/claude-usage-limits-guide-hassid]] — mechanism, figures and general tactics
- [[sources/claude-code-token-saving-guide]] — Claude Code session routine
- [[sources/wiki-build-and-restructure-chat-summary]] — this vault's own practice
