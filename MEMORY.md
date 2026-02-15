# Project Memory

Corrections and learned facts that persist across sessions.
When a mistake is corrected, append a `[LEARN:category]` entry below.

---

## Project Setup (2026-02-15)

- **Course:** Introduction to Econometrics (graduate level)
- **Institution:** CREST, Institut Polytechnique de Paris
- **Textbooks:** Wooldridge (2019) *Introductory Econometrics*, Angrist & Pischke (2009) *Mostly Harmless Econometrics*
- **Supplementary:** Hansen (2022), Hayashi (2000), Stock & Watson (2020), Greene (2018), Cameron & Trivedi (2005)
- **Language:** R (with `fixest`, `sandwich`, `lmtest`, `modelsummary`, `ggplot2`)

## Color Palette (IP Paris / CREST)

- Primary dark blue: `#233E5C`
- CREST blue: `#144563`
- Accent blue: `#018BD3`
- Light blue: `#61ABF6`
- Dark navy: `#011A29`
- Warm accent (red): `#C0392B`

## Key Conventions

- Beamer `.tex` is authoritative; Quarto `.qmd` derives from it
- SCSS theme: `Quarto/ipp-clean.scss` (not `emory-clean.scss`)
- XeLaTeX only (3-pass compilation)
- Robust SE by default; cluster SE for panel data
- `set.seed(YYYYMMDD)` at top of every stochastic script
- `here::here()` for R paths; relative paths for LaTeX
- Figures: transparent bg, `theme_ipp()`, 300 DPI

## Lecture Sequence (13 lectures)

1. Intro & Probability Review
2. Simple Regression
3. Multiple Regression: Estimation
4. Multiple Regression: Inference
5. Asymptotics for OLS
6. Heteroskedasticity
7. Specification & Functional Form
8. Instrumental Variables
9. Simultaneous Equations
10. Panel Data
11. Binary Response Models
12. Time Series Basics
13. Advanced Topics / Review

---

<!-- Append new [LEARN] entries below. Most recent at bottom. -->
