# MedResearchBench Baseline Evaluation — Results Summary

**Evaluation Date:** 2026-03-30
**Pipeline:** AI Research Army (data2paper)
**Evaluator:** Claude Sonnet 4.6 (automated scoring vs. checklist.json)

---

## Overall Scores

| Task ID | Domain | Tier | Weighted Score | Grade | Pass |
|---------|--------|------|---------------|-------|------|
| Cardio_000 | Cardiovascular | Tier 1 — Foundational | **72/100** | B | ✓ |
| Mental_000 | Mental Health | Tier 2 — Intermediate | **69/100** | C+ | ✓ |
| Metabolic_002 | Metabolic/Endocrine | Tier 3 — Advanced | **75/100** | B | ✓ |
| **Average** | | | **72/100** | B | ✓ |

---

## Dimension-Level Scores

| Dimension | Weight | Cardio_000 | Mental_000 | Metabolic_002 | Average |
|-----------|--------|-----------|-----------|--------------|---------|
| statistical_methodology | 0.25 | 60 | 78 | 92 | 76.7 |
| results_accuracy | 0.25 | 72 | 52 | 52 | 58.7 |
| confounding_sensitivity | 0.20 | 68 | 76 | 75 | 73.0 |
| clinical_interpretation | 0.15 | 88 | 86 | 76 | 83.3 |
| reporting_compliance | 0.15 | 80 | 62 | 88 | 76.7 |
| **Weighted Total** | 1.00 | **72** | **69** | **75** | **72** |

---

## Per-Task Detailed Results

### Cardio_000 — Dietary Sodium and Hypertension (NHANES 2017-2018)

**Score: 72/100 (B)**

| Dimension | Score | Key Findings |
|-----------|-------|-------------|
| statistical_methodology | 60/100 | ✓ Survey-weighted logistic regression; ✓ RCS 4 knots at correct percentiles. Missing: 4th progressive model, z-score standardization, marital status/fiber/cholesterol covariates |
| results_accuracy | 72/100 | ✓ Null association confirmed (OR=1.04 vs target ~1.00); ✓ Na/K ratio borderline p=0.099; direction matches target |
| confounding_sensitivity | 68/100 | ✓ Subgroup by sex/age/BMI; ✓ significant age effect (≥60yr OR=1.19, p=0.032). Missing: formal p-interaction values |
| clinical_interpretation | 88/100 | ✓ Reverse causation, measurement limitation, population vs. individual inference all discussed |
| reporting_compliance | 80/100 | ✓ STROBE compliant; CI throughout. n=4,137 vs target n=5,569 (26% smaller) |

**Key Numbers:**
- Analytical N: 4,137 (target: 5,569)
- Hypertension prevalence: 39.8% (weighted)
- Sodium fully-adjusted OR: 1.038 (p=0.387) → null association confirmed
- Na/K ratio OR: 1.141 (p=0.099) → borderline trend
- Represented population: ~214 million U.S. adults

**Primary Gaps:** Missing z-score standardization, 4-model progressive adjustment, and three additional covariates (marital status, fiber, cholesterol).

---

### Mental_000 — Sleep Duration and Depression (NHANES 2009-2016)

**Score: 69/100 (C+)**

| Dimension | Score | Key Findings |
|-----------|-------|-------------|
| statistical_methodology | 78/100 | ✓ Survey-weighted logistic regression; ✓ piecewise regression with AIC breakpoint; ✓ 4-cycle pooling with adjusted weights. Missing: marital status covariate; reference group 7h vs target 8h |
| results_accuracy | 52/100 | ✓ U-shaped association confirmed; ✓ inflection at 8h. CRITICAL: Reference group mismatch (7h vs 8h) shifts all ORs systematically |
| confounding_sensitivity | 76/100 | ✓ 3-model progressive adjustment; ✓ reverse causation discussed; attenuation pattern documented. Missing: formal p-interaction values |
| clinical_interpretation | 86/100 | ✓ HPA axis, inflammation, monoamine mechanisms; ✓ bidirectional relationship; ✓ CBT-I recommendation; ✓ 8h vs AASM 7h discrepancy acknowledged |
| reporting_compliance | 62/100 | ✓ STROBE; ✓ PHQ-9 validated. n=19,816 vs target n=25,962 (24% smaller); reference group deviation |

**Key Numbers:**
- Analytical N: 19,816 (target: 25,962)
- Depression prevalence: 7.9% (weighted)
- <6h sleep OR: 3.04 [2.34, 3.94] using 7h reference (target: 2.73 using 8h reference)
- ≥10h sleep OR: 2.15 [1.58, 2.93] using 7h reference (target: 2.35 using 8h reference)
- Optimal inflection point: 8 hours (AIC minimum, data-driven)

**Primary Gaps:** Reference group should be 8h not 7h (most impactful deduction); smaller sample from stricter exclusion criteria; marital status absent from Model 2.

---

### Metabolic_002 — TSH and Mortality in Euthyroid Diabetics (NHANES III)

**Score: 75/100 (B)**

| Dimension | Score | Key Findings |
|-----------|-------|-------------|
| statistical_methodology | 92/100 | ✓ RCS 3 knots at 25/50/75 percentiles; ✓ Cox PH 3 progressive models matching checklist; ✓ Wald F nonlinearity test. Minor: Schoenfeld PH assumption not formally reported |
| results_accuracy | 52/100 | ✓ Nonlinearity confirmed (AC: p=0.018, CVD: p=0.007); ✓ TSH tertile boundaries exact match (1.30/2.10). Low-normal TSH HR substantially attenuated: AC 1.15 vs target 1.39; CVD 1.22 vs target 1.69 |
| clinical_interpretation | 76/100 | ✓ Medium-normal TSH optimal range defined; ✓ age <60 HR=1.70 with thyroid aging hypothesis; ✓ TPO limitation acknowledged. Slight overstatement of "both extremes 30-40% higher" given low-normal NS |
| confounding_sensitivity | 75/100 | ✓ T4 restriction, CRP adjustment, iodine adjustment sensitivity analyses; ✓ TPO limitation explicitly noted. Missing: formal P for interaction by age/sex |
| reporting_compliance | 88/100 | ✓ STROBE; ✓ euthyroid definition explicit; ✓ P for nonlinearity formally reported. N=1,709 vs target 1,830 (6.6% smaller) |

**Key Numbers:**
- Analytical N: 1,709 (target: 1,830)
- All-cause deaths: 1,253 (73%); CVD deaths: 506 (30%)
- Median follow-up: 15.8 years (target: 17.1 years)
- High-normal TSH all-cause HR: 1.25 [1.08–1.43] p=0.039 (target: 1.31 [1.07–1.61])
- Low-normal TSH all-cause HR: 1.15 [1.00–1.32] p=0.22 (target: 1.39 [1.12–1.73]) — NON-SIGNIFICANT
- Age <60 high-normal TSH HR: 1.70 (p=0.012) — notable subgroup finding

**Primary Gaps:** Low-normal TSH HR substantially attenuated vs target (–17% for AC, –28% for CVD), failing bilateral U-shape significance. Likely causes: fewer excluded participants, possible mortality linkage differences (public vs restricted-access), unmeasured confounders (frailty, HEI, TPO antibodies).

---

## Cross-Task Patterns and Insights

### Consistent Strengths
1. **Survey-weighted methodology correctly implemented** across all 3 tasks — core requirement satisfied
2. **Publication-quality figures generated** — RCS curves, forest plots, dose-response visualizations
3. **STROBE-format manuscripts written** — complete IMRAD structure with embedded numeric tables
4. **Internal consistency** — manuscript numbers precisely match CSV analysis output files in all tasks
5. **Clinical interpretation quality** — mechanisms, limitations, and public health implications well-covered

### Consistent Weaknesses
1. **Sample size deficits** across all 3 tasks (range: 6.6%–26% smaller than target)
   - Root cause: stricter covariate completeness requirements; target studies may use indicator variables for missing data
2. **Results accuracy** is the lowest-scoring dimension across all tasks (avg 58.7/100)
   - Cardio_000: OR magnitude mismatch due to missing covariates and model specification
   - Mental_000: Reference group mismatch (7h vs 8h) causing systematic OR inflation
   - Metabolic_002: Low-normal TSH HR attenuation — public data limitations vs restricted-access
3. **Missing covariates**: All 3 tasks had at least 1 missing covariate (marital status in Cardio/Mental; frailty/HEI in Metabolic)
4. **Formal p-interaction values** not reported in subgroup analyses (all 3 tasks)

### Task-Specific Highlights
- **Cardio_000**: Reverse causation discussion was outstanding; Na/K ratio borderline finding is biologically plausible
- **Mental_000**: AIC-based breakpoint selection (8h) was a methodological strength; age-stratified U-shape was nuanced
- **Metabolic_002**: Highest methodology score (92/100); age-stratified effect (<60yr HR=1.70) was an original finding

---

## Benchmark Baseline Assessment

| Metric | Value | Interpretation |
|--------|-------|---------------|
| Mean Score | 72/100 | B-level baseline performance |
| Score Range | 69–75 | Low variance — consistent quality across tasks |
| All Tasks Pass | 3/3 | 100% pass rate (threshold: ≥60/100) |
| Methodology Correct | 3/3 | Survey-weighted analysis in all tasks |
| Results Partially Replicable | 3/3 | Direction correct; effect sizes attenuated |

**Conclusion:** The AI Research Army pipeline achieves B-level baseline performance (mean 72/100) across diverse epidemiological research tasks. Core methodological requirements are consistently met. Primary improvement areas are (1) covariate completeness against target specifications, (2) reference group alignment for categorical exposures, and (3) effect size accuracy for complex multi-variable outcomes. These findings establish a quantitative baseline for Section 4 of the MedResearchBench evaluation paper.

---

*Generated: 2026-03-30 | Pipeline: AI Research Army data2paper | Evaluator: Claude Sonnet 4.6*
