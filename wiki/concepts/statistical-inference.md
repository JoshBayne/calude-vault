---
type: concept
name: "Statistical inference"
updated: 2026-10-28
sources: 2
tags: [concept, statistics, inference]
---

# Statistical inference

## Definition
Drawing conclusions about a population from a sample, using confidence intervals (a point estimate ± margin of error) and hypothesis tests (decide between H₀ and Hₐ using a test statistic, a critical value or a p-value).

## How it works / key claims
- For a mean with unknown σ use the t distribution with df = n − 1; for a proportion use z.
- Interval width shrinks with the square root of n: halving the width needs about 4× the sample.
- Sample size for a proportion: n = z²·p·q ÷ E², using p = 0.5 when unknown.
- Type I error = reject a true H₀ (probability α); Type II = fail to reject a false H₀ (probability β); power = 1 − β. Small p-values reject H₀.
- Test selection: one proportion (z), one mean (t), two independent means (two-sample t), paired data (paired t on differences).

## Evidence and examples
- Four worked intervals and the n = 323 sample-size example, a downtime t test (t = −5.699 vs critical 3.707) and a paired test (t = 2.63 vs 2.179) — [[sources/uhcl-quantitative-notes]] (all recomputed and correct).
- *Inference:* informal reasoning fallacies taught in public speaking (post-hoc, hasty generalization from inadequate evidence) are the everyday versions of the errors that inference formalizes — [[sources/uhcl-communication-and-misc-notes]].
- *Inference:* the wiki's own consistency checks (recomputing trial balances and worked examples) apply the same habit of testing a claim against evidence before trusting it; see [[concepts/error-detection-and-controls]].

## Related concepts
- [[concepts/decision-analysis-and-regret]] — error costs as decision trade-offs
- [[concepts/error-detection-and-controls]] — checking numbers

## Open questions and disagreements
- Module 7's one-tailed and two-tailed example answers were not visible in the slides; z-values for those examples are my computation.

## Sources
- [[sources/uhcl-quantitative-notes]] — methods and examples
- [[sources/uhcl-communication-and-misc-notes]] — fallacy definitions
