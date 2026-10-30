---
type: concept
name: "Decision analysis and regret"
updated: 2026-10-28
sources: 2
tags: [concept, decision-analysis, risk]
---

# Decision analysis and regret

## Definition
Structured methods for choosing among alternatives when outcomes depend on uncertain states of nature, covering certainty, risk (known probabilities) and uncertainty (unknown probabilities).

## How it works / key claims
- Under uncertainty: maximax (optimistic), maximin (pessimistic), equally likely, criterion of realism (α·max + (1 − α)·min), and minimax regret.
- Under risk: expected monetary value (EMV), expected opportunity loss, and the expected value of perfect information (EVPI = expected value with perfect information − best EMV).
- Different criteria can recommend different choices from the same payoff table.

## Evidence and examples
- Thompson's sheds (payoffs +200k/−180k large plant, +100k/−20k small plant, 0 for nothing; 50/50 states). By my recomputation: maximax picks the large plant, maximin picks doing nothing, EMV and equally likely pick the small plant (40,000), α = 0.8 realism picks the large plant (124,000), minimax regret picks the small plant, and EVPI = 60,000 — [[sources/uhcl-quantitative-notes]]
- Hypothesis-test errors can be framed as decision costs: Type I (reject a true H₀, probability α) versus Type II (probability β) — [[sources/uhcl-quantitative-notes]]. *Inference:* the legal burdens "preponderance" (civil) and "beyond a reasonable doubt" (criminal) in [[sources/uhcl-environmental-economics-and-law-notes]] are choices about which error is costlier, analogous to choosing α.

## Related concepts
- [[concepts/opportunity-cost]] — regret is opportunity loss
- [[concepts/statistical-inference]] — error trade-offs
- [[concepts/break-even-and-profit-functions]] — payoffs often come from profit models

## Open questions and disagreements
- The slides give no recommended criterion; the criterion depends on the decision maker's risk attitude.

## Sources
- [[sources/uhcl-quantitative-notes]] — decision criteria and the sheds example
- [[sources/uhcl-environmental-economics-and-law-notes]] — burden-of-proof standards (basis of the analogy)
