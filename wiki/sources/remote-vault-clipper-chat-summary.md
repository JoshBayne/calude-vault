---
type: source
title: "Remote Vault Clipper: build a web clipper that writes to a self-hosted Obsidian vault"
author: "Claude, with the vault owner (chat session)"
published: 2026-10-29
ingested: 2026-10-29
source_path: "raw-sources/remote-vault-clipper-chat-summary.md"
tags: [obsidian, chrome-extension, web-clipper, local-rest-api, docker, swag, nginx]
---

# Remote Vault Clipper: build a web clipper that writes to a self-hosted Obsidian vault

## Summary
A write-up of a chat session that built **Remote Vault Clipper**, a fork of the MIT-licensed Obsidian Web Clipper. The fork sends each clip as a Markdown file over HTTPS to the Local REST API plugin, which runs in the Obsidian app inside the owner's `linuxserver/obsidian` container. The session also found why the owner's SWAG URL failed the connection test and supplied a SWAG proxy file for a separate API subdomain.

## Key points
- The clipper's source is MIT-licensed, but the Obsidian name, logo and icons are not. The fork therefore has its own name and icon.
- The save uses `PUT` with `If-None-Match: *` for new notes (adds ` 1`, ` 2` on a collision), `PUT` for overwrite, `POST` for append, and read-then-`PUT` with `If-Match` for prepend.
- The URL and API key stay in `chrome.storage.local`; plain `http://` is refused for public hosts.
- The Local REST API binds to `127.0.0.1` by default; in Docker it must be `0.0.0.0`.
- The reported error came from a URL that pointed to the desktop page (ports 3000/3001), not to the API (27124). The fix is a separate SWAG subdomain with no extra authentication layer, because that layer would take the `Authorization` header or return a login page.
- Both proxy examples (Caddy and SWAG) forward only `GET /` and `GET|PUT|POST /vault/…`.

## Evidence and methods
Evidence comes from the session: the upstream source code, the Local REST API OpenAPI file and source, the linuxserver documentation, unit tests (24 pass), a headless-Chromium run of the real built extension through real Caddy to a fake API server, and an `nginx -t` plus end-to-end run of the SWAG file in a SWAG-like setup. The plugin's static checker flagged every bundle; a stricter scan showed these were false positives on the `function(` keyword.

## Limitations and caveats
- Not tested against the real Local REST API plugin, the owner's container or the owner's real SWAG instance; the SWAG test used stub include files.
- Update 2026-10-29 (later in the same session): the owner confirmed that the SWAG route works after using the host IP in the proxy file instead of the container name and publishing port 27124 on the container. The raw note was written before this report and was not changed; see [[topics/remote-vault-clipper]].
- Images are not uploaded; notes keep the web image links.
- Domain names and addresses in the raw note are placeholders.

## Entities and concepts
- [[topics/remote-vault-clipper]] — the project page drawn from this source.

## Related sources and topics
- [[sources/claude-desktop-obsidian-mcp-setup]] — an earlier session about a different route into this vault (MCP over SSH).
- [[topics/obsidian-mcp-integration]] — the MCP route; this source adds a second, write-oriented route through the REST API plugin.
