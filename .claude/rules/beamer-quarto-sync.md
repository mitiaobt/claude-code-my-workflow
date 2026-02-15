---
paths:
  - "Slides/**/*.tex"
  - "Quarto/**/*.qmd"
---

# Beamer → Quarto Auto-Sync Rule (MANDATORY)

**Every edit to a Beamer `.tex` file MUST be immediately synced to the corresponding Quarto `.qmd` file — automatically, without the user asking.** This is non-negotiable.

## The Rule

When you modify a Beamer `.tex` file, you MUST also apply the equivalent change to the Quarto `.qmd` (if it exists) **in the same task**, before reporting completion. Do NOT wait to be asked. Do NOT just "flag the drift." Just do it.

## Lecture Mapping

| Lecture | Beamer | Quarto |
|---------|--------|--------|
| 1 | `Slides/Lecture01_Intro.tex` | `Quarto/Lecture01_Intro.qmd` |
| 2 | `Slides/Lecture02_SimpleRegression.tex` | `Quarto/Lecture02_SimpleRegression.qmd` |
| 3 | `Slides/Lecture03_MultipleRegression.tex` | `Quarto/Lecture03_MultipleRegression.qmd` |
| 4 | `Slides/Lecture04_Inference.tex` | `Quarto/Lecture04_Inference.qmd` |
| 5 | `Slides/Lecture05_Asymptotics.tex` | `Quarto/Lecture05_Asymptotics.qmd` |
| 6 | `Slides/Lecture06_Heteroskedasticity.tex` | `Quarto/Lecture06_Heteroskedasticity.qmd` |
| 7 | `Slides/Lecture07_Specification.tex` | `Quarto/Lecture07_Specification.qmd` |
| 8 | `Slides/Lecture08_IV.tex` | `Quarto/Lecture08_IV.qmd` |
| 9 | `Slides/Lecture09_SimultaneousEq.tex` | `Quarto/Lecture09_SimultaneousEq.qmd` |
| 10 | `Slides/Lecture10_PanelData.tex` | `Quarto/Lecture10_PanelData.qmd` |
| 11 | `Slides/Lecture11_BinaryResponse.tex` | `Quarto/Lecture11_BinaryResponse.qmd` |
| 12 | `Slides/Lecture12_TimeSeries.tex` | `Quarto/Lecture12_TimeSeries.qmd` |
| 13 | `Slides/Lecture13_Advanced.tex` | `Quarto/Lecture13_Advanced.qmd` |

## Workflow (Every Time)

1. Apply fix to Beamer `.tex`
2. **Immediately** apply equivalent fix to Quarto `.qmd`
3. Compile Beamer (3-pass xelatex)
4. Render Quarto (`./scripts/sync_to_docs.sh LectureN`)
5. Only then report task complete

## LaTeX → Quarto Translation Reference

| Beamer | Quarto Equivalent |
| ------ | ----------------- |
| `\mutedtext{text}` | `[text]{style="color: #525252;"}` |
| `\key{text}` | `[**text**]{.hi-red}` |
| `\highlight{text}` | `[text]{.ipphighlight}` |
| `\textcolor{ippblue}{text}` | `[text]{.ippblue}` |
| `\textcolor{crestblue}{text}` | `[text]{.ippaccent}` |
| `\textcolor{accentblue}{text}` | `[text]{.ipphighlight}` |
| `\textcolor{warmaccent}{text}` | `[text]{.hi-red}` |
| `\textcolor{positive}{text}` | `[text]{.positive}` |
| `\textcolor{negative}{text}` | `[text]{.negative}` |
| `\item text` | `- text` |
| `\begin{keybox}` | `::: {.keybox}` |
| `\begin{highlightbox}` | `::: {.highlightbox}` |
| `\begin{methodbox}` | `::: {.methodbox}` |
| `\begin{assumptionbox}` | `::: {.assumptionbox}` |
| `\begin{definitionbox}[Title]` | `::: {.assumptionbox}\n### Title` |
| `\begin{resultbox}` | `::: {.resultbox}` |
| `\begin{eqbox}` | `::: {.eqbox}` |
| `$formula$` | `$formula$` (same) |

## When NOT to Sync

- Quarto file doesn't exist yet
- Change is LaTeX-only infrastructure (preamble, theme files)
- Explicitly told to skip Quarto sync

## Enforcement

Before marking any Beamer editing task as complete, check:
> "Did I also update the Quarto file?"

If the answer is no and a Quarto file exists, **you are NOT done.**

## When to Update This Table

After creating a new Quarto translation, add it to the mapping table above.
