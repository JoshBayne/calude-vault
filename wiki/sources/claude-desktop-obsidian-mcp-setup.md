---
type: source
title: "Claude Desktop to self-hosted Obsidian vault via MCP over SSH"
author: "Claude, with the vault owner (chat session)"
published: 2026-10-29
ingested: 2026-10-29
source_path: "raw-sources/claude-desktop-obsidian-mcp-setup.md"
tags: [obsidian, mcp, claude-desktop, docker, portainer, ssh, windows]
---

# Claude Desktop to self-hosted Obsidian vault via MCP over SSH

## Summary
A write-up of a chat session that connected Claude Desktop to the owner's self-hosted Obsidian vault. A Portainer-managed container runs the official `mcp/filesystem` MCP server with the vault mounted. Claude Desktop starts the server on demand through `ssh` and `docker exec`, using stdio. No port is exposed and no API credits are used.

## Key points
- The design is one idle container (`mcp-obsidian`) plus a `claude_desktop_config.json` entry that runs `ssh ... docker exec -i mcp-obsidian node /app/dist/index.js /vault`.
- The vault is mounted read-only (`:ro`) by default; removing `:ro` lets Claude create and edit notes.
- Password login through `sshpass` failed on Windows (`spawn sshpass ENOENT`); SSH key login is the working method.
- Three setup errors were hit and fixed: missing `sshpass`, `Permission denied (publickey,password)` from `BatchMode=yes` with no key installed, and a Docker socket permission problem that needed either docker-group membership or a narrow sudoers rule.
- The web and mobile Claude apps cannot use this setup; they need a public HTTPS MCP endpoint with OAuth.

## Evidence and methods
Evidence comes from the session itself: the Claude Desktop log lines, an `ssh -v` log showing every identity file as `type -1`, and the user's report that the Docker command needed `sudo`. The `/app/dist/index.js` entrypoint was taken from the public Dockerfile of the MCP filesystem server and is meant to be confirmed with `docker exec mcp-obsidian ls /app/dist`. Whether the final config works end to end is not recorded in the session.

## Limitations and caveats
- Final success is not confirmed in the source; the last reported state was the Docker `sudo` problem.
- The `mcp/filesystem` server does only file operations; it does not understand backlinks, tags or the graph.
- Docker group membership is equal to root on the server; the sudoers option is narrower.
- Host names, user names and addresses were replaced by placeholders in the raw note.

## Entities and concepts
- [[topics/obsidian-mcp-integration]] — the working design, steps and troubleshooting drawn from this source.

## Related sources and topics
- [[topics/work-and-web-projects]] — other saved Q&A and scripting notes from the same owner.
