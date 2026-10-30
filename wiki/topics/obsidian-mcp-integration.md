---
type: topic
name: "Obsidian MCP integration"
updated: 2026-10-29
sources: 2
tags: [obsidian, mcp, claude-desktop, docker, portainer, ssh]
---

# Obsidian MCP integration

## Current synthesis
Claude Desktop can read this vault through a stdio MCP server that runs in a Docker container on the server hosting the vault. The link goes over SSH, so no network port is opened. Claude Desktop is the only Claude client that works this way; the web and mobile apps need a different, public setup. See [[sources/claude-desktop-obsidian-mcp-setup]].

## Major themes
- **Architecture:** a Portainer stack runs an idle `mcp-obsidian` container (image `mcp/filesystem`, `network_mode: none`) that mounts the vault at `/vault`. Claude Desktop runs `ssh <user>@<server> "docker exec -i mcp-obsidian node /app/dist/index.js /vault"`. — [[sources/claude-desktop-obsidian-mcp-setup]]
- **Access level:** the mount is `:ro` by default. Removing `:ro` allows note creation and edits. — [[sources/claude-desktop-obsidian-mcp-setup]]
- **Authentication:** use an SSH key (`ssh-keygen -t ed25519`, then append the public key to `~/.ssh/authorized_keys` on the server). `sshpass` does not work natively on Windows. — [[sources/claude-desktop-obsidian-mcp-setup]]
- **Docker permission:** the SSH user needs Docker access without a password prompt: add it to the `docker` group, or allow only the exact `docker exec` command in sudoers and use `sudo -n` in the config. — [[sources/claude-desktop-obsidian-mcp-setup]]

## Points of agreement
Only one source so far, so there is nothing to compare.

## Tensions and contradictions
- The docker-group fix is simple but gives root-equivalent access; the sudoers rule is narrower but needs the config to use `sudo -n`.
- The server is file-level only. It cannot use Obsidian features such as backlinks or tags.

## Implications
- Notes written to the vault should have clear titles and links, because Claude reads files on demand and does not hold the whole vault in context.
- For claude.ai and mobile, a public HTTPS MCP endpoint with OAuth would be needed. This is inference from the product's connector model, not tested here.

## Open questions
- Does the final config (key login plus Docker access) connect successfully? The source does not say.
- Read-only or read-write vault access?
- Is a remote HTTPS connector worth adding for web and mobile?
- A second route into the vault now exists: the Remote Vault Clipper browser extension writes notes through the Local REST API plugin in the `linuxserver/obsidian` container. Whether that container uses the same vault folder as `mcp-obsidian` is not stated. — [[sources/remote-vault-clipper-chat-summary]]

## Related pages
- [[concepts/llm-token-economics]] — why file format and folder scope matter when Claude reads this vault (inference)
- [[sources/claude-desktop-obsidian-mcp-setup]] — the source for this page
- [[topics/work-and-web-projects]] — other saved Q&A and scripting notes
- [[topics/remote-vault-clipper]] — browser extension that writes clips into the vault through the Local REST API plugin
