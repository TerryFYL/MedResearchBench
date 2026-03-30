# Codebook: NHANES 2011-2018 — NAFLD Prevalence and Risk Factors

## Demographics (DEMO)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SEQN | Respondent sequence number | ID | - |
| RIDAGEYR | Age in years at screening | Continuous | 0-80 (80 = 80+) |
| RIAGENDR | Gender | Categorical | 1=Male, 2=Female |
| RIDRETH3 | Race/Hispanic origin with NH Asian | Categorical | 1=Mexican American, 2=Other Hispanic, 3=NH White, 4=NH Black, 6=NH Asian, 7=Other/Multi-Racial |
| DMDEDUC2 | Education level (adults 20+) | Categorical | 1=Less than 9th grade, 2=9-11th grade, 3=HS grad/GED, 4=Some college/AA, 5=College graduate+ |
| INDFMPIR | Family income to poverty ratio | Continuous | 0-5 (5 = >=5.00) |

## Liver Function Tests (BIOPRO — Standard Biochemistry Profile)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| LBXSATSI | ALT (U/L) | Continuous | U/L |
| LBXSASSI | AST (U/L) | Continuous | U/L |
| LBXSGTSI | GGT (U/L) | Continuous | U/L |
| LBXSAPSI | Alkaline phosphatase (U/L) | Continuous | U/L |
| LBXSTB | Total bilirubin (mg/dL) | Continuous | mg/dL |
| LBXSAL | Albumin (g/dL) | Continuous | g/dL |

## Complete Blood Count (CBC)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| LBXPLTSI | Platelet count (1000 cells/uL) | Continuous | 1000 cells/uL |

## Fasting Glucose and Insulin (GLU, INS)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| LBXGLU | Fasting glucose (mg/dL) | Continuous | mg/dL |
| LBXIN | Insulin (uU/mL) | Continuous | uU/mL |

## Glycohemoglobin (GHB)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| LBXGH | Glycohemoglobin HbA1c (%) | Continuous | % |

## Lipid Panel (TRIGLY, HDL, TCHOL)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| LBXTR | Triglycerides (mg/dL) | Continuous | mg/dL |
| LBDHDD | Direct HDL-cholesterol (mg/dL) | Continuous | mg/dL |
| LBXTC | Total cholesterol (mg/dL) | Continuous | mg/dL |

## Body Measures (BMX)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| BMXBMI | Body Mass Index (kg/m^2) | Continuous | kg/m^2 |
| BMXWAIST | Waist circumference (cm) | Continuous | cm |
| BMXWT | Weight (kg) | Continuous | kg |
| BMXHT | Standing height (cm) | Continuous | cm |

## Hepatitis Serology (HEPA, HEPC)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| LBXHBS | Hepatitis B surface antigen (HBsAg) | Categorical | 1=Positive, 2=Negative |
| LBXHCR | Hepatitis C RNA (confirmed) | Categorical | 1=Positive, 2=Negative |
| LBDHCV | Hepatitis C antibody | Categorical | 1=Positive, 2=Negative |

## Alcohol Use (ALQ)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| ALQ101 | Had at least 12 alcohol drinks/1 year | Categorical | 1=Yes, 2=No |
| ALQ120Q | How often drink alcohol over past 12 months | Continuous | days |
| ALQ120U | Unit for ALQ120Q | Categorical | 1=Week, 2=Month, 3=Year |
| ALQ130 | Average # alcoholic drinks/day past 12 months | Continuous | drinks/day |
| ALQ141Q | # days have 4/5+ drinks in past 12 months | Continuous | days |

## Diabetes (DIQ)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| DIQ010 | Doctor told you have diabetes | Categorical | 1=Yes, 2=No, 3=Borderline |
| DIQ050 | Taking insulin now | Categorical | 1=Yes, 2=No |
| DIQ070 | Taking diabetic pills | Categorical | 1=Yes, 2=No |

## Blood Pressure (BPX, BPQ)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| BPXSY1-3 | Systolic BP, readings 1-3 (mmHg) | Continuous | mmHg |
| BPXDI1-3 | Diastolic BP, readings 1-3 (mmHg) | Continuous | mmHg |
| BPQ050A | Now taking prescribed medicine for HBP | Categorical | 1=Yes, 2=No |

## Derived Variables / Diagnostic Indices
| Variable | Description | Derivation |
|----------|-------------|------------|
| USFLI | US Fatty Liver Index | Composite of age, race/ethnicity, GGT, fasting insulin, fasting glucose (score 0-100, ≥30 = NAFLD) |
| NFS | NAFLD Fibrosis Score | -1.675 + 0.037 × age + 0.094 × BMI + 1.13 × IFG/diabetes + 0.99 × AST/ALT − 0.013 × platelet − 0.66 × albumin |
| FIB-4 | Fibrosis-4 Index | (Age × AST) / (Platelet × √ALT) |
| NAFLD | NAFLD status (binary) | USFLI ≥30 AND no excessive alcohol AND HBsAg negative AND anti-HCV negative |
| Excessive alcohol | Alcohol exclusion criterion | >2 drinks/day (men) or >1 drink/day (women) |
| BMI category | Weight classification | <25=Normal, 25-29.9=Overweight, 30-34.9=Obese I, ≥35=Obese II-III |

## Survey Design Variables
| Variable | Description |
|----------|-------------|
| WTMEC2YR | Full sample 2-year MEC exam weight |
| WTSAF2YR | Fasting subsample 2-year weight |
| SDMVPSU | Masked variance pseudo-PSU |
| SDMVSTRA | Masked variance pseudo-stratum |

## Notes
- Use WTMEC2YR for analyses not requiring fasting blood work; use WTSAF2YR for analyses involving fasting glucose, insulin, or triglycerides
- When pooling 4 NHANES cycles, divide 2-year weights by 4
- USFLI was developed and validated specifically for the U.S. population using NHANES data
- NFS includes age in its calculation — results in elderly populations may be biased toward higher fibrosis scores
- Excessive alcohol thresholds: >2 drinks/day for men, >1 drink/day for women (AASLD guidelines)
- Hepatitis B and C serology available for most adult participants; missing values require exclusion
- ALT/AST assay methods may vary slightly across NHANES cycles — check documentation for each cycle
