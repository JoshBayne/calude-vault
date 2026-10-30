---
type: source
title: "UHCL IT notes (networking, MIS, security)"
author: "Josh Bayne (own notes; Cisco-style networking sequence)"
ingested: 2026-10-28
source_path: "raw-sources/ (collection: 1 - Network Devices, 2 - Interfaces and cables, 3 - OSI Model and TCP IP Suite, 4 - Introduction to Cisco IOS CLI, Module 1, Module 2 - Secure Info Systems, Domain-1-Security-Principles)"
tags: [source, collection, networking, mis, security, uhcl]
---

# UHCL IT notes (networking, MIS, security)

## Summary
A four-part networking sequence (devices, Ethernet/fiber, OSI vs TCP/IP, Cisco IOS CLI basics) plus MIS Module 1 (information-system concepts, Leavitt's Diamond, value chain, shadow IT) and a barely started security module.

## Key points
- Ethernet copper standards all cap at 100 m; straight-through vs crossover cabling; fiber is EMI-immune and does not leak signal.
- OSI has 7 layers and TCP/IP 4; PDUs are segment, packet, frame, bits.
- Cisco CLI modes: user EXEC, privileged EXEC, global config; `enable secret` (MD5) supersedes `enable password`.
- Shadow IT trade-offs: speed and innovation against weak security, compliance and duplication.

## Evidence and methods
Definitions, standards tables and command examples; no lab output.

## Limitations and caveats
- `Module 2` stops early; `Domain-1-Security-Principles` is an empty stub (the underscore variant `Domain-1-Security-Principles_` was not read).
- `3-0 Lecture Notes` and `4-0 Lecture Notes` are not IT notes: they are ACCT 2301 Chapters 3–4 (checked 2026-10-30; see [[sources/uhcl-accounting-notes]]).
- Course names and terms are not stated in these files.

## Entities and concepts
- [[concepts/error-detection-and-controls]] — layered checks and controls
- [[concepts/externalities-and-public-goods]] — spam and security as externalities (see [[topics/cross-domain-connections]])

## Related sources and topics
- [[topics/networking]], [[topics/information-systems-and-security]] — syntheses of this source
- [[sources/uhcl-environmental-economics-and-law-notes]] — cyberlaw (spam, cybersquatting)
