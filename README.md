# MedResearchBench

**The first benchmark for evaluating AI systems on medical clinical research tasks.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Tasks: 16](https://img.shields.io/badge/Tasks-16-blue.svg)]()
[![Domains: 8](https://img.shields.io/badge/Domains-8-green.svg)]()

> Paper: *MedResearchBench: A Multi-Domain Benchmark for Evaluating AI Research Agents on Clinical Medical Research* (preprint forthcoming)

---

## Overview

MedResearchBench evaluates whether AI systems can conduct **clinically sound, publication-quality medical research** — from raw public data to STROBE-compliant manuscripts. It addresses a critical gap: existing AI research benchmarks (ResearchClawBench, ScienceBench) focus on fundamental sciences and do not capture the unique challenges of clinical epidemiology.

**Key features:**
- 16 tasks across 8 clinical domains (cardiovascular, oncology, mental health, metabolic, respiratory, neurology, infectious disease, )
- Ground truth from 16 published papers (IF range: 2.3–51.0)
- 6 medical-specific evaluation dimensions
- Anti-paper-mill filtering criteria
- Compatible with ResearchClawBench task format

---

## Benchmark Structure

```
tasks/{TaskID}/
├── task_info.json          # Research question, data references, metadata
├── data/
│   ├── codebook.md         # Variable definitions + survey design variables
│   └── placeholder.txt     # Data source and download instructions
├── related_work/
│   └── references.md       # 3-4 related papers
└── target_study/
    ├── paper_info.md       # Ground truth paper metadata (PMID, DOI, journal)
    ├── checklist.json      # 5 evaluation items across 6 dimensions
    └── images/             # Figure description placeholders
```

Data files are **not included** in this repository. All tasks use publicly available datasets (NHANES, SEER) downloadable from CDC and NCI websites. See each task's `data/placeholder.txt` for download instructions.

---

## Task List

| # | Task ID | Domain | Tier | Research Question | Dataset |
|---|---------|--------|------|------------------|---------|
| 1 | Cardio_000 | Cardiovascular | 1 | Dietary sodium and hypertension dose-response | NHANES 2017-2018 |
| 2 | Cardio_003 | Cardiovascular | 2 | Racial disparities in hypertension control | NHANES 2013-2018 |
| 3 | Onco_000 | Oncology | 2 | CRC survival trends by race/ethnicity | SEER 1992-2018 |
| 4 | Onco_002 | Oncology | 3 | SES disparities in CRC staging and survival | SEER-Medicare 1991-2010 |
| 5 | Mental_000 | Mental Health | 2 | Sleep duration and depression, U-shaped | NHANES 2009-2016 |
| 6 | Mental_002 | Mental Health | 1 | Depression prevalence trends 2005-2016 | NHANES 2005-2016 |
| 7 | Metabolic_000 | Metabolic | 1 | HOMA-IR threshold for metabolic syndrome | NHANES 2011-2018 |
| 8 | Metabolic_002 | Metabolic | 3 | TSH and all-cause/CV mortality (nonlinear) | NHANES III + NDI |
| 9 | Metabolic_003 | Metabolic | 1 | NAFLD prevalence and fibrosis risk factors | NHANES 2011-2018 |
| 10 | Neuro_002 | Neurology | 2 | Heavy metal exposure and cognitive function | NHANES 2011-2014 |
| 11 | Neuro_003 | Neurology | 3 | Dietary antioxidants and Parkinson's mortality | NHANES 2007-2018 + NDI |
| 12 | Infection_000 | Infectious Disease | 2 | HBV seroprevalence and vaccine coverage trends | NHANES 1999-2016 |
| 13 | Infection_001 | Infectious Disease | 3 | HPV vaccine effectiveness (12-year monitoring) | NHANES 2003-2018 |
| 14 | Respiratory_000 | Respiratory | 1 | Air pollution biomarkers and lung function | NHANES 2007-2012 |
| 15 | Respiratory_001 | Respiratory | 3 | Undiagnosed COPD prevalence and mortality | NHANES III + 2007-2012 |
| 16 | Respiratory_003 | Respiratory | 2 | OSA risk and metabolic comorbidities | NHANES 2005-2018 |

**Difficulty tiers:** Tier 1 (Foundational) · Tier 2 (Intermediate) · Tier 3 (Advanced)

---

## Evaluation Dimensions

| Dimension | Description |
|-----------|-------------|
| `statistical_methodology` | Appropriate method selection, survey-weighted analysis, model specification |
| `results_accuracy` | Correct numerical results, effect sizes with 95% CI |
| `visualization_quality` | Publication-ready figures following domain conventions |
| `clinical_interpretation` | Clinically meaningful, actionable conclusions |
| `confounding_sensitivity` | Progressive adjustment, sensitivity analyses, residual confounding |
| `reporting_compliance` | STROBE/CONSORT/PRISMA adherence |

Scoring: 0–100 per item, where **50 = matches ground truth paper quality**. Scores above 50 indicate AI output exceeded the published paper on that criterion.

---

## Baseline Results

We evaluated an agentic data2paper pipeline (AI Research Army) on 3 pilot tasks spanning all difficulty tiers (2026-03-30):

| Task | Tier | Score | Grade |
|------|------|-------|-------|
| Cardio_000 | 1 | 72/100 | B |
| Mental_000 | 2 | 69/100 | C+ |
| Metabolic_002 | 3 | 75/100 | B |
| **Mean** | | **72/100** | **B** |

Detailed evaluation reports are in `bench-runs/{TaskID}/evaluation.json`.

**Key finding:** Survey-weighted methodology was correctly implemented in all 3 tasks. Primary limitation: results accuracy (mean 58.7/100) due to covariate incompleteness and reference group misspecification.

---

## Comparison with ResearchClawBench

| Feature | ResearchClawBench | MedResearchBench |
|---------|------------------|-----------------|
| Domains | 10 (fundamental science) | 8 (clinical medicine) |
| Data paradigm | Experimental/simulated | Population surveys + registries |
| Statistical focus | ML metrics | Survey-weighted inference, survival analysis |
| Reporting standards | Informal | STROBE/CONSORT (formal) |
| Unique requirement | — | Codebook + complex survey design |
| Confounding evaluation | Not included | Dedicated dimension |

---

## Citation

```bibtex
@article{tian2026medresearchbench,
  title={MedResearchBench: A Multi-Domain Benchmark for Evaluating AI Research Agents on Clinical Medical Research},
  author={Tian, Zhanxiao},
  journal={arXiv preprint},
  year={2026}
}
```

---

## License

MIT License. Task materials are derived from publicly available datasets (NHANES: CDC public domain; SEER: NCI public domain). Ground truth paper metadata is used for research evaluation purposes only.
