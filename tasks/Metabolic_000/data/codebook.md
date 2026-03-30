# Codebook: NHANES 2011-2018 — HOMA-IR and Metabolic Syndrome

## Demographics (DEMO)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SEQN | Respondent sequence number | ID | - |
| RIDAGEYR | Age in years at screening | Continuous | 0-80 (80 = 80+) |
| RIAGENDR | Gender | Categorical | 1=Male, 2=Female |
| RIDRETH3 | Race/Hispanic origin with NH Asian | Categorical | 1=Mexican American, 2=Other Hispanic, 3=NH White, 4=NH Black, 6=NH Asian, 7=Other/Multi-Racial |
| DMDEDUC2 | Education level (adults 20+) | Categorical | 1=Less than 9th grade, 2=9-11th grade, 3=HS grad/GED, 4=Some college/AA, 5=College graduate+ |
| INDFMPIR | Family income to poverty ratio | Continuous | 0-5 (5 = >=5.00) |

## Fasting Glucose (GLU)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| LBXGLU | Fasting glucose (mg/dL) | Continuous | mg/dL |
| PHAFSTMN | Total length of food fast (minutes) | Continuous | minutes |
| PHAFSTHR | Total length of food fast (hours) | Continuous | hours |

## Fasting Insulin (INS)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| LBXIN | Insulin (uU/mL) | Continuous | uU/mL |
| LBDINSI | Insulin (pmol/L) | Continuous | pmol/L |

## Lipid Panel — Triglycerides and HDL (TRIGLY, HDL)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| LBXTR | Triglycerides (mg/dL) | Continuous | mg/dL |
| LBDTRSI | Triglycerides (mmol/L) | Continuous | mmol/L |
| LBDHDD | Direct HDL-cholesterol (mg/dL) | Continuous | mg/dL |

## Blood Pressure (BPX)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| BPXSY1-3 | Systolic BP, readings 1-3 (mmHg) | Continuous | mmHg |
| BPXDI1-3 | Diastolic BP, readings 1-3 (mmHg) | Continuous | mmHg |

## Body Measures (BMX)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| BMXBMI | Body Mass Index (kg/m^2) | Continuous | kg/m^2 |
| BMXWAIST | Waist circumference (cm) | Continuous | cm |
| BMXWT | Weight (kg) | Continuous | kg |
| BMXHT | Standing height (cm) | Continuous | cm |

## Medical Conditions (MCQ) and Diabetes (DIQ)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| DIQ010 | Doctor told you have diabetes | Categorical | 1=Yes, 2=No, 3=Borderline |
| DIQ050 | Taking insulin now | Categorical | 1=Yes, 2=No |
| DIQ070 | Taking diabetic pills to lower blood sugar | Categorical | 1=Yes, 2=No |

## Blood Pressure Questionnaire (BPQ)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| BPQ020 | Ever told you had high blood pressure | Categorical | 1=Yes, 2=No |
| BPQ040A | Taking prescription for hypertension | Categorical | 1=Yes, 2=No |
| BPQ050A | Now taking prescribed medicine for HBP | Categorical | 1=Yes, 2=No |
| BPQ080 | Doctor told you have high cholesterol | Categorical | 1=Yes, 2=No |
| BPQ090D | Told to take prescribed cholesterol medicine | Categorical | 1=Yes, 2=No |

## Derived Variables
| Variable | Description | Derivation |
|----------|-------------|------------|
| HOMA-IR | Homeostasis model assessment of insulin resistance | (LBXGLU × LBXIN) / 405 |
| MetS | Metabolic syndrome (binary) | ≥3 of 5 ATP III/AHA-NHLBI criteria (see below) |
| Mean SBP | Average systolic BP | Mean of available readings |
| Mean DBP | Average diastolic BP | Mean of available readings |
| BMI category | Weight status | <25=Normal, 25-29.9=Overweight, ≥30=Obese |

## Metabolic Syndrome Criteria (Harmonized ATP III/AHA-NHLBI)
| Component | Threshold |
|-----------|-----------|
| Elevated waist circumference | ≥102 cm (men), ≥88 cm (women) |
| Elevated triglycerides | ≥150 mg/dL or on lipid-lowering medication |
| Reduced HDL-C | <40 mg/dL (men), <50 mg/dL (women) or on lipid-lowering medication |
| Elevated blood pressure | ≥130/85 mmHg or on antihypertensive medication |
| Elevated fasting glucose | ≥100 mg/dL or on glucose-lowering medication |

## Survey Design Variables
| Variable | Description |
|----------|-------------|
| WTMEC2YR | Full sample 2-year MEC exam weight |
| WTSAF2YR | Fasting subsample 2-year weight |
| SDMVPSU | Masked variance pseudo-PSU |
| SDMVSTRA | Masked variance pseudo-stratum |

## Notes
- Use WTSAF2YR (fasting subsample weights) for all analyses involving glucose, insulin, triglycerides, or HOMA-IR
- When pooling 4 NHANES cycles, divide 2-year weights by 4 to create combined weights
- Fasting subsample includes participants who fasted 8-24 hours before morning blood draw
- Exclude participants with diagnosed diabetes (DIQ010=1) or taking insulin (DIQ050=1) for HOMA-IR analyses if the goal is to identify undiagnosed metabolic risk
- Blood pressure is typically averaged across available readings; exclude first reading if 3 readings available
- Complex survey design requires Taylor series linearization for variance estimation
