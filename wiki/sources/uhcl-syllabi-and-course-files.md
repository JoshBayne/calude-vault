---
type: source
title: "UHCL syllabi and course files (PDF, DOCX and PPTX)"
author: "Course instructors and textbook publishers; `Blackboard Homework 1` carries Josh Bayne's answers"
ingested: 2026-11-01
source_path: "raw-sources/: FINC-4331-Syllabus-FA23.pdf; FINC-4351-FA-2023-Syllabus.docx; MKTG 3301 - Summer 2022 - Online - Dr. Ryan W. Paul - Syllabus.pdf.PDF; Public Speaking Syllabus Spring 22.docx; Public Speaking Syllabus Spring 22.pdf; Syllabus_EnvEnergy_SP24.pdf; 1324-final-exam-review-problems.pdf.PDF.pdf; Lockdown Browser UHCL.pdf; Blackboard Homework 1 - Josh Bayne.docx; Blackboard Homework 1 - Josh Bayne.pdf; Billingsley-1_PFP-15.PPTX; Brigham_IFM_14e_PPT_CH01.pptx; FinMan 15e_IE PPT_Ch01.pptx"
tags: [source, collection, uhcl, syllabi]
---

# UHCL syllabi and course files

## Summary
Thirteen binary files that the vault connector could not open, read in full on 2026-11-01 by extracting their text locally: five syllabi (one in two formats), three textbook chapter decks, a math final-exam review, a homework (two formats) and exam-software instructions. They say what each course was officially about, and they settle several guesses on the coursework pages.

## Key points

### Syllabi
| Course | Instructor | Term | Texts | Assessment |
|---|---|---|---|---|
| COMM 1315 Public Speaking | Dr. Andrea Baldwin | Spring 2022 | Fassett and Nainby, *Empowering Public Speaking* (2021) | 2 exams 20%, 3 speeches 50%, analysis paper 15%, other 15% |
| MKTG 3301 Principles of Marketing | Ryan W. Paul (adjunct) | Summer 2022, 8 weeks, online | Grewal and Levy, *Marketing*, 8th ed. | 3 exams, 4 quizzes and 1 homework, 380 points |
| FINC 4331 Business Finance | Professor Bendeck | Fall 2023 | RMA *Credit Essentials Course Participant Workbook* (2023) | quizzes 40%, final 20%, cases 20%, group work 20% (read from the listed order) |
| FINC 4351 International Finance | Prof. Ivelina Pavlova-Stout | Fall 2023 | Eiteman, Stonehill and Moffett, *Multinational Business Finance*, 16th ed. | Exam 1 25%, Exam 2 30%, final 30%, Excel project 10%, participation 5% |
| ECON 3381/5137, ENVR 4931/5331 Energy and Environmental Economics | Allyssa A. Wadsworth, PhD | Spring 2024 | Dahl, *International Energy Markets*, 2nd ed.; Tietenberg and Lewis, *Environmental Economics and Policy*, 7th ed. | undergraduates: exams (best 2 of 3) 40%, activity 10%, presentation and homework 30% as listed, two written responses 20% |

- **FINC 4331** is a commercial-credit course. It covers knowing a bank's customer, credit-risk analysis from statements, cash-flow projections, loan structure, loan committees, guarantors, tax returns and global cash flow. The final is the RMA Credit Essentials Certificate exam, and 80% earns the certificate.
- **FINC 4351** covers foreign-exchange markets and exposure, financing the multinational firm, multinational capital budgeting, and derivatives such as currency futures, forwards and options.
- **MKTG 3301** has one central question: "How do marketers offer value to customers?" The homework was a roughly 10-slide marketing plan with a SWOT analysis, SMART goals and market segmentation, due 2022-07-18.
- **COMM 1315** has a "Public Speaking is…" theme for each textbook chapter. The schedule names a "CAP PAPER" (communication analysis paper, 3–5 pages), assigned 3/30 and due 4/19.
- **Energy and Environmental Economics** gives exams on 2/14, 4/3 and 5/1. "LT" means Lewis and Tietenberg and "D" means Dahl.

### Textbook decks
- **`Billingsley-1_PFP-15.PPTX`** — *Personal Financial Planning* 15e, Chapter 1: SMART goals, propensity to consume, wealth, goal horizons, the planning life cycle and how planners are paid.
- **`Brigham_IFM_14e_PPT_CH01.pptx`** — Brigham and Daves, *Intermediate Financial Management* 14e, Chapter 1: business forms, agency problems, intrinsic value, cost of money, securities and markets, securitization and the mortgage crisis.
- **`FinMan 15e_IE PPT_Ch01.pptx`** — *Financial & Managerial Accounting* 15e, Chapter 1: GAAP assumptions and principles, business frauds and SOX, the NetSolutions transactions, the four statements, and the ratio of liabilities to stockholders' equity.

### Other files
- **`1324-final-exam-review-problems`** — 53 MATH 1324 review problems: linear and quadratic models, equilibrium, matrices, linear programming and the simplex method, logarithms, simple and compound interest, annuities, and probability.
- **`Blackboard Homework 1`** (ACCT 2301) — answers that the SEC can enforce regulations, that FASB is an independent non-profit and not a government regulator, and a list of the asset topics in the FASB codification. The DOCX and PDF are the same.
- **`Lockdown Browser UHCL`** — Blackboard instructions for LockDown Browser with a webcam. No course is named.

## Evidence and methods
Text came from `pdftotext` for PDFs and from the document XML for DOCX and PPTX. The raw files were not changed. The two `Public Speaking Syllabus` copies match apart from page headers and table layout. In the Billingsley deck, the retirement figures ($95,454, $180,641 and $241,600 for $2,000 a year at 5%) recompute correctly. The NetSolutions November figures also recompute: net income $3,050, retained earnings $1,050, cash $5,900.

## Limitations and caveats
- **Credential not copied:** the homework reproduces a shared course login for the FASB codification, and it remains in the raw DOCX and PDF. It is left out of the wiki on purpose. Keep those two files out of any shared copy.
- **Math symbols lost:** extraction dropped the variables from `1324-final-exam-review-problems`, so the equations are unreadable and only topics and word problems were used.
- **Pictures and charts not seen:** slides that are only diagrams, such as the six-step planning process, the business cycle and the intrinsic-value picture, gave a title and no content.
- **No schedules for FINC 4331 and 4351:** both syllabi point to a schedule that is not in the text extracted here.
- **FINC 4351 weights** are readable in order, but the syllabus mentions three exams and a "group presentation" in one place and an Excel project in the grade table.
- **Energy and Environmental Economics grading:** the extracted table separates the labels from the percentages, so the 10%/30% split between activity, presentation and homework is uncertain.
- Syllabi are plans. Three say they can change, and none shows what was actually taught.
- Slide figures such as the 2016 household medians, the 2019 salaries and the 2017 starting salaries are dated and were not checked.
- `ECON2302`, `MBA 6035`, `syllabus 1324-01 sp22` and `Z-chart-formal` are scans with no text layer and are still unread ([[sources/empty-stub-and-unreadable-files]]).

## Entities and concepts
- [[concepts/time-value-of-money]] — retirement compounding, intrinsic value as present value, and review problems
- [[concepts/opportunity-cost]] — spending now against later, through propensity to consume (inference)

## Related sources and topics
- [[topics/uhcl-coursework]] — course map updated from these files
- [[topics/corporate-finance]], [[topics/public-speaking]], [[topics/energy-and-environmental-economics]], [[topics/math-1324-business-math]], [[topics/financial-accounting]] — pages these files add to
- [[sources/uhcl-finance-notes]], [[sources/uhcl-communication-and-misc-notes]], [[sources/uhcl-environmental-economics-and-law-notes]], [[sources/uhcl-quantitative-notes]], [[sources/uhcl-accounting-notes]] — the notes these documents frame
