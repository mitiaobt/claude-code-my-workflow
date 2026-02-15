# Plan: Create Lecture 2 — Simple Regression

**Status:** APPROVED
**Date:** 2026-02-15

## Slide Outline (~44 slides)

### Part I: The Simple Regression Model (slides 1-10)
1. Title slide
2. Recap from Lecture 1 (CEF, LIE, CLT bridge)
3. Motivating examples (Y vs X)
4. The simple linear regression model
5. Interpreting β₀ and β₁
6. The error term
7. PRF vs SRF
8. Returns to education revisited
9. When can we interpret β₁ causally?
10. Roadmap

### Part II: Deriving the OLS Estimator (slides 11-20)
11. Divider
12. The idea: minimize SSR
13. Objective function
14. First-order conditions
15. Normal equations
16. OLS estimators (closed-form)
17. Intuition for β̂₁ (cov/var)
18. Fitted values and residuals
19. Algebraic properties of OLS
20. OLS derivation summary

### Part III: Assumptions for Unbiasedness (slides 21-28)
21. Divider
22. Why assumptions?
23. SLR.1: Linear in parameters
24. SLR.2: Random sampling
25. SLR.3: Sample variation in X
26. SLR.4: Zero conditional mean (KEY assumption)
27. Proving unbiasedness (step-by-step)
28. What ZCM rules out

### Part IV: Variance and Efficiency (slides 29-35)
29. SLR.5: Homoskedasticity
30. Variance of β̂₁
31. Estimating σ² (SER)
32. Standard errors
33. Gauss-Markov theorem (BLUE)
34. SLR.6: Normality (optional)
35. Assumption summary table

### Part V: Goodness of Fit (slides 36-40)
36. Divider
37. TSS = ESS + RSS decomposition
38. R² definition
39. R² pitfalls
40. Example: R² in wage equation

### Part VI: Preview & Wrap-up (slides 41-44)
41. Inference preview (t-test, CI)
42. What's next (multiple regression)
43. Key takeaways
44. References

## Verification
1. Compile: 3-pass XeLaTeX + bibtex
2. Check: no overfull vboxes > 10pt
3. Check: all citations resolve
4. Run proofreader agent
5. Run domain-reviewer agent
