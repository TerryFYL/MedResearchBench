# Codebook: NHANES 2007-2012 — Undiagnosed Obstructive Lung Disease

## Demographics (DEMO_E / DEMO_F / DEMO_G)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SEQN | Respondent sequence number | ID | - |
| RIDAGEYR | Age in years at screening | Continuous | 0-80 (80 = 80+) |
| RIAGENDR | Gender | Categorical | 1=Male, 2=Female |
| RIDRETH1 | Race/Hispanic origin | Categorical | 1=Mexican American, 2=Other Hispanic, 3=NH White, 4=NH Black, 5=Other/Multi-Racial |
| DMDEDUC2 | Education level (adults 20+) | Categorical | 1=Less than 9th grade, 2=9-11th grade, 3=High school grad/GED, 4=Some college/AA, 5=College graduate+ |
| INDFMPIR | Family income to poverty ratio | Continuous | 0-5 (5 = >=5.00) |
| DMDBORN4 | Country of birth | Categorical | 1=Born in 50 US states or DC, 2=Others |

## Spirometry — Pre-Bronchodilator (SPX_E / SPX_F / SPX_G)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SPXNFVC | Baseline FVC (mL) | Continuous | mL |
| SPXNFEV1 | Baseline FEV1 (mL) | Continuous | mL |
| SPXNFEV6 | Baseline FEV6 (mL) | Continuous | mL |
| SPXNPEF | Baseline PEF (L/s) | Continuous | L/s |
| SPXNF257 | Baseline FEF 25-75% (mL/s) | Continuous | mL/s |
| SPXNQFVC | Baseline FVC quality grade | Categorical | A-F (A=Exceeds ATS, F=Not valid) |
| SPXNQFV1 | Baseline FEV1 quality grade | Categorical | A-F |

## Spirometry — Post-Bronchodilator (SPX_E / SPX_F / SPX_G)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SPXBFVC | 2nd test FVC (mL) — post-bronchodilator | Continuous | mL |
| SPXBFEV1 | 2nd test FEV1 (mL) — post-bronchodilator | Continuous | mL |
| SPXBQFVC | 2nd test FVC quality grade | Categorical | A-F |
| SPXBQFV1 | 2nd test FEV1 quality grade | Categorical | A-F |

## Airflow Obstruction Definitions (Derived)
| Variable | Description | Criteria | Classification |
|----------|-------------|----------|----------------|
| LLN_obstruction | Obstruction by lower limit of normal | FEV1/FVC < age/sex/race/height-specific LLN (Hankinson 1999) | Binary |
| GOLD_obstruction | Obstruction by GOLD fixed ratio | FEV1/FVC < 0.70 | Binary |
| GOLD_stage | GOLD severity staging | Stage I: FEV1 >=80% predicted; Stage II: 50-79%; Stage III: 30-49%; Stage IV: <30% | Ordinal |
| Diagnosis_status | Diagnosed vs undiagnosed | Diagnosed: self-reported COPD/emphysema/bronchitis; Undiagnosed: spirometric obstruction without self-report | Categorical |

## Medical Conditions Questionnaire (MCQ_E / MCQ_F / MCQ_G)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| MCQ160G | Ever told you have emphysema | Categorical | 1=Yes, 2=No |
| MCQ160K | Ever told you have chronic bronchitis | Categorical | 1=Yes, 2=No |
| MCQ160P | Ever told you have COPD (2011-2012 only) | Categorical | 1=Yes, 2=No |
| MCQ010 | Ever told you have asthma | Categorical | 1=Yes, 2=No |
| MCQ160B | Ever told you have heart failure | Categorical | 1=Yes, 2=No |
| MCQ160C | Ever told you have coronary heart disease | Categorical | 1=Yes, 2=No |
| MCQ160F | Ever told you have a stroke | Categorical | 1=Yes, 2=No |
| MCQ220 | Ever told you have cancer/malignancy | Categorical | 1=Yes, 2=No |
| DIQ010 | Doctor told you have diabetes | Categorical | 1=Yes, 2=No, 3=Borderline |

## Respiratory Symptoms (RDQ / MCQ modules)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| RDQ070 | Wheezing or whistling in chest past 12 months | Categorical | 1=Yes, 2=No |
| RDQ140 | Had a dry cough at night in past 12 months | Categorical | 1=Yes, 2=No |
| RDQ031 | Cough on most days for 3+ months | Categorical | 1=Yes, 2=No |
| RDQ050 | Phlegm on most days for 3+ months | Categorical | 1=Yes, 2=No |

## Smoking History (SMQ_E / SMQ_F / SMQ_G)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SMQ020 | Smoked at least 100 cigarettes in life | Categorical | 1=Yes, 2=No |
| SMQ040 | Do you now smoke cigarettes | Categorical | 1=Every day, 2=Some days, 3=Not at all |
| SMD030 | Age started smoking cigarettes regularly | Continuous | Years |
| SMD057 | # cigarettes smoked per day when quit | Continuous | Number/day |
| SMD641 | # cigarettes smoked per day now | Continuous | Number/day |
| SMD650 | Average # cigarettes/day during past 30 days | Continuous | Number/day |

## Healthcare Utilization and General Health (HUQ_E / HUQ_F / HUQ_G)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| HUQ010 | General health condition | Categorical | 1=Excellent, 2=Very good, 3=Good, 4=Fair, 5=Poor |
| HUQ030 | Routine place to go for healthcare | Categorical | 1=Yes, 2=No |
| HUQ051 | # times received healthcare over past year | Continuous | 0-99 |
| HIQ011 | Covered by health insurance | Categorical | 1=Yes, 2=No |

## Prescription Medications (RXQ_RX)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| RXDDRUG | Generic drug name | Text | - |
| RXDDRGID | Generic drug code | Code | Used to identify respiratory medications |

## Survey Design Variables
| Variable | Description | Type | Usage |
|----------|-------------|------|-------|
| WTMEC2YR | Full sample 2-year MEC examination weight | Weight | Divide by 3 for 6-year combined analysis |
| SDMVPSU | Masked variance pseudo-PSU | Design | Primary sampling unit |
| SDMVSTRA | Masked variance pseudo-stratum | Design | Stratum for variance estimation |

## Notes on Multi-Cycle Combination
- When combining 3 cycles (2007-2008, 2009-2010, 2011-2012), divide WTMEC2YR by 3
- SEQN is unique within cycle but not across cycles; create composite ID with cycle identifier
- Spirometry protocols were identical across all three cycles (same equipment and procedures)
- Post-bronchodilator spirometry was only performed on participants with baseline obstruction (FEV1/FVC < LLN or < 0.70)
- NHANES III reference equations (Hankinson et al. 1999) used for predicted values and LLN calculation
- Note: NHANES used pre-bronchodilator spirometry as baseline; GOLD criteria technically require post-bronchodilator values, but pre-bronchodilator estimates provide upper bound for COPD prevalence
