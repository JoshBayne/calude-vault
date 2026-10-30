---
title: "Practical workflow for reducing token usage in Claude Code while preserving session continuity. Includes compacting strategies, CLAUDE.md structure, modular context management, and prompt engineering tips."
source: "https://gist.github.com/artemgetmann/74f28d2958b53baf50597b669d4bce43"
author:
  - "[[262588213843476]]"
published:
created: 2026-10-30
description: "Practical workflow for reducing token usage in Claude Code while preserving session continuity. Includes compacting strategies, CLAUDE.md structure, modular context management, and prompt engineering tips. - claude-code-token-saving-guide.md"
tags:
  - "clippings"
---
This is a personal reference workflow for minimizing token usage while maintaining project continuity across Claude Code (Sonnet 4 with file access).

---

## ✅ Setup: Populate `CLAUDE.md`Claude loads `CLAUDE.md` automatically at session start.

Keep it under **5k tokens**. Claude uses this as project memory.

### Example prompt to Claude:```
Populate and maintain CLAUDE.md with all relevant project-wide context so you can resume work efficiently without me repeating context each session. Include:
- Project summary & active features
- Tech stack
- Code style & naming conventions
- Known bugs and next TODOs
- Test scenarios we haven’t completed yet (if any)
Keep it under 5k tokens total.

If it becomes impossible to keep all relevant info under 5k tokens, split less critical sections into separate files under the docs/ directory. For example, if there are details about a future system version (e.g., MK2), create a separate markdown file like docs/mk2_notes.md instead of bloating CLAUDE.md.
```

---

## 🛍 Session Workflow### 🖚 End of Session1. Run:
```
/compact Focus on code samples and API usage
```

(You can change the focus as needed — e.g., "design decisions" or "test coverage, or just /compact, but will have more fluff and save less on tokens")

2. Prompt Claude:
```
Append that summary to docs/progress.md
Also save a standalone summary to session_summary.md
```
3. **Do NOT run `/clear` unless you want to reset everything.**
	- It's safer to just exit or start a new chat.
		- Session will stay available if you want to revisit it later.

### 🆑 Start of Session- Start new chat
- Load:
```
@CLAUDE.md
@docs/progress.md
@session_summary.md (optional)
```

---

## 🔁 Every ~40 Messages- Run:
```
/compact Focus on code samples and API usage
```
- Prompt Claude:
```
Save that summary to session_summary.md
```

This keeps the working context tight and avoids token bloat.

---

## 📁 FYI: Structured Project LogsMaintain `progress.md`, `log.md`, etc. for running session history.

### Log Workflow:- Update at end of each session
- Claude can read it at session start
- Load it manually with `@progress.md` if needed

**Pro tip:** Keep logs in `docs/` and only load when needed.

---

## 📆 FYI: Modular File Context with `@file` ReferencesInstead of pasting long blocks:

- Split reusable info into standalone `.md` or `.yaml` files
- Load on demand via `@filename.md`

Good for:

- Command syntax
- API docs
- Configs / routes / edge cases

---

## 🎯 FYI: Prompt Engineering for Token EfficiencyWrite like a spec. Be precise.

**Bad:**

> Hey can you fix this bug?

**Good:**

> Fix the off-by-one bug in `utils.py` line 12 that causes the last item to be skipped. Input: list of ints. Output: adjusted list. Keep type hints.

Other tips:

- Ask grouped questions instead of one-by-one
- Avoid redundant background unless necessary

---

## 🧹 Summary- Use `CLAUDE.md` for persistent context (≤ 5k tokens)
- End sessions with `/compact`, then log to `progress.md` and optionally `session_summary.md`
- Start sessions by loading only needed files
- Compact every ~40 messages to keep things clean
- Use modular files and focused prompts to minimize token load

Keep it lean. Let Claude handle memory. You just keep shipping.