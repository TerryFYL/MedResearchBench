# Codebook: NHANES 2005-2008 and 2015-2018 — METS-IR and Obstructive Sleep Apnea

## Demographics (DEMO)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SEQN | Respondent sequence number | ID | - |
| RIDAGEYR | Age in years at screening | Continuous | 0-80 (80 = 80+) |
| RIAGENDR | Gender | Categorical | 1=Male, 2=Female |
| RIDRETH1 | Race/Hispanic origin | Categorical | 1=Mexican American, 2=Other Hispanic, 3=NH White, 4=NH Black, 5=Other Race/Multi-Racial |
| DMDEDUC2 | Education level (adults 20+) | Categorical | 1=Less than 9th grade, 2=9-11th grade, 3=HS grad/GED, 4=Some college/AA, 5=College graduate+ |
| DMDMARTL | Marital status | Categorical | 1=Married, 2=Widowed, 3=Divorced, 4=Separated, 5=Never married, 6=Living with partner |
| INDFMPIR | Family income to poverty ratio | Continuous | 0-5 (5 = ≥5.00) |

## Sleep Disorder Questionnaire (SLQ)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SLQ050 | Ever told by doctor have sleep disorder | Categorical | 1=Yes, 2=No |
| SLQ060 | Ever told have sleep apnea | Categorical | 1=Yes, 2=No |
| SLQ030 | How often do you snore | Categorical | 0=Never, 1=Rarely, 2=Occasionally, 3=Frequently, 4=Almost always |
| SLQ040 | How often do you snort/stop breathing | Categorical | 0=Never, 1=Rarely, 2=Occasionally, 3=Frequently, 4=Almost always |
| SLQ120 | How often feel overly sleepy during day | Categorical | 0=Never, 1=Rarely, 2=Sometimes, 3=Often, 4=Almost always |

### OSA Case Definition
OSA identified by self-reported doctor-diagnosed sleep apnea (SLQ060 = 1) from the sleep disorder questionnaire administered by trained NHANES interviewers.

## Fasting Glucose (GLU)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| LBXGLU | Fasting glucose (mg/dL) | Continuous | mg/dL |

## Fasting Insulin (INS)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| LBXIN | Insulin (μU/mL) | Continuous | μU/mL |

## Lipid Panel — Triglycerides and HDL (TRIGLY, HDL)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| LBXTR | Triglycerides (mg/dL) | Continuous | mg/dL |
| LBDHDD | Direct HDL-cholesterol (mg/dL) | Continuous | mg/dL |

## Body Measures (BMX)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| BMXBMI | Body mass index (kg/m²) | Continuous | kg/m² |
| BMXWAIST | Waist circumference (cm) | Continuous | cm |
| BMXWT | Weight (kg) | Continuous | kg |
| BMXHT | Standing height (cm) | Continuous | cm |

## Blood Pressure (BPX)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| BPXSY1-3 | Systolic BP, readings 1-3 (mmHg) | Continuous | mmHg |
| BPXDI1-3 | Diastolic BP, readings 1-3 (mmHg) | Continuous | mmHg |

## Medical Conditions (MCQ, DIQ, BPQ)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| DIQ010 | Doctor told you have diabetes | Categorical | 1=Yes, 2=No, 3=Borderline |
| BPQ020 | Ever told you had high blood pressure | Categorical | 1=Yes, 2=No |
| MCQ160C | Ever told you had coronary heart disease | Categorical | 1=Yes, 2=No |
| MCQ160D | Ever told you had angina | Categorical | 1=Yes, 2=No |
| MCQ160E | Ever told you had heart attack | Categorical | 1=Yes, 2=No |
| MCQ160F | Ever told you had stroke | Categorical | 1=Yes, 2=No |
| MCQ160B | Ever told you had CHF | Categorical | 1=Yes, 2=No |

## Lifestyle Variables
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SMQ020 | Smoked at least 100 cigarettes in life | Categorical | 1=Yes, 2=No |
| SMQ040 | Do you now smoke cigarettes | Categorical | 1=Every day, 2=Some days, 3=Not at all |
| ALQ101 | Had at least 12 alcohol drinks/year | Categorical | 1=Yes, 2=No |
| PAQ605-PAQ680 | Physical activity variables | Categorical/Continuous | Varies |

## Insulin Resistance Index Calculations
| Index | Formula | Components |
|-------|---------|------------|
| **METS-IR** | ln((2 × FPG) + TG) × BMI / ln(HDL-C) | LBXGLU, LBXTR, BMXBMI, LBDHDD |
| **TyG** | ln(TG × FPG / 2) | LBXTR, LBXGLU |
| **TG/HDL-C** | TG / HDL-C | LBXTR, LBDHDD |
| **HOMA-IR** | FPG × Fasting Insulin / 405 | LBXGLU, LBXIN |

## Survey Design Variables
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| WTMEC2YR | MEC exam weight (2-year) | Continuous | Survey weight |
| WTSAF2YR | Fasting subsample weight (2-year) | Continuous | Survey weight |
| SDMVPSU | Masked variance pseudo-PSU | Categorical | PSU ID |
| SDMVSTRA | Masked variance pseudo-stratum | Categorical | Stratum ID |

### Multi-Cycle Weight Adjustment
- When pooling 4 NHANES cycles, divide 2-year weights by 4
- Use fasting subsample weights (WTSAF2YR / 4) for all analyses involving fasting laboratory measures
- Use MEC weights (WTMEC2YR / 4) for analyses using only interview and examination data

### Notes
- Sleep disorder questionnaire (SLQ) administered to adults aged 16+ years; study restricted to adults ≥20 years
- OSA is self-reported, not confirmed by polysomnography; this may underestimate true OSA prevalence
- NHANES 2009-2014 cycles did not include sleep apnea questionnaire items, creating a gap between 2008 and 2015
- METS-IR requires only fasting glucose, triglycerides, HDL-C, and BMI — no insulin measurement needed
