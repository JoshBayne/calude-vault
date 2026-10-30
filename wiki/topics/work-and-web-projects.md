---
type: topic
name: "Work and web projects"
updated: 2026-10-28
sources: 1
source_pages: ["[[sources/business-and-work-notes]]"]
tags: [topic, work, it, automation, sharepoint, compliance]
status: ingested-partial
---

# Work and Web Projects

Saved AI-assistant conversations and short tool notes related to running a small business's IT, finance operations and web presence. Most are **Q&A transcripts**, not original notes, so this page summarizes the *questions and approaches*, not verified procedures. Business context: [[topics/princess-party-business-smpp]]. Accounting background: [[topics/financial-accounting]] (AP/AR files) and career context: [[topics/corporate-finance]]. Tool/hardware lists: [[topics/personal-and-hobbies]].

## Projects and questions

### Messaging and payments
- **Notifuse + Square** (`notifuse project`, ~14 KB): goal is a self-hosted **Notifuse** instance sending reminders and confirmation emails to clients, with **Square** as payment processor and current reminder system. The answer given: no native connector exists, so build a small **middleware** service that receives **Square webhooks** (e.g. `booking.created/updated`, `payment.created/updated`, public HTTPS endpoint, 2xx response within 10 s) and calls Notifuse's transactional API.

### Microsoft 365 / SharePoint
- **Investor portal** (`investor portal`, ~74 KB, fully read 2026-10-29): Q1 on who viewed a file (no per-user view; use the Purview audit log). Q2 on a segregated invite-only portal (separate site, broken inheritance, Entra B2B guests, MFA, sensitivity labels, link expiry, audit, quarterly reviews, licensing table). Then two HTML landing-page templates with a demo-booking button (fund version, then private-tech-company version). Details and caveats: [[sources/smpp-and-sharepoint-ai-transcripts]].
- **Library structure** (`sharepoint files`): one library with folders vs multiple libraries; "it depends"; folders suit closely related content and simple permissions, multiple libraries suit different versioning/retention/permissions; avoid deep nesting.
- **Interactive graphs** (`sharepoint graph`): ways to show Excel-based interactive charts on a SharePoint page, starting with the File and Media web part.
- **Calendar sharing** (`calendar planning`): automate placing selected users' personal calendars on a team calendar under Microsoft 365 Business Premium (admin access, non-technical users); first check whether built-in free/busy and the Scheduling Assistant already solve it.

### Files and scripting
- **Flatten nested folders** (`nested files`): move hundreds of images/videos from deeply nested subdirectories into one folder using `find … -exec mv`, a safer variant that prefixes the parent folder name to avoid duplicate names, or `rsync`.

### Accounts payable and compliance
- **AP/AR** (`ap-ar`, `ap-ar files`): weekly AP compliance tasks, vendor master file collection, and an AP folder structure; summarized in [[topics/financial-accounting]].
- **Compliance career path** (`compliance goals`): the author holds a **BS in Finance from UHCL** and asks what learning and certifications would ease a move into internal-policy and external compliance work (e.g. **SOC 2**) at a tech company pursuing government and healthcare contracts; the answer maps finance/audit experience into compliance.

### Web and content
- **Bulma components** (`navbar`, `card`, `large hero banner`): HTML snippets and doc links used for the SMPP site (see [[topics/princess-party-business-smpp]]).
- **YouTube ideas** (`youtube ideas`, ~14 KB): a prompt that asks the assistant to act as a **five-member deliberating committee** to develop a video-essay script arguing that the animated show *Home Movies* (Brendon Small, 1999) has one of the best series endings, covering the finale, preceding arcs and the show's in-show movies.

### Tools list
- `Programs-to-reinstall` (2025-02-28): Orcaslicer, Bleachbit, Topaz Photo AI, Guitar Pro 8, TabStop, Affinity, Calibre, Obsidian(?), Mullvad, SuperDisplay, "HumbleBundle Photo Tools???", Python, ffmpeg, Ruby.

## Sources summarized

| Source | Summary |
|---|---|
| `notifuse project` | Square-to-Notifuse webhook middleware approach. |
| `investor portal` | SharePoint viewer analytics, portal design and two HTML templates. |
| `sharepoint files`, `sharepoint graph`, `calendar planning` | SharePoint/M365 architecture and automation Q&A. |
| `nested files` | Shell approaches for flattening directories. |
| `compliance goals` | Finance-to-compliance (SOC 2) career mapping. |
| `ap-ar`, `ap-ar files` | AP compliance and folder structure (see financial accounting page). |
| `youtube ideas` | Video-essay committee prompt about *Home Movies*. |
| `navbar`, `card`, `large hero banner` | Bulma web snippets. |
| `Programs-to-reinstall` | Software reinstall checklist. |
