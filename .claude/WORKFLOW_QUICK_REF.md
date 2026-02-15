# Workflow Quick Reference

**Model:** Contractor (you direct, Claude orchestrates)

---

## The Loop

```
Your instruction
    ↓
[PLAN] (if multi-file or unclear) → Show plan → Your approval
    ↓
[EXECUTE] Implement, verify, done
    ↓
[REPORT] Summary + what's ready
    ↓
Repeat
```

---

## I Ask You When

- **Design forks:** "Option A (fast) vs. Option B (robust). Which?"
- **Code ambiguity:** "Spec unclear on X. Assume Y?"
- **Replication edge case:** "Just missed tolerance. Investigate?"
- **Scope question:** "Also refactor Y while here, or focus on X?"

---

## I Just Execute When

- Code fix is obvious (bug, pattern application)
- Verification (tolerance checks, tests, compilation)
- Documentation (logs, commits)
- Plotting (per established standards)
- Deployment (after you approve, I ship automatically)

---

## Quality Gates (No Exceptions)

| Score | Action |
|-------|--------|
| >= 80 | Ready to commit |
| < 80  | Fix blocking issues |

---

## Non-Negotiables

- **Path convention:** `here::here()` for R, relative paths for LaTeX (`../Preambles/`, `../Figures/`)
- **Seed convention:** `set.seed(YYYYMMDD)` once at top of every stochastic R script
- **Figure standards:** transparent bg, IP Paris theme (`theme_ipp()`), 300 DPI, `width = 12, height = 5`
- **Color palette:** IP Paris blues (`#233E5C`, `#144563`, `#018BD3`, `#61ABF6`) + red accent (`#C0392B`)
- **Tolerance thresholds:** Point estimates 1e-6, SE 1e-4, t-stats 1e-3, p-values 1e-4
- **Robust SE by default:** Never report classical SE without explicit justification
- **Cluster SE for panels:** Always specify cluster variable for panel data

---

## Preferences

**Visual:** IP Paris palette, transparent backgrounds, minimal ggplot2 themes
**Reporting:** Concise bullets; details on request
**Session logs:** Always (post-plan, incremental, end-of-session)
**Replication:** Strict — flag anything outside tolerance thresholds

---

## Exploration Mode

For experimental work, use the **Fast-Track** workflow:
- Work in `explorations/` folder
- 60/100 quality threshold (vs. 80/100 for production)
- No plan needed — just a research value check (2 min)
- See `.claude/rules/exploration-fast-track.md`

---

## Next Step

You provide task → I plan (if needed) → Your approval → Execute → Done.
