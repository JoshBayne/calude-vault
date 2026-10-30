---
type: topic
name: "Remote Vault Clipper"
updated: 2026-10-29
sources: 1
aliases: [web clipper fork, obsidian clipper fork]
tags: [obsidian, chrome-extension, web-clipper, local-rest-api, docker, swag]
---

# Remote Vault Clipper

## Current synthesis
Remote Vault Clipper is the owner's Chrome extension. It is a fork of the Obsidian Web Clipper that saves clips into the self-hosted vault over the network. The extension calls the Local REST API community plugin, which runs inside the Obsidian app in the `linuxserver/obsidian` container. Public access goes through the owner's `linuxserver/swag` reverse proxy on a separate API subdomain. See [[sources/remote-vault-clipper-chat-summary]].

## Major themes
- **Data path:** browser extension → HTTPS → SWAG subdomain (`obsidian-api.<domain>`) → `https://<host IP>:27124` (published container port; the container name did not work on the owner's setup) → vault. On the LAN, direct HTTPS on 27124 (trusted plugin certificate) or HTTP on 27123 is possible. — [[sources/remote-vault-clipper-chat-summary]]
- **Save behaviors:** create never overwrites; overwrite, append and prepend follow the clipper templates; daily notes use a configured folder and date format. — [[sources/remote-vault-clipper-chat-summary]]
- **Security choices:** key in local storage only; no plain HTTP to public hosts; proxy forwards only `/` and `/vault/`; desktop GUI ports 3000/3001 must not be public without strong authentication. — [[sources/remote-vault-clipper-chat-summary]]
- **Branding:** the code is MIT-licensed, but the Obsidian marks are not, so the fork has its own name and icon. — [[sources/remote-vault-clipper-chat-summary]]

## Confirmed result
- 2026-10-29: the owner reported that the SWAG route works. Two changes were needed: the SWAG proxy file calls the host IP address of the Docker host, not the container name, and port 27124 of the Obsidian container is published on the host. This is a user report; no logs were seen. — [[sources/remote-vault-clipper-chat-summary]]
- Likely reason (inference, not tested): SWAG and the Obsidian container are not on the same user-defined Docker network, so SWAG could not resolve the container name.
- Security note: the published port must be reachable by SWAG only (LAN-bound, no router forward), because the API key is the only protection on that port.

## Points of agreement
Only one source so far.

## Tensions and contradictions
- An extra authentication layer (basic auth, Authelia, Authentik) protects the desktop subdomain, but on the API subdomain it breaks the bearer key. The API subdomain relies on the plugin's key check and its 10-failures-per-minute block.
- The Caddy example skips certificate verification on the internal hop to the plugin; trusting the plugin CA is stronger but needs more setup.

## Implications
- The connection test must reach port 27124. An HTML reply means the URL points to the GUI or a login page; the extension now reports this.
- The REST route writes through the running Obsidian app, so Obsidian must stay open in the container.

## Open questions
- Is port 27124 bound to the LAN address only, and not forwarded on the router? Not stated.
- Is the vault written by this extension the same vault that the MCP container mounts? Not stated (inference only).
- Should image upload be added?

## Related pages
- [[sources/remote-vault-clipper-chat-summary]] — the source for this page
- [[topics/obsidian-mcp-integration]] — the other route into this vault (MCP over SSH)
- [[topics/networking]] — general networking notes
- [[topics/work-and-web-projects]] — other technical projects and saved Q&A
