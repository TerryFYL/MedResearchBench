# Codebook: NHANES 2013-2018 (Pooled 3 Cycles) — Hypertension Racial/Ethnic Disparities

## Demographics (DEMO)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SEQN | Respondent sequence number | ID | - |
| RIDAGEYR | Age in years at screening | Continuous | 18-80 (80 = 80+) |
| RIAGENDR | Gender | Categorical | 1=Male, 2=Female |
| RIDRETH3 | Race/Hispanic origin with NH Asian | Categorical | 1=Mexican American, 2=Other Hispanic, 3=NH White, 4=NH Black, 6=NH Asian, 7=Other/Multi-Racial |
| DMDEDUC2 | Education level (adults 20+) | Categorical | 1=Less than 9th grade, 2=9-11th grade, 3=HS grad/GED, 4=Some college/AA, 5=College graduate+ |
| INDFMPIR | Family income to poverty ratio | Continuous | 0-5 |
| HIQ011 | Covered by health insurance | Categorical | 1=Yes, 2=No |

## Blood Pressure Examination (BPX)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| BPXSY1-3 | Systolic BP readings 1-3 | Continuous | mmHg |
| BPXDI1-3 | Diastolic BP readings 1-3 | Continuous | mmHg |

## Blood Pressure Questionnaire (BPQ)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| BPQ020 | Ever told you had high blood pressure | Categorical | 1=Yes, 2=No |
| BPQ040A | Taking prescription for hypertension | Categorical | 1=Yes, 2=No |
| BPQ050A | Now taking prescribed medicine for HBP | Categorical | 1=Yes, 2=No |

## Comorbidities
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| DIQ010 | Doctor told you have diabetes | Categorical | 1=Yes, 2=No, 3=Borderline |
| MCQ160B | Ever told had congestive heart failure | Categorical | 1=Yes, 2=No |
| MCQ160C | Ever told had coronary heart disease | Categorical | 1=Yes, 2=No |
| MCQ160D | Ever told had angina/angina pectoris | Categorical | 1=Yes, 2=No |
| MCQ160E | Ever told had heart attack | Categorical | 1=Yes, 2=No |
| MCQ160F | Ever told had a stroke | Categorical | 1=Yes, 2=No |

## Body Measures (BMX)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| BMXBMI | Body Mass Index (kg/m^2) | Continuous | kg/m^2 |

## Prescription Medications (RXQ_RX)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| RXDDRUG | Generic drug name | Text | - |
| RXDDRGID | Drug ID | Text | - |
| RXDCOUNT | Number of prescription medications taken | Continuous | count |

## Derived Variables
| Variable | Description | Derivation |
|----------|-------------|------------|
| Hypertension | Binary: has hypertension | Mean SBP >= 140 OR mean DBP >= 90 OR currently taking antihypertensive medication |
| Awareness | Binary: aware of hypertension (among those with HTN) | Self-report of physician diagnosis (BPQ020=1) |
| Treatment | Binary: currently treated (among those aware) | Currently taking antihypertensive medication |
| Control | Binary: BP controlled (among those treated) | Mean SBP < 140 AND mean DBP < 90 |
| Race/ethnicity (5 groups) | Categorical | NH White, NH Black, Hispanic, NH Asian, Other |

## Survey Design Variables (Pooled 3 Cycles)
| Variable | Description |
|----------|-------------|
| WTMEC2YR | Full sample 2-year MEC exam weight |
| SDMVPSU | Masked variance pseudo-PSU |
| SDMVSTRA | Masked variance pseudo-stratum |

## Notes
- When combining 3 NHANES cycles: divide WTMEC2YR by 3 for 6-year pooled weight
- Exclude pregnant women (RIDEXPRG = 1)
- Age standardization: use 2010 US Census population or the direct method per NCHS guidelines
- Mean BP: average of 2nd and 3rd readings (if available); use only available readings if fewer than 3
- Race/ethnicity: pool Mexican American and Other Hispanic into "Hispanic"; NH Asian available from 2011-2012 onward
