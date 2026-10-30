---
type: source
title: "Empty stubs and unreadable files"
author: "Josh Bayne (notes); several files are course or vendor documents"
ingested: 2026-10-29
source_path: "raw-sources/ (collection listed below)"
tags: [source, collection, gaps]
---

# Empty stubs and unreadable files

## Summary
Files that were read on 2026-10-29 and hold almost no text, plus files this vault connector cannot read.

## Key points
### Read: small content
- `_Initiative Tracker`: a table with three player characters. Arturas 14, Petals 13, Taegan 12 (a fourth row is empty). See [[topics/dnd-campaigns-and-worldbuilding]].
- `_Monsters`: one line ("beasts, creeps, and foul things encountered by the party"). Empty index.
- `Contact`: one line, plan for a contact page with socials, email and phone ([[topics/princess-party-business-smpp]]).
- `Characters`: hub with 18 links; all 18 linked pages are empty tag-only stubs (`Tinker Fairy`, `Arabian Princess`, `Latina Princess`, `Bayou Princess`, `Snow White`, `Sleeping Beauty`, `Scottish Princess`, `Sailor Prince`, `Cinderella` and `Cinderella (Movie Dress)`, `Little Mermaid` and `Little Mermaid (Human)`, `Prince Charming`, `Rapunzel`, `Polynesian Princess`, `Beauty Princess`, `Snow Princess`, `Snow Queen`).
- Brigham finance deck notes: `CH02`, `CH04`, `CH05`, `CH06`, `CH08`, `CH09`, `CH11`, `CH12`, `CH13`, `CH15`, `CH16` and the `_Chap` spreadsheets for 2, 4, 5, 6, 8. All hold only a title and timestamps (June–July 2023). No content. See [[sources/uhcl-finance-notes]].
- `Homework-2---Questions(2)`: ACCT 3341 homework (July 2023); a wrapper around about 1,000 small images with no text.
- `Fall-2023-ARTS-1304`: 15 page images, no text.

### Not readable with this tool
- The connector returns raw bytes for binary files. Compressed pages are lost.
- `MKTG 3301 - Summer 2022 - Online ... Syllabus.pdf.PDF` (8 pages): only metadata. Author Ryan Paul (UHCL); created 2022-05-09; links to a McGraw Hill textbook page, the UHCL academic-honesty page, the student success center, a booking link and a UHCL email. The grading and schedule text could not be read.
- Not tried (binary): `ECON2302 - Spring 2022 Syllabus.pdf`, `Managerial Accounting – MBA 6035 … Syllabus.pdf`, `syllabus 1324-01 sp22.pdf`, `Syllabus_EnvEnergy_SP24.pdf`, `Lockdown Browser UHCL.pdf`, `Z-chart-formal.pdf`, `FINC-4331-Syllabus-FA23.pdf`, `Public Speaking Syllabus Spring 22` (.docx, .pdf), `Blackboard Homework 1 - Josh Bayne` (.docx, .pdf), `1324-final-exam-review-problems.pdf.PDF.pdf`, `FINC-4351-FA-2023-Syllabus.docx`, `Billingsley-1_PFP-15.PPTX`, `Brigham_IFM_14e_PPT_CH01.pptx`, `FinMan 15e_IE PPT_Ch01.pptx`.
- `Aronoc.save` (417 KB) and `Port of Biscayne.save` (1.9 MB): too large for the connector; likely app save data or ink. Not read.

## Evidence and methods
File reads and size checks.

## Limitations and caveats
- To read the binary files, give the PDF/DOCX text (export to text or Markdown) or run an OCR step on the computer.

## Entities and concepts
None.

## Related sources and topics
- [[sources/uhcl-finance-notes]], [[sources/delrun-campaign-notes]], [[sources/business-and-work-notes]]
