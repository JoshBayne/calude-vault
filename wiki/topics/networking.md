---
type: topic
name: "Networking (Cisco / CCNA-style)"
updated: 2026-10-28
sources: 1
source_pages: ["[[sources/uhcl-it-notes]]"]
tags: [topic, networking, cisco, it]
status: ingested-partial
---

# Networking (Cisco / CCNA-style)

A four-part sequence of notes on network fundamentals, closely matching a Cisco CCNA study path. Security angles continue in [[topics/information-systems-and-security]]. Cabling and device details are also practical background for [[topics/work-and-web-projects]] and hobby tech in [[topics/personal-and-hobbies]].

## Core concepts

### 1. Network devices
- A network lets nodes share resources. Node types: **router, switch, firewall, server, client**; servers and clients are *end hosts/endpoints*.
- **Switches** connect hosts within a LAN (many ports, no inter-LAN connectivity). **Routers** connect LANs/WAN/Internet (fewer interfaces).
- **Firewalls**: hardware (rule-based, may include an **IPS**; "next-gen" adds advanced filtering) or **host-based** software.

### 2. Interfaces and cables
- **Ethernet** is IEEE 802.3 (1983). Copper standards (all max 100 m): 10BASE-T (802.3i), 100BASE-T (802.3u), 1000BASE-T (802.3ab), 10GBASE-T (802.3an).
- **UTP**: 4 pairs; 10/100 Mbps use 2 pairs, gigabit and 10G use all 4. **Straight-through** cables join unlike devices (PC/router transmit on pins 1,2; switch on 3,6); **crossover** cables join like devices. **Auto MDI-X** detects and swaps pins automatically.
- **Fiber** (SFP transceivers): multimode (LED, cheaper, shorter) vs single-mode (laser, longer, pricier). Standards table: 1000BASE-LX, 10GBASE-SR (400 m), -LR (10 km), -ER (30 km).
- **UTP vs fiber**: UTP is cheap, ~100 m, vulnerable to EMI and leaks faint signal; fiber is costlier, longer-range, EMI-immune and doesn't leak signal.
- Bits/bytes: speeds in bits per second, storage in bytes.

### 3. OSI model and TCP/IP
- Seven layers: Application, Presentation, Session, Transport, Network, Data Link, Physical (mnemonic in notes: "All People Seem To Need Data Processing").
- PDUs: data → segment (L4) → packet (L3) → frame (L2) → bits (L1). Routers work at L3 (IP/logical addressing); switches at L2.
- **TCP/IP** (DARPA) has four layers: Application (OSI 7–5), Transport, Internet (OSI 3), Link (OSI 2–1). It is the model actually used today; OSI still shapes the vocabulary.

### 4. Cisco IOS CLI
- Connect via **console port** with a rollover cable and a terminal emulator (PuTTY: 9600 baud, 8 data bits, 1 stop bit, no parity, no flow control).
- Modes: **User EXEC** (`hostname>`), **Privileged EXEC** (`enable`, `hostname#`), **Global config** (`configure terminal` / `conf t`).
- `running-config` vs `startup-config`; save with `write`, `write memory`, or `copy running-config startup-config`.
- Passwords: `enable password` (cleartext), `service password-encryption` (weak), `enable secret` (MD5, takes precedence). `do` runs exec commands from config mode; `no` negates a command.

## Sources summarized

| Source | Summary |
|---|---|
| `1 - Network Devices` | Nodes, clients/servers, switches, routers, firewalls. |
| `2 - Interfaces and cables` | Ethernet standards, UTP pinouts, straight-through vs crossover, fiber types, UTP vs fiber. |
| `3 - OSI Model and TCP IP Suite` | OSI layers and PDUs, TCP/IP mapping. |
| `4 - Introduction to Cisco IOS CLI` | Console access, CLI modes, config files, password commands. |
| `3-0 Lecture Notes`, `4-0 Lecture Notes` | **Not networking:** ACCT 2301 Chapters 3–4 (adjusting entries, closing; read 2026-10-30, see [[topics/financial-accounting]]). `1-0` and `2-0 Lecture Notes` were read and are accounting; see [[topics/financial-accounting]]. |

## Gaps
- Topics beyond Cisco CLI basics (IP addressing, VLANs, routing) are not in the files read.
