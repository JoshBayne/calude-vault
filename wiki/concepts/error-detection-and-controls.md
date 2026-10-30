---
type: concept
name: "Error detection and controls"
updated: 2026-10-28
sources: 4
tags: [concept, accounting, controls, audit, security]
---

# Error detection and controls

## Definition
Methods that make mistakes and misuse visible: arithmetic cross-checks in bookkeeping, audit trails and access logs, and layered permissions.

## How it works / key claims
- **Trial balance**: equal debits and credits prove arithmetic consistency but not correctness. A difference divisible by 9 suggests a transposition or slide; by 2, a debit/credit flip; by 10/100/1000, an addition slip. Wrong-account errors do not unbalance the trial balance and need a correcting entry.
- **Audit trail**: the SharePoint thread says analytics give aggregate viewer data while the audit log is the most detailed record of who touched a file — [[sources/business-and-work-notes]].
- **Access controls**: Cisco `enable secret` (MD5) overrides the cleartext `enable password`; `service password-encryption` is weak — [[sources/uhcl-it-notes]].
- **Compliance workflow**: weekly accounts-payable tasks and a vendor master file (saved AI Q&A, not independently verified) — [[sources/uhcl-accounting-notes]].
- **Shadow IT** is a control gap: faster, but with weak security and compliance — [[sources/uhcl-it-notes]].

## Evidence and examples
- **A live example in these notes:** the NetSolutions trial balance's credit column sums to 42,690 vs the stated 42,600, a difference of 90 (divisible by 9). Fees Earned of 16,340 instead of 16,430 would balance it, so the technique the notes teach points to a transposition in the notes themselves — [[sources/uhcl-accounting-notes]] (inference; the original textbook figure was not checked).
- Inventory T-account credit 8,750 vs journal entry 4,375 in `First Spreadsheet Notes` is a wrong-amount error of the kind a trial balance would not catch if both sides carried it — [[sources/uhcl-accounting-notes]].
- An inconsistent fixed cost (3600 vs 36000) in the math notes (`Chapter 1.6` break-even) was found by recomputation — [[sources/uhcl-quantitative-notes]].

## Related concepts
- [[concepts/statistical-inference]] — testing claims against evidence
- [[concepts/externalities-and-public-goods]] — controls as a response to costs one party imposes on another

## Open questions and disagreements
- Whether the source notes or the original textbooks hold the correct figures is unresolved for each flagged item.

## Sources
- [[sources/uhcl-accounting-notes]] — trial balance technique and flagged errors
- [[sources/business-and-work-notes]] — audit log and AP workflow transcripts
- [[sources/uhcl-it-notes]] — access-control commands and shadow IT
- [[sources/uhcl-quantitative-notes]] — recomputation of worked examples
