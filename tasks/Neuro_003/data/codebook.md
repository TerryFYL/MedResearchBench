# Codebook: NHANES 2007-2018 — Composite Dietary Antioxidant Index and Parkinson's Disease

## Demographics (DEMO_E through DEMO_J)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SEQN | Respondent sequence number | ID | - |
| RIDAGEYR | Age in years at screening | Continuous | 0-80 (80 = 80+) |
| RIAGENDR | Gender | Categorical | 1=Male, 2=Female |
| RIDRETH1 | Race/Hispanic origin | Categorical | 1=Mexican American, 2=Other Hispanic, 3=NH White, 4=NH Black, 5=Other/Multi-Racial |
| DMDEDUC2 | Education level (adults 20+) | Categorical | 1-5 scale |
| INDFMPIR | Family income to poverty ratio | Continuous | 0-5 |

## Dietary Intake — Total Nutrient Intakes (DR1TOT / DR2TOT files, each cycle)
| Variable | Description | Type | Units |
|----------|-------------|------|-------|
| DR1TVARA | Vitamin A intake, day 1 | Continuous | mcg RAE |
| DR1TVC | Vitamin C intake, day 1 | Continuous | mg |
| DR1TATOC | Vitamin E (alpha-tocopherol) intake, day 1 | Continuous | mg |
| DR1TCARO | Total carotenoid intake, day 1 | Continuous | mcg |
| DR1TSELE | Selenium intake, day 1 | Continuous | mcg |
| DR1TZINC | Zinc intake, day 1 | Continuous | mg |

Note: Day 2 variables use DR2 prefix. Average of day 1 and day 2 intakes is used when both available.

## Dietary Supplement Intake (DSQTOT files, each cycle)
| Variable | Description | Type | Units |
|----------|-------------|------|-------|
| DSQTVARA | Total supplemental vitamin A | Continuous | mcg RAE |
| DSQTVC | Total supplemental vitamin C | Continuous | mg |
| DSQTVB6 | Total supplemental vitamin B6 | Continuous | mg |
| DSQTSE | Total supplemental selenium | Continuous | mcg |
| DSQTZN | Total supplemental zinc | Continuous | mg |

## Composite Dietary Antioxidant Index (CDAI) — Derived
| Component | Source Variables | Standardization |
|-----------|----------------|-----------------|
| Vitamin A | DR1TVARA + DR2TVARA + DSQTVARA | (value - mean) / SD |
| Vitamin C | DR1TVC + DR2TVC + DSQTVC | (value - mean) / SD |
| Vitamin E | DR1TATOC + DR2TATOC + supplements | (value - mean) / SD |
| Carotenoids | DR1TCARO + DR2TCARO | (value - mean) / SD |
| Selenium | DR1TSELE + DR2TSELE + DSQTSE | (value - mean) / SD |
| Zinc | DR1TZINC + DR2TZINC + DSQTZN | (value - mean) / SD |

**CDAI = sum of 6 standardized values**

CDAI Tertile cutpoints: Q1 (<-1.07), Q2 (-1.07 to 1.74), Q3 (>1.74)

## Parkinson's Disease Identification (RXQ_RX files, each cycle)
| PD Medication | Generic Name | Drug Class |
|---------------|-------------|------------|
| Carbidopa | Carbidopa | DOPA decarboxylase inhibitor |
| Levodopa | Levodopa | Dopamine precursor |
| Entacapone | Entacapone | COMT inhibitor |
| Amantadine | Amantadine | NMDA antagonist/dopaminergic |
| Pramipexole | Pramipexole | Dopamine agonist |
| Bromocriptine | Bromocriptine | Dopamine agonist |

PD case = prescribed one or more of the above medications.

## Medical History and Covariates
| Variable | Source | Description | Type | Values |
|----------|--------|-------------|------|--------|
| BPQ020 | BPQ | Ever told had high blood pressure | Categorical | 1=Yes, 2=No |
| DIQ010 | DIQ | Doctor told you have diabetes | Categorical | 1=Yes, 2=No, 3=Borderline |
| LBXGLU | GLU/BIOPRO | Fasting glucose | Continuous | mg/dL |
| LBXSATSI | BIOPRO | ALT (alanine aminotransferase) | Continuous | U/L |
| LBXSCR | BIOPRO | Serum creatinine | Continuous | mg/dL |
| LBXSTR | TRIGLY/BIOPRO | Triglycerides | Continuous | mg/dL |
| LBXTC | TCHOL/BIOPRO | Total cholesterol | Continuous | mg/dL |
| BMXBMI | BMX | Body mass index | Continuous | kg/m2 |
| SMQ020 | SMQ | Smoked at least 100 cigarettes in life | Categorical | 1=Yes, 2=No |
| ALQ130 | ALQ | Avg # alcoholic drinks/day | Continuous | Number |

## Mortality Follow-Up (NHANES Linked Mortality Files)
| Variable | Description | Type |
|----------|-------------|------|
| ELIGSTAT | Eligibility status for mortality follow-up | Categorical |
| MORTSTAT | Final mortality status | Categorical (0=Alive, 1=Deceased) |
| PERMTH_INT | Person-months of follow-up from interview | Continuous |
| PERMTH_EXM | Person-months of follow-up from examination | Continuous |
| UCOD_LEADING | Underlying cause of death (leading categories) | Categorical |

Mortality data linked to National Death Index through December 31, 2019.

## Survey Design Variables
| Variable | Description | Type | Usage |
|----------|-------------|------|-------|
| WTMEC2YR | Full sample 2-year MEC examination weight | Weight | Divide by 6 for 12-year combined analysis |
| WTDR2D | Dietary day 1 and day 2 sample weight | Weight | For analyses using day 2 dietary recall |
| SDMVPSU | Masked variance pseudo-PSU | Design | Primary sampling unit |
| SDMVSTRA | Masked variance pseudo-stratum | Design | Stratum for variance estimation |

## Notes
- CDAI calculation follows methodology described by Wright et al. and Zhou et al.
- Dietary data from 24-hour recalls conducted by trained NHANES dietary interviewers
- Day 1 recall at MEC, Day 2 recall by telephone 3-10 days later
- Supplement intake from Dietary Supplements and Prescription Medications section
- PD identification via medication proxy — may miss undiagnosed or untreated PD cases
- Mortality follow-up available through December 31, 2019 (public-use linked mortality files)
- When combining 6 NHANES cycles, divide 2-year MEC weights by 6
- Cox regression uses PERMTH_EXM for time-to-event from MEC examination date
