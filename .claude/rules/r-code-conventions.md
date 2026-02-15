---
paths:
  - "**/*.R"
  - "Figures/**/*.R"
  - "scripts/**/*.R"
---

# R Code Standards

**Standard:** Senior Principal Data Engineer + PhD researcher quality

---

## 1. Reproducibility

- `set.seed()` called ONCE at top (YYYYMMDD format)
- All packages loaded at top via `library()` (not `require()`)
- All paths relative to repository root
- `dir.create(..., recursive = TRUE)` for output directories

## 2. Core Packages

```r
# --- Econometrics ---
library(fixest)        # Fast FE estimation, cluster SE, IV
library(sandwich)      # Robust covariance estimators (HC, HAC)
library(lmtest)        # Diagnostic tests (coeftest, bptest, etc.)
library(ivreg)         # IV/2SLS estimation
library(plm)           # Panel data models (alt. to fixest)
library(modelsummary)  # Regression tables (preferred over stargazer)
library(broom)         # Tidy model output

# --- Data wrangling ---
library(dplyr)
library(tidyr)
library(haven)         # Read Stata/SPSS/SAS files
library(readr)

# --- Visualization ---
library(ggplot2)
```

## 3. Function Design

- `snake_case` naming, verb-noun pattern
- Roxygen-style documentation
- Default parameters, no magic numbers
- Named return values (lists or tibbles)

## 4. Domain Correctness — Econometrics Pitfalls

| Pitfall | Impact | Prevention |
|---------|--------|------------|
| `lm()` reports classical SE | Misleading under heteroskedasticity | Use `coeftest(mod, vcov = vcovHC(mod, "HC1"))` |
| `fixest::feols()` auto-clusters when FE present | Silently changes inference | Explicitly set `vcov` argument |
| `sandwich::vcovHC()` HC0 vs HC1 vs HC3 | Different small-sample corrections | Match the type to what slides describe |
| `modelsummary` default SE | May not show robust SE | Always pass `vcov` argument explicitly |
| `haven::read_dta()` labelled columns | Breaks numeric operations | Convert with `as.numeric()` |
| Wrong degrees of freedom | Affects F-tests, t-tests | Verify $n - k$ vs $n - k - 1$ |
| Forgetting to cluster SE | Underestimates SE in panel data | Always specify cluster variable |
| `ivreg` vs `feols` for IV | Different diagnostics, defaults | Document which package and why |

## 5. Visual Identity — IP Paris Palette

```r
# --- IP Paris / CREST institutional palette ---
ipp_blue      <- "#233E5C"   # Primary dark blue
crest_blue    <- "#144563"   # CREST blue
accent_blue   <- "#018BD3"   # Vibrant blue
light_blue    <- "#61ABF6"   # Light blue
warm_accent   <- "#C0392B"   # Red accent
positive_green <- "#15803d"
negative_red  <- "#b91c1c"
muted_gray    <- "#525252"
```

### Custom Theme
```r
theme_ipp <- function(base_size = 14) {
  theme_minimal(base_size = base_size) +
    theme(
      plot.title = element_text(face = "bold", color = ipp_blue),
      plot.subtitle = element_text(color = crest_blue),
      axis.title = element_text(color = ipp_blue),
      legend.position = "bottom"
    )
}
```

### Figure Dimensions for Beamer
```r
ggsave(filepath, width = 12, height = 5, bg = "transparent")
```

## 6. RDS Data Pattern

**Heavy computations saved as RDS; slide rendering loads pre-computed data.**

```r
saveRDS(result, file.path(out_dir, "descriptive_name.rds"))
```

## 7. Common Pitfalls

| Pitfall | Impact | Prevention |
|---------|--------|------------|
| Missing `bg = "transparent"` | White boxes on slides | Always include in ggsave() |
| Hardcoded paths | Breaks on other machines | Use relative paths |
| Not setting `options(scipen = 999)` | Coefficients in scientific notation | Set at top of script |

## 8. Line Length & Mathematical Exceptions

**Standard:** Keep lines <= 100 characters.

**Exception: Mathematical Formulas** -- lines may exceed 100 chars **if and only if:**

1. Breaking the line would harm readability of the math (influence functions, matrix ops, finite-difference approximations, formula implementations matching paper equations)
2. An inline comment explains the mathematical operation:
   ```r
   # Sieve projection: inner product of residuals onto basis functions P_k
   alpha_k <- sum(r_i * basis[, k]) / sum(basis[, k]^2)
   ```
3. The line is in a numerically intensive section (simulation loops, estimation routines, inference calculations)

**Quality Gate Impact:**
- Long lines in non-mathematical code: minor penalty (-1 to -2 per line)
- Long lines in documented mathematical sections: no penalty

## 9. Code Quality Checklist

```
[ ] Packages at top via library()
[ ] set.seed() once at top
[ ] All paths relative
[ ] Functions documented (Roxygen)
[ ] Figures: transparent bg, explicit dimensions
[ ] RDS: every computed object saved
[ ] Comments explain WHY not WHAT
[ ] Robust SE used by default (not classical)
[ ] Cluster variable specified for panel data
```
