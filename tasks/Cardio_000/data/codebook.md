# Codebook: NHANES 2017-2018 — Dietary Sodium, Potassium, and Hypertension

## Demographics (DEMO_J)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SEQN | Respondent sequence number | ID | - |
| RIDAGEYR | Age in years at screening | Continuous | 0-80 (80 = 80+) |
| RIAGENDR | Gender | Categorical | 1=Male, 2=Female |
| RIDRETH3 | Race/Hispanic origin with NH Asian | Categorical | 1=Mexican American, 2=Other Hispanic, 3=NH White, 4=NH Black, 6=NH Asian, 7=Other/Multi-Racial |
| DMDEDUC2 | Education level (adults 20+) | Categorical | 1=Less than 9th grade, 2=9-11th grade, 3=High school grad/GED, 4=Some college/AA, 5=College graduate+ |
| DMDMARTL | Marital status | Categorical | 1=Married, 2=Widowed, 3=Divorced, 4=Separated, 5=Never married, 6=Living with partner |
| INDFMPIR | Family income to poverty ratio | Continuous | 0-5 (5 = >=5.00) |

## Dietary Intake — Total Nutrient Intakes, Day 1 (DR1TOT_J)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| DR1TSODI | Sodium (mg) | Continuous | mg/day |
| DR1TPOTA | Potassium (mg) | Continuous | mg/day |
| DR1TKCAL | Energy (kcal) | Continuous | kcal/day |
| DR1TFIBE | Dietary fiber (g) | Continuous | g/day |
| DR1TCHOL | Cholesterol (mg) | Continuous | mg/day |
| DR1DRSTZ | Dietary recall status | Categorical | 1=Reliable and met minimum criteria, 2=Not reliable, 4=Not done, 5=Incomplete |

## Blood Pressure (BPX_J)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| BPXOSY1 | Systolic BP, 1st reading (mmHg) | Continuous | mmHg |
| BPXODI1 | Diastolic BP, 1st reading (mmHg) | Continuous | mmHg |
| BPXOSY2 | Systolic BP, 2nd reading (mmHg) | Continuous | mmHg |
| BPXODI2 | Diastolic BP, 2nd reading (mmHg) | Continuous | mmHg |
| BPXOSY3 | Systolic BP, 3rd reading (mmHg) | Continuous | mmHg |
| BPXODI3 | Diastolic BP, 3rd reading (mmHg) | Continuous | mmHg |

## Questionnaire — Blood Pressure & Cholesterol (BPQ_J)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| BPQ020 | Ever told you had high blood pressure | Categorical | 1=Yes, 2=No, 9=Don't know |
| BPQ040A | Taking prescription for hypertension | Categorical | 1=Yes, 2=No, 9=Don't know |
| BPQ050A | Now taking prescribed medicine for HBP | Categorical | 1=Yes, 2=No, 9=Don't know |

## Physical Activity (PAQ_J)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| PAQ605 | Vigorous work activity | Categorical | 1=Yes, 2=No |
| PAQ620 | Moderate work activity | Categorical | 1=Yes, 2=No |
| PAQ650 | Vigorous recreational activity | Categorical | 1=Yes, 2=No |
| PAQ665 | Moderate recreational activity | Categorical | 1=Yes, 2=No |

## Smoking & Alcohol (SMQ_J, ALQ_J)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SMQ020 | Smoked at least 100 cigarettes in life | Categorical | 1=Yes, 2=No |
| SMQ040 | Do you now smoke cigarettes | Categorical | 1=Every day, 2=Some days, 3=Not at all |
| ALQ130 | Average # alcoholic drinks/day past 12 months | Continuous | drinks/day |

## Body Measures (BMX_J)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| BMXBMI | Body Mass Index (kg/m^2) | Continuous | kg/m^2 |
| BMXWAIST | Waist circumference (cm) | Continuous | cm |

## Derived Variables
| Variable | Description | Derivation |
|----------|-------------|------------|
| Hypertension (outcome) | Binary hypertension status | 1 if: self-reported diagnosis (BPQ020=1) OR taking antihypertensive medication (BPQ050A=1) OR mean SBP >= 140 OR mean DBP >= 90 |
| Na/K ratio | Sodium-to-potassium intake ratio | DR1TSODI / DR1TPOTA |
| Mean SBP | Average systolic BP | Mean of available BPXOSY1-3 readings |
| Mean DBP | Average diastolic BP | Mean of available BPXODI1-3 readings |

## Survey Design Variables
| Variable | Description |
|----------|-------------|
| WTMEC2YR | Full sample 2-year MEC exam weight |
| SDMVPSU | Masked variance pseudo-PSU |
| SDMVSTRA | Masked variance pseudo-stratum |
| WTDRD1 | Dietary day one sample weight |

## Notes
- Missing values: coded as NaN or blank
- Survey weights MUST be applied for population-level inference
- Use WTDRD1 (dietary weights) when analyzing dietary intake variables
- Use WTMEC2YR (MEC weights) when analyzing examination data without dietary variables
- Complex survey design requires Taylor series linearization (proc surveymeans/surveylogistic in SAS, or svydesign in R)
- Dietary intake is from a single 24-hour recall (Day 1), subject to within-person variability
- Blood pressure is the average of up to 3 readings; exclude first reading if 3 readings available per NHANES analytic guidelines
