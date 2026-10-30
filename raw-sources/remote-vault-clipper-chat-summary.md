---
title: "Remote Vault Clipper: build a web clipper that writes to a self-hosted Obsidian vault"
date: 2026-10-29
type: chat-summary
participants: [vault owner, Claude]
tags: [obsidian, chrome-extension, web-clipper, local-rest-api, docker, linuxserver-obsidian, swag, nginx, caddy]
---

# Remote Vault Clipper – chat summary (2026-10-29)

Domain names and addresses are placeholders. The real API key was never given in the chat.

## 1. Goal

The owner asked for a version of the Obsidian Web Clipper browser extension that sends `.md` files to a remote vault. The vault runs in a Docker container that is accessible through a web browser. The owner asked Claude to use the Chrome Extension Builder plugin.

## 2. Decisions (owner answers)

| Question | Answer |
| --- | --- |
| Docker image of the vault | `linuxserver/obsidian` (Obsidian desktop app in the browser) |
| How to write the file | Local REST API community plugin, inside the Obsidian app in the container |
| Network | LAN and public URL through a reverse proxy |
| Base of the build | Fork of the official clipper (keeps templates, highlighter, Defuddle) |

Later the owner said that the container is behind NGINX in the `linuxserver/swag` container, with a public URL.

## 3. Facts found during research

- The official clipper (`obsidianmd/obsidian-clipper`) source code is MIT-licensed. The Obsidian trademarks, icons and marketing assets are not part of that license. A fork must use a different name and icon.
- The clipper saves through an `obsidian://new` URI and the clipboard. The fork adds a network save in the same place.
- Local REST API plugin (`coddingtonbear/obsidian-local-rest-api`): HTTPS on port 27124 (self-signed certificate), optional HTTP on 27123, bearer API key. `PUT /vault/<path>` creates or replaces; `If-None-Match: *` prevents an overwrite (HTTP 412); `POST` appends; `GET /` returns `authenticated: true|false`. It blocks a source after 10 wrong keys in one minute. The default binding host is `127.0.0.1`, so in Docker it must be `0.0.0.0`. This version has no `/periodic/` daily-note route.
- `linuxserver/obsidian`: GUI on ports 3000 (HTTP) and 3001 (HTTPS), `/config` volume, `shm_size: 1gb`. `CUSTOM_USER`/`PASSWORD` give basic auth for a trusted LAN only. The GUI has a terminal with passwordless sudo, so it must not be exposed to the internet without strong authentication.

## 4. What was built

Project name: **Remote Vault Clipper** (version `1.7.1-rv.1`, Chrome manifest `1.7.1.1`).

- New core module `src/utils/remote-vault.ts`: URL check, path encoding, save behaviors, connection test, error mapping, timeout (20 s), `credentials: omit`, `redirect: error`.
- Template behaviors:
  - Create: `PUT` with `If-None-Match: *`; on a name collision it adds ` 1`, ` 2` … (never overwrites).
  - Overwrite: `PUT`.
  - Append (note or daily note): `POST`.
  - Prepend (note or daily note): `GET`, insert after the frontmatter, `PUT` with `If-Match` (one retry).
  - Daily note path comes from a folder and a dayjs format in the settings.
- Settings page: new **Remote vault** section (on/off, URL, API key, daily-notes folder and format, Test connection).
- The URL and key are stored in `chrome.storage.local` only (not synced, not in the settings export).
- Plain `http://` is refused for public hosts. It is permitted for private addresses (LAN ranges, `localhost`, `.local`, `.lan`, Tailscale `100.64/10` and `.ts.net`).
- Popup: button changes to "Add to remote vault"; the vault picker is hidden; an error keeps the clip open and editable. Quick clip uses the same path.
- Rebrand: new name, description, icons and settings logo; Firefox ID changed; the store-rating prompt was disabled. Functional text that names Obsidian was kept.
- Not done: image upload (notes keep web image links); one remote vault per browser profile; no store publication.

## 5. Deliverables

- `remote-vault-clipper-chrome.zip` – load-unpacked Chrome build.
- `remote-vault-clipper-source.zip` – git repository (upstream plus two commits).
- `SETUP.md` – setup procedure in Simplified Technical English.
- `docker-compose.yml` and `Caddyfile` – example stack with a Caddy proxy that forwards only `GET /` and `GET|PUT|POST /vault/*`.
- `obsidian-api.subdomain.conf` – SWAG (NGINX) proxy file for a separate API subdomain.

## 6. Verification

- 24 unit tests for the new module pass. One upstream test (`youtube` template fixture) also fails on unchanged upstream code.
- The real built extension ran in headless Chromium. It clipped a synthetic page through real Caddy to a fake REST server. The file had correct frontmatter and Markdown.
- Server-down test: the error showed, the clip stayed editable, the button became active again.
- Caddy: `caddy validate` passed. Commands, search, MCP and DELETE got 404.
- SWAG file: `nginx -t` passed in a SWAG-like test setup (stub `ssl.conf`, `proxy.conf`, `resolver.conf`). Saves worked through it to an HTTPS fake. Other paths got 404; DELETE, PATCH and `POST /` got 403.
- The plugin's own checker and packager flagged all bundles. The cause is a case-insensitive pattern that matches every `function(` keyword. A strict scan found no `eval`, no `new Function` and no remote code. The project build ZIP was used and was confirmed identical to the tested build.
- Not tested: the real Local REST API plugin, the owner's real container and the owner's real SWAG instance.

## 7. Problem reported and correction

Symptom: the connection test said "The URL replied, but not as the Local REST API plugin."

Cause: the public SWAG URL goes to the Obsidian desktop page (port 3000/3001), so `GET /` returned HTML, not the API JSON.

Correction:
1. Set the plugin **Binding host** to `0.0.0.0`.
2. Add a second subdomain (example `obsidian-api.<domain>`) with DNS and SWAG certificate coverage (`SUBDOMAINS` or wildcard).
3. Copy `obsidian-api.subdomain.conf` to `/config/nginx/proxy-confs/`; it proxies to `https://obsidian:27124`. Restart swag.
4. Check with `curl -s https://obsidian-api.<domain>/` – the reply must be JSON.
5. Do not put basic auth, Authelia or Authentik on the API subdomain; they use the `Authorization` header or return a login page.

The extension was also changed: the connection test now says when the URL returns an HTML page and points to port 27124.

## 8. Open items

- The owner has not yet reported a result after the SWAG correction.
- Whether to trust the plugin certificate for direct LAN HTTPS, or to use the proxy for all access.
- Image upload to the vault is not supported.
