---
type: topic
name: "Statistics and quantitative analysis (DSCI 3321/3331)"
updated: 2026-10-28
sources: 1
source_pages: ["[[sources/uhcl-quantitative-notes]]"]
tags: [topic, statistics, dsci3321, dsci3331, decision-analysis]
courses: [DSCI 3321, DSCI 3331]
status: ingested-mostly
---

# Statistics and Quantitative Analysis (DSCI 3321, DSCI 3331)

Two Fall-2022/Spring-2023 courses. **DSCI 3321** (Glen Houston, instructor) covers Modules 6–8 (estimation and hypothesis tests); **DSCI 3331** covers quantitative analysis for management (Render/Stair/Hanna, *Quantitative Analysis for Management* 9e). Notes are OneNote exports where each page is mostly slide images with OCR text. Builds on algebra in [[topics/math-1324-business-math]]; applied examples reappear in [[topics/corporate-finance]] (risk) and [[topics/economics]] (break-even, marginal analysis). Part of [[topics/uhcl-coursework]].

## DSCI 3321: statistics

### Module 6: Confidence intervals
- General form: **point estimate ± margin of error**. For a proportion use z; for a mean with **unknown σ** use t with **df = n − 1** (fatter tails, approaches z as n grows).
- Ways to narrow an interval: lower the confidence level or increase n. Because of the square root, **doubling n shrinks the width only by √2; halving the width needs 4× the sample**, a third needs 9×.
- **Sample size for a proportion**: n = z²·p·q / E². If p is unknown use **p = 0.5** (largest n). Example: 95% confidence, E = 0.05, prior p = 0.70 → **n = 323** households (recomputed: 1.96² × 0.21 ÷ 0.0025 = 322.7).
- Worked mean intervals (all recompute correctly): 64 dogs (mean 30, s = 10, 95%) → (27.5, 32.5); Skittles bags (n = 64, 2.8 oz, s = 0.4, 99%) → (2.667, 2.933); lead-time demand (n = 25, 370.16, s = 75, 90%) → (344.5, 395.8); clinic waits (n = 25, 38.1, s = 10, 95%) → (33.97, 42.23).

### Module 7: Hypothesis tests for one proportion or one mean
- **Four steps**: state H₀/Hₐ; compute the test statistic; find the critical value or p-value (draw the rejection region); conclude in the problem's language.
- **Critical value approach**: reject if |observed| > |critical|. **p-value approach** (required only for proportions): the smallest α at which H₀ can be rejected; reject if p < α (one-tailed) or p < α/2 (two-tailed as taught). Example: p = 0.035 is rejected at α = 0.05 but not at 0.01.
- **One proportion**: z = (p̂ − p₀)/√(p₀q₀/n). **One mean (σ unknown)**: t = (x̄ − μ₀)/(s/√n), df = n − 1.
- **Type I** (reject a true H₀, probability α), **Type II** (fail to reject a false H₀, probability β), **power** = 1 − β.
- Worked examples: downtime test (n = 7, mean 5.6 vs 8.4, s = 1.3, α = 0.01) → t = −5.699, critical 3.707, **reject**. Retirement-plan survey (n = 97, 82% support vs 70%, α = 1%) and policy-rereading survey (164 of 380 vs 48%, α = 1%) are set up in the slides; by my recomputation z ≈ 2.58 (reject, one-tailed critical z ≈ 2.33) and z ≈ −1.89 (fail to reject, two-tailed critical ≈ 2.58) respectively.

### Module 8: Two dependent (paired) means
- Paired t test on differences: t = (d̄ − 0)/(s_d/√n); CI for D: d̄ ± t·s_d/√n.
- Example: 13 before/after pairs, d̄ = 2.54, s_d = 3.48 → t = **2.63** > t.025,12 = 2.179, so **reject** (recomputed: 2.54 ÷ (3.48/√13) = 2.63).
- 98% CI for D (d̄ = 40.56, s_d = 26.58, n = 22, t = 2.518): **[26.29, 54.83]** (recomputed correctly).
- **Choosing a test**: one-sample z (one proportion), one-sample t (one mean), two-sample t (two independent means, e.g. Canadians vs Americans' heights), paired t (the same subjects measured twice, e.g. students' scores in two courses).

## DSCI 3331: quantitative analysis for management

### Chapter 1: The QA approach
- **Quantitative analysis** turns raw data into meaningful information, but **qualitative factors** (weather, legislation) still matter. Steps: define the problem (often the hardest), develop a model, acquire input data ("garbage in, garbage out"), develop a solution, test it, analyze results (including **sensitivity analysis**), implement.
- Models save money and allow "what if" questions but can oversimplify and downplay qualitative information.
- **Break-even example (Bagels R Us)**: fixed cost $100/day, variable cost $0.50, price $1 → **break-even Q = F/(P − V) = 200 bagels**.

### Chapter 3: Decision analysis
- Six steps of decision theory; three environments: **certainty**, **risk** (known probabilities), **uncertainty** (unknown).
- **Under uncertainty**: maximax (optimistic), maximin (pessimistic), equally likely (Laplace), criterion of realism (Hurwicz: α·max + (1 − α)·min), minimax regret.
- **Under risk**: **EMV** = Σ payoff × probability; **EVPI** = expected value with perfect information − best EMV; **expected opportunity loss** = expected regret. **Decision trees** use squares for decisions and circles for states of nature.
- **Thompson's backyard sheds** (payoffs: large plant +200k/−180k, small plant +100k/−20k, do nothing 0/0; 50/50 probabilities). By my recomputation from the payoffs: maximax → large plant; maximin → do nothing; Laplace and EMV → small plant (40,000); α = 0.8 realism → large plant (124,000); minimax regret → small plant (max regret 100,000); EVwPI = 100,000, so **EVPI = 60,000** (matches the slide).

## Sources summarized

| Source | Summary |
|---|---|
| `Module-6---Confidence-Interva`, `Module-6---Determining-the-Sa` | Confidence intervals, interval width, sample size for p. |
| `Module-7---Hypothesis-testing`, `Houston-Module-7---More-issue`, `Module-7---One-tailed-Test-fo`, `Module-7---Two-tailed-Test-fo` | Errors, power, p-value, one- and two-tailed tests (`Houston-Module-7…` is image-only). |
| `Module-8---Hypothesis-Test-an` | Paired t test, CI for D, test selection. |
| `Z-chart-formal`, `T-chart` | Link-only PDFs of the z and t tables. |
| `Chapter-1---Intro-to-QA` | QA approach, modeling, break-even example, QM for Windows/Excel QM screens. |
| `Chapter 3 - Decision Analysis`, `Chapter-3---Decision-Analysis` | Text outline plus Thompson-example slides. |
| `Chapter 1` | A short QA note (see also the first file). |
