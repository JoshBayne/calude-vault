---
title: Claude Desktop to self-hosted Obsidian vault via MCP over SSH
date: 2026-10-29
type: source
tags: [obsidian, mcp, claude-desktop, docker, portainer, ssh, windows]
---

# Claude Desktop to self-hosted Obsidian vault via MCP over SSH

## Goal

Let Claude read (and optionally write) the Markdown notes in a self-hosted Obsidian vault. The vault runs in Docker on a headless Ubuntu server. The setup must not use paid Claude API calls and must not need a local copy of the vault.

## Final design

- A Portainer stack runs one idle container, `mcp-obsidian`, from the image `mcp/filesystem` (official MCP filesystem server).
- The container mounts the same host folder as the Obsidian container. The mount is read-only (`:ro`) by default.
- Claude Desktop starts the MCP server on demand: it runs `ssh` to the server, and `ssh` runs `docker exec -i mcp-obsidian node /app/dist/index.js /vault`.
- Transport is stdio over SSH. No port is open to the internet. No OAuth is needed.
- Cost: uses the Claude subscription. No API credits.

## Compose file (Portainer stack)

```yaml
services:
  mcp-obsidian:
    image: mcp/filesystem
    container_name: mcp-obsidian
    restart: unless-stopped
    network_mode: none
    entrypoint: ["tail", "-f", "/dev/null"]
    volumes:
      - ${VAULT_PATH}:/vault:ro
```

Deploy in Portainer: Stacks > Add stack > Web editor. Set the stack environment variable `VAULT_PATH` to the host path of the vault. Remove `:ro` to allow Claude to write notes.

Check the server entrypoint exists: `docker exec mcp-obsidian ls /app/dist` (expect `index.js`).

## Claude Desktop config (`claude_desktop_config.json`)

```json
{
  "mcpServers": {
    "obsidian-vault": {
      "command": "ssh",
      "args": [
        "-T",
        "-o", "BatchMode=yes",
        "<user>@<server-ip>",
        "docker exec -i mcp-obsidian node /app/dist/index.js /vault"
      ]
    }
  }
}
```

Restart Claude Desktop fully after each config change. Logs: Claude Desktop MCP log for `obsidian-vault`.

## Windows SSH key setup

1. Create a key in PowerShell: `ssh-keygen -t ed25519` (accept defaults, empty passphrase).
2. Copy the public key to the server (Windows has no `ssh-copy-id`):
   `type $env:USERPROFILE\.ssh\id_ed25519.pub | ssh <user>@<server-ip> "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys"`
3. Test: `ssh <user>@<server-ip> "echo ok"` must print `ok` with no password prompt.
4. Test the Docker command: `ssh -T <user>@<server-ip> "docker exec -i mcp-obsidian ls /app/dist"`.

## Errors seen and fixes

| Error | Cause | Fix |
|---|---|---|
| `spawn sshpass ENOENT` | `sshpass` is not installed, or not in the PATH of Claude Desktop. Not available natively on Windows. | Use SSH key login. Do not use `sshpass`. |
| `Permission denied (publickey,password)` in the Claude log | `BatchMode=yes` blocks password prompts, and no key was on the server. | Install the public key on the server (steps above). |
| `ssh -v` shows every identity file as `type -1` | The key files do not exist in `C:\Users\<user>\.ssh\`. | Run `ssh-keygen -t ed25519`, then copy the key. |
| Docker command needs `sudo` and a password | The SSH user cannot use the Docker socket. | Option A: `sudo usermod -aG docker <user>`. Option B: a sudoers rule that allows only the exact `docker exec` command with `NOPASSWD`, and use `sudo -n` in the config. |

## Limits

- This method works for Claude Desktop only. `claude_desktop_config.json` cannot hold remote server URLs.
- Claude on the web and on mobile connects from Anthropic's servers. It needs a public HTTPS MCP endpoint with OAuth (a custom connector). That is a separate setup.
- The `mcp/filesystem` server only does file operations. It does not know Obsidian features such as backlinks or tags.
- Docker group membership is the same as root access on the server. Keep the SSH key private. Do not store a password in the config file.

## Open items

- Decide: read-only (`:ro`) or read-write vault access.
- Decide whether to add a remote HTTPS connector for claude.ai and mobile.
