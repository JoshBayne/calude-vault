---
type: topic
name: "Business math (MATH 1324)"
updated: 2026-11-01
sources: 2
source_pages: ["[[sources/uhcl-quantitative-notes]]", "[[sources/uhcl-syllabi-and-course-files]]"]
tags: [topic, math, math1324, business-math]
courses: [MATH 1324]
status: ingested-partial
---

# Business Math (MATH 1324)

Notes from UHCL **MATH 1324** (Mathematics for Business and Social Sciences), Chapter 1 on functions. Feeds into [[topics/economics]] (linear supply/demand), [[topics/managerial-accounting]] (cost functions) and [[topics/statistics]]. Part of [[topics/uhcl-coursework]].

## Core concepts

### 1.2 Functions
- A **relation** is a set of ordered pairs; a **function** assigns each domain element to exactly one range element. Use the **vertical line test** on graphs. Worked table examples decide function vs non-function (a repeated x with different y fails).
- **Function notation**: f(x) is the output for input x (not f × x). Examples: f(x) = 12x − x³, g(t) = t² + 2t + 4, f(2x), g(t + 3) = t² + 8t + 19.
- **Domain**: implied restrictions come from division by zero and even roots of negatives (e.g. √(4 − 3x) → x ≤ 4/3).
- Application: a box with square cross-section, V(x) = x²(108 − 4x); V(10) = 6,800 in³, V(20) = 11,200 in³; domain (0, 27).
- **Operations** on functions (sum, difference, product, quotient) and **composition** (f∘g)(x) = f(g(x)); worked examples include (f∘f)(x) = 9x + 20.

### 1.3 Linear functions
- Slope-intercept form f(x) = mx + b; slope = Δy/Δx; horizontal = constant (slope 0); vertical lines are not functions.
- **Intercepts** by setting y = 0 or x = 0; **point-slope form** y − y₁ = m(x − x₁).
- **Parallel** lines share slope; **perpendicular** slopes are negative reciprocals. Worked examples build lines from two points, parallel/perpendicular conditions, and vertical/horizontal special cases.

### 1.1 Linear equations and inequalities
- A **solution set** makes the equation true; equivalent equations share it. Add/subtract the same quantity or multiply/divide by a nonzero quantity on both sides. An **identity** is always true (e.g. 3 + 2t = 3 + 2t); some equations have **no solution** (3x + 4 = 3x + 7).
- Equations with the variable in a denominator must be **checked for extraneous solutions** (4/(x − 2) = … gives x = 2, which divides by zero, so no solution). Solving for one variable in a formula treats the others as constants (S = P + Prt → t = (S − P)/(Pr); C = 5/9(F − 32) → F = 9C/5 + 32).
- **Inequalities**: same steps, but **multiplying/dividing by a negative flips the sign**. Interval notation uses parentheses for strict bounds and brackets for inclusive ones. Examples: 2(x + 1) < x − 5 → (−∞, −7); 5 − 3y > 14 − 6y → (3, ∞); 8 + 2x ≤ 3x + 10 → [−2, ∞).
- Applications: a $735,000 building depreciating $1,750/month is fully depreciated in **420 months (35 years)**; a car costing $23,706 with 8% tax has a $21,950 price and **$1,756 tax**; R = 40x vs C = 20x + 1600 gives a profit when **x > 80**.

### 1.5 Systems of linear equations
- Two lines have one solution, none (parallel) or infinitely many (**dependent**). Methods: **substitution** and **addition/elimination**; three equations by eliminating one variable twice.
- Worked results: (5, 1); (2, −4); no solution (parallel); (17/10, −11/10); dependent system; the 3×3 system gives **(−1, 2, 1)**; a medication mixing problem needs **4 cc of the 20% and 6 cc of the 5% solution** to make 10 cc of 11%. (All recompute correctly.)

### 1.6 Business and economics applications
- **Profit** P(x) = R(x) − C(x); R(x) = price × units; C(x) = variable + fixed costs; C(0) = fixed cost; P(0) = −FC. For linear functions the slopes are **marginal cost, revenue, profit**.
- **Break-even** is where R = C. Examples: receivers with C = 210x + 40,000 and R = 430x give P(x) = 220x − 40,000 and **P(500) = $70,000**; DVD players (C = 64x + 9,800, R = 100x) give P(250) = **−$800**; belts at $12 with $8 variable and $1,600 fixed break even at **400 belts** (revenue $4,800).
- **Market equilibrium** where supply meets demand: at p = 60 demand 2p + 5q = 500 gives 76 pairs but supply p − 2q = 10 gives only 25, a **shortage**; with demand p = −4q + 220 and supply p = 15q + 30, equilibrium is **q = 10, p = $180**, revenue $1,800.

### 2.1 Quadratic equations
- Solve by **factoring** (one side must be zero; zero-product property) or the **square root property**. Results: 8x − 4x² = 0 → x = 0 or 2; 9t² + 6t + 1 = 0 → t = −1/3; (x − 4)(x + 3) = 18 → x = −5 or 6; (z − 2)² = 3z + 12 → z = −1 or 8. `Chapter 1.4 Graphing Utilities` is an empty file.

### Course scope beyond these notes
The 53-problem final review shows the course went well past the notes, which stop at Chapter 2.1. It also covers quadratic optimization (vertex, maximum revenue and profit), matrices and row reduction, linear inequalities, linear programming and the simplex method, logarithms and exponential decay, simple and compound interest, annuities and loans, conditional probability, and the mean and standard deviation of a discrete distribution — [[sources/uhcl-syllabi-and-course-files]]. Its equations did not survive text extraction, and it has no answers.

## Data-quality flags
Minor typos in the source notes (final answers are correct): in `Chapter 1.2`, an intermediate step for g(t + 3) writes 2(t + 2) instead of 2(t + 3), and the h/g quotient shows x² + 2 where g(x) = x² + 1; in `Chapter 1.3`, "g(−1) = y" should read 7.

## Errors and inconsistencies found in the source notes
- **`Chapter 1.6` break-even example**: the problem states C(x) = 85x + 3600, the next line subtracts 36000, and the profit line reads P(x) = 300x − 3600, but the answers are P(200) = 24,000 and "x > 120". Those answers match a fixed cost of **36,000**; with 3,600 they would be 56,400 and x > 12. The source is internally inconsistent (likely a typo in the fixed cost); the textbook figure was not checked. Updated 2026-10-30; an earlier version of this page declared 56,400 and x > 12 correct.
- **`Chapter 1.6` equilibrium**: the problem states supply as p = 15q + 20 but the solution uses 15q + 30 (which yields q = 10); with +20, q would be 200/19.
- **`Chapter 1.1`**: problem 1 shows x = 2, but 5x + 12 = 2 gives **x = −2**; problem 3 shows an intermediate "t ≤ −2/19" before the correct interval (−∞, −19/2].
- **`Chapter 2.1`**: 4y² + 5 = 10 gives y = ±√5/2 (i.e. √(5/4)), not ±√(5/2).

## Sources summarized

| Source | Summary |
|---|---|
| `_MATH 1324` | Hub page linking syllabus and chapter notes. |
| `Chapter 1.1` | Linear equations, identities, extraneous solutions, formulas, inequalities, applications. |
| `Chapter 1.2 Functions` | Relations, functions, notation, domain, operations, composition with worked examples. |
| `Chapter 1.3 Linear Functions` | Slope, intercepts, point-slope, parallel/perpendicular lines. |
| `Chapter 1.4 Graphing Utilities` | Empty. |
| `Chapter 1.5`, `Chapter 1.6`, `Chapter 2.1 Quadratic Equations` | Systems, business applications, quadratics (see sections above). |
| `1324-final-exam-review-problems.pdf.PDF.pdf` | Final review problems, read 2026-11-01 for topics only (equations lost in extraction). |
| `1324-final-exam-review-proble`, `syllabus 1324-01 sp22.pdf` | The `.md` is a wrapper around page images, not read. The syllabus is a scan, unread. |
