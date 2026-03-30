# Codebook: NHANES 2007-2012 — Blood Volatile Organic Compounds and Airflow Obstruction

## Demographics (DEMO_E / DEMO_F / DEMO_G)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SEQN | Respondent sequence number | ID | - |
| RIDAGEYR | Age in years at screening | Continuous | 0-80 (80 = 80+) |
| RIAGENDR | Gender | Categorical | 1=Male, 2=Female |
| RIDRETH1 | Race/Hispanic origin | Categorical | 1=Mexican American, 2=Other Hispanic, 3=NH White, 4=NH Black, 5=Other/Multi-Racial |
| DMDEDUC2 | Education level (adults 20+) | Categorical | 1=Less than 9th grade, 2=9-11th grade, 3=High school grad/GED, 4=Some college/AA, 5=College graduate+ |
| INDFMPIR | Family income to poverty ratio | Continuous | 0-5 (5 = >=5.00) |

## Spirometry — Pre-Bronchodilator (SPX_E / SPX_F / SPX_G)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SPXNFVC | Baseline FVC (mL) | Continuous | mL |
| SPXNFEV1 | Baseline FEV1 (mL) | Continuous | mL |
| SPXNQFVC | Baseline FVC quality grade | Categorical | A-F |
| SPXNQFV1 | Baseline FEV1 quality grade | Categorical | A-F |

## Spirometry — Post-Bronchodilator (SPX_E / SPX_F / SPX_G)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SPXBFVC | 2nd test FVC (mL) — post-bronchodilator | Continuous | mL |
| SPXBFEV1 | 2nd test FEV1 (mL) — post-bronchodilator | Continuous | mL |
| SPXBQFVC | 2nd test FVC quality grade | Categorical | A-F |
| SPXBQFV1 | 2nd test FEV1 quality grade | Categorical | A-F |

## Airflow Obstruction Definitions (Derived)
| Variable | Description | Criteria |
|----------|-------------|----------|
| Pre_BD_obstruction | Pre-bronchodilator obstruction | FEV1/FVC < 0.70 |
| Non_reversible | Non-reversible obstruction (COPD-like) | Pre-BD FEV1/FVC < 0.70 AND post-BD FEV1/FVC < 0.70 |
| Reversible | Reversible obstruction (asthma-like) | Pre-BD FEV1/FVC < 0.70 AND post-BD FEV1/FVC >= 0.70 |
| No_obstruction | Reference group | Pre-BD FEV1/FVC >= 0.70 |

## Blood Volatile Organic Compounds (VOCWB_E / VOCWB_F / VOCWB_G)
| Variable | Description | Parent Compound | Type | LOD (ng/mL) |
|----------|-------------|----------------|------|-------------|
| LBXVBZ | Blood benzene | Benzene | Continuous | 0.024 |
| LBXVTO | Blood toluene | Toluene | Continuous | 0.025 |
| LBXVEB | Blood ethylbenzene | Ethylbenzene | Continuous | 0.024 |
| LBXVXY | Blood m-/p-xylene | m-/p-Xylene | Continuous | 0.024 |
| LBXVOX | Blood o-xylene | o-Xylene | Continuous | 0.024 |
| LBXVST | Blood styrene | Styrene | Continuous | 0.030 |
| LBXVCF | Blood chloroform | Chloroform | Continuous | 0.008 |
| LBXVBM | Blood bromodichloromethane | Bromodichloromethane | Continuous | 0.006 |
| LBXVCM | Blood dibromochloromethane | Dibromochloromethane | Continuous | 0.005 |
| LBXVBF | Blood bromoform | Bromoform | Continuous | 0.006 |
| LBXVME | Blood MTBE | Methyl tert-butyl ether | Continuous | 0.010 |
| LBXV4C | Blood tetrachloroethene | Tetrachloroethene | Continuous | 0.040 |
| LBXVTC | Blood trichloroethene | Trichloroethene | Continuous | 0.012 |
| LBXV1D | Blood 1,4-dichlorobenzene | 1,4-Dichlorobenzene | Continuous | 0.040 |

Note: 41 blood VOCs total are measured. Above are the most commonly detected and analytically relevant. Full list in NHANES VOC documentation.

## Smoking Status and Tobacco Smoke Exposure
| Variable | Source | Description | Type | Values |
|----------|--------|-------------|------|--------|
| SMQ020 | SMQ_E/F/G | Smoked at least 100 cigarettes in life | Categorical | 1=Yes, 2=No |
| SMQ040 | SMQ_E/F/G | Do you now smoke cigarettes | Categorical | 1=Every day, 2=Some days, 3=Not at all |
| SMD057 | SMQ_E/F/G | # cigarettes/day when quit | Continuous | Number/day |
| SMD650 | SMQ_E/F/G | Avg # cigarettes/day past 30 days | Continuous | Number/day |
| LBXCOT | COT_E/F/G | Serum cotinine (ng/mL) | Continuous | ng/mL (ETS biomarker) |
| Pack_years | Derived | (cigarettes/day / 20) × years smoked | Continuous | Pack-years |

## Body Measures and Physical Activity
| Variable | Source | Description | Type | Values |
|----------|--------|-------------|------|--------|
| BMXBMI | BMX_E/F/G | Body mass index (kg/m²) | Continuous | kg/m² |
| PAQ605 | PAQ_E/F/G | Vigorous recreational activities | Categorical | 1=Yes, 2=No |
| PAQ620 | PAQ_E/F/G | Moderate recreational activities | Categorical | 1=Yes, 2=No |

## Survey Design Variables
| Variable | Description | Type | Usage |
|----------|-------------|------|-------|
| WTMEC2YR | Full sample 2-year MEC examination weight | Weight | Divide by 3 for 6-year combined analysis |
| WTSVO2YR | VOC subsample 2-year weight | Weight | Use when analyzing VOC subsample; divide by 3 for 6-year |
| SDMVPSU | Masked variance pseudo-PSU | Design | Primary sampling unit |
| SDMVSTRA | Masked variance pseudo-stratum | Design | Stratum for variance estimation |

## Notes
- Blood VOCs measured by headspace SPME-GC-IDMS by CDC Division of Laboratory Sciences
- Spirometry performed on participants aged 6-79 following ATS/ERS guidelines
- Post-bronchodilator spirometry only performed on participants with pre-BD FEV1/FVC < LLN or < 0.70
- Blood VOC subsample: approximately one-third of MEC participants
- When combining VOC + spirometry data, use appropriate subsample weight (WTSVO2YR / 3)
- Replace values below LOD with LOD/sqrt(2)
- Log-transform blood VOC concentrations before regression due to right-skewed distributions
- Quality grades A, B, C acceptable for spirometry analysis; exclude D and F
