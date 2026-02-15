# CLAUDE.MD -- Academic Project Development with Claude Code

**Project:** Introduction to Econometrics
**Institution:** CREST, Institut Polytechnique de Paris
**Branch:** main

---

## Core Principles

- **Plan first** -- enter plan mode before non-trivial tasks; save plans to `quality_reports/plans/`
- **Verify after** -- compile/render and confirm output at the end of every task
- **Single source of truth** -- Beamer `.tex` is authoritative; Quarto `.qmd` derives from it
- **Quality gates** -- nothing ships below 80/100
- **[LEARN] tags** -- when corrected, save `[LEARN:category] wrong → right` to MEMORY.md

---

## Folder Structure

```
intro-econometrics/
├── CLAUDE.MD                    # This file
├── .claude/                     # Rules, skills, agents, hooks
├── Bibliography_base.bib        # Centralized bibliography
├── Figures/                     # Figures and images
├── Preambles/header.tex         # LaTeX headers (IP Paris theme)
├── Slides/                      # Beamer .tex files
├── Quarto/                      # RevealJS .qmd files + theme
├── docs/                        # GitHub Pages (auto-generated)
├── scripts/                     # Utility scripts + R code
├── quality_reports/             # Plans, session logs, merge reports
├── explorations/                # Research sandbox (see rules)
├── templates/                   # Session log, quality report templates
└── master_supporting_docs/      # Papers and existing slides
```

---

## Commands

```bash
# LaTeX (3-pass, XeLaTeX only)
cd Slides && TEXINPUTS=../Preambles:$TEXINPUTS xelatex -interaction=nonstopmode file.tex
BIBINPUTS=..:$BIBINPUTS bibtex file
TEXINPUTS=../Preambles:$TEXINPUTS xelatex -interaction=nonstopmode file.tex
TEXINPUTS=../Preambles:$TEXINPUTS xelatex -interaction=nonstopmode file.tex

# Deploy Quarto to GitHub Pages
./scripts/sync_to_docs.sh LectureN

# Quality score
python scripts/quality_score.py Quarto/file.qmd
```

---

## Quality Thresholds

| Score | Gate | Meaning |
|-------|------|---------|
| 80 | Commit | Good enough to save |
| 90 | PR | Ready for deployment |
| 95 | Excellence | Aspirational |

---

## Skills Quick Reference

| Command | What It Does |
|---------|-------------|
| `/compile-latex [file]` | 3-pass XeLaTeX + bibtex |
| `/deploy [LectureN]` | Render Quarto + sync to docs/ |
| `/extract-tikz [LectureN]` | TikZ → PDF → SVG |
| `/proofread [file]` | Grammar/typo/overflow review |
| `/visual-audit [file]` | Slide layout audit |
| `/pedagogy-review [file]` | Narrative, notation, pacing review |
| `/review-r [file]` | R code quality review |
| `/qa-quarto [LectureN]` | Adversarial Quarto vs Beamer QA |
| `/slide-excellence [file]` | Combined multi-agent review |
| `/translate-to-quarto [file]` | Beamer → Quarto translation |
| `/validate-bib` | Cross-reference citations |
| `/devils-advocate` | Challenge slide design |
| `/create-lecture` | Full lecture creation |
| `/commit [msg]` | Stage, commit, PR, merge |
| `/lit-review [topic]` | Literature search + synthesis |
| `/research-ideation [topic]` | Research questions + strategies |
| `/interview-me [topic]` | Interactive research interview |
| `/review-paper [file]` | Manuscript review |
| `/data-analysis [dataset]` | End-to-end R analysis |

---

## Beamer Custom Environments

| Environment | Effect | Use Case |
|---|---|---|
| `keybox` | Red accent background box | Key takeaways and important results |
| `highlightbox` | Light blue left-accent box | Highlighted points and remarks |
| `methodbox` | Dark blue left-accent box | Estimation methods and procedures |
| `assumptionbox` | Blue-bordered titled box | Formal assumptions (e.g., OLS, IV) |
| `definitionbox[Title]` | Blue-bordered titled box | Formal definitions |
| `resultbox` | Bold-bordered result box | Theorems, propositions, key results |
| `eqbox` | Subtle blue background | Featured equations |

## Quarto CSS Classes

| Class | Effect | Use Case |
|---|---|---|
| `.smaller` | 85% font | Dense content slides |
| `.smallest` | 80% font | Very dense reference slides |
| `.ippblue` | IP Paris dark blue text | Institutional color emphasis |
| `.ippaccent` | CREST blue text | Secondary emphasis |
| `.ipphighlight` | Vibrant blue text | Highlights and alerts |
| `.positive` | Green bold | Good/identified annotations |
| `.negative` | Red bold | Bad/problematic annotations |
| `.hi` | Bold primary blue | Inline emphasis |
| `.hi-red` | Bold red | Inline warning emphasis |
| `.keybox` | Red accent background box | Key takeaways |
| `.highlightbox` | Light blue left-accent box | Highlights |
| `.methodbox` | Dark blue left-accent box | Methods |
| `.assumptionbox` | Blue-bordered box | Assumptions |
| `.resultbox` | Bold-bordered box | Results |
| `.eqbox` | Subtle blue background | Equations |

---

## Current Project State

| Lecture | Beamer | Quarto | Key Content |
|---------|--------|--------|-------------|
| 1: Intro & Probability Review | `Lecture01_Intro.tex` | -- | Course overview, probability review, statistical inference |
| 2: Simple Regression | `Lecture02_SimpleRegression.tex` | -- | OLS derivation, assumptions (SLR.1-6), Gauss-Markov, R-squared |
| 3: Multiple Regression: Estimation | *planned* | -- | Matrix notation, OLS in matrix form, FWL, adjusted R-squared |
| 4: Multiple Regression: Inference | *planned* | -- | t-tests, F-tests, confidence intervals |
| 5: Asymptotics for OLS | *planned* | -- | Consistency, asymptotic normality, LLN/CLT |
| 6: Heteroskedasticity | *planned* | -- | Consequences, detection, robust SE, WLS/GLS |
| 7: Specification & Functional Form | *planned* | -- | Omitted variables, measurement error, functional form |
| 8: Instrumental Variables | *planned* | -- | Endogeneity, 2SLS, IV assumptions, weak instruments |
| 9: Simultaneous Equations | *planned* | -- | Supply-demand, identification, estimation |
| 10: Panel Data | *planned* | -- | FE, RE, first differencing, Hausman test |
| 11: Binary Response Models | *planned* | -- | Probit, logit, marginal effects |
| 12: Time Series Basics | *planned* | -- | Stationarity, AR/MA, spurious regression |
| 13: Advanced Topics / Review | *planned* | -- | Selected topics, course synthesis |
