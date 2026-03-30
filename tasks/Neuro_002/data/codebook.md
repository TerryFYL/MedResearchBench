# Codebook: NHANES 2011-2014 — Blood Heavy Metals and Cognitive Function

## Demographics (DEMO_G / DEMO_H)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SEQN | Respondent sequence number | ID | - |
| RIDAGEYR | Age in years at screening | Continuous | 0-80 (80 = 80+) |
| RIAGENDR | Gender | Categorical | 1=Male, 2=Female |
| RIDRETH1 | Race/Hispanic origin | Categorical | 1=Mexican American, 2=Other Hispanic, 3=NH White, 4=NH Black, 5=Other/Multi-Racial |
| DMDEDUC2 | Education level (adults 20+) | Categorical | 1=Less than 9th grade, 2=9-11th grade, 3=High school grad/GED, 4=Some college/AA, 5=College graduate+ |
| INDFMPIR | Family income to poverty ratio | Continuous | 0-5 (5 = >=5.00) |

## Blood Metals — Lead, Cadmium, Mercury, Selenium, Manganese (PBCD_G / PBCD_H)
| Variable | Description | Type | Units | LOD |
|----------|-------------|------|-------|-----|
| LBXBPB | Blood lead | Continuous | ug/dL | 0.25 |
| LBXBCD | Blood cadmium | Continuous | ug/L | 0.10 |
| LBXTHG | Blood total mercury | Continuous | ug/L | 0.28 |
| LBXBSE | Blood selenium | Continuous | ug/L | 24.48 |
| LBXBMN | Blood manganese | Continuous | ug/L | 0.99 |

## Serum Biochemistry — Iron (BIOPRO_G / BIOPRO_H)
| Variable | Description | Type | Units |
|----------|-------------|------|-------|
| LBXSIR | Serum iron | Continuous | ug/dL |
| LBXSTF | Serum transferrin | Continuous | mg/dL |
| LBXSFE | Serum ferritin | Continuous | ng/mL |

## Cognitive Functioning (CFQ_G / CFQ_H)
| Variable | Description | Type | Range |
|----------|-------------|------|-------|
| CFDAST | DSST score (# correct in 120 sec) | Continuous | 0-133 |
| CFDDS | Animal Fluency Test score | Continuous | 0-40+ |
| CFDCST | CERAD Word List — total score (3 trials) | Continuous | 0-30 |
| CFDCSR | CERAD Word List — delayed recall score | Continuous | 0-10 |

### Cognitive Test Descriptions
- **CERAD Word List Learning**: Three consecutive learning trials of 10 unrelated words read aloud. Score = total words recalled across 3 trials (max 30). Tests immediate learning/memory.
- **CERAD Word List Recall**: Delayed recall of the 10 words after a distractor task. Score = words recalled (max 10). Tests delayed memory.
- **Animal Fluency Test (AFT)**: Name as many animals as possible in 60 seconds. Tests verbal fluency and executive function.
- **Digit Symbol Substitution Test (DSST)**: Match symbols to numbers using a key; score = correct matches in 120 seconds (max 133). Tests processing speed, sustained attention, and working memory.

### Low Cognitive Performance Definition
Low cognitive performance on each test is defined as scoring **below the 25th percentile** of the test score distribution in the study population.

## Medical History and Health Behaviors
| Variable | Source | Description | Type | Values |
|----------|--------|-------------|------|--------|
| DIQ010 | DIQ_G/H | Doctor told you have diabetes | Categorical | 1=Yes, 2=No, 3=Borderline |
| BPQ020 | BPQ_G/H | Ever told you had high blood pressure | Categorical | 1=Yes, 2=No |
| SMQ020 | SMQ_G/H | Smoked at least 100 cigarettes in life | Categorical | 1=Yes, 2=No |
| SMQ040 | SMQ_G/H | Do you now smoke cigarettes | Categorical | 1=Every day, 2=Some days, 3=Not at all |
| ALQ130 | ALQ_G/H | Avg # alcoholic drinks/day past 12 months | Continuous | Number/day |
| BMXBMI | BMX_G/H | Body mass index (kg/m2) | Continuous | kg/m2 |
| PAQ605 | PAQ_G/H | Vigorous recreational activities | Categorical | 1=Yes, 2=No |
| PAQ620 | PAQ_G/H | Moderate recreational activities | Categorical | 1=Yes, 2=No |

## Derived Smoking Status
| Category | Criteria |
|----------|----------|
| Never smoker | SMQ020 = 2 (No) |
| Former smoker | SMQ020 = 1 (Yes) AND SMQ040 = 3 (Not at all) |
| Current smoker | SMQ020 = 1 (Yes) AND SMQ040 = 1 or 2 |

## Survey Design Variables
| Variable | Description | Type | Usage |
|----------|-------------|------|-------|
| WTMEC2YR | Full sample 2-year MEC examination weight | Weight | Divide by 2 for 4-year combined analysis |
| SDMVPSU | Masked variance pseudo-PSU | Design | Primary sampling unit |
| SDMVSTRA | Masked variance pseudo-stratum | Design | Stratum for variance estimation |

## Notes
- Blood metals measured by inductively coupled plasma mass spectrometry (ICP-MS) at CDC Division of Laboratory Sciences
- Cognitive function tests administered in NHANES only to participants aged 60+ years (2011-2014 cycles)
- CERAD, AFT, and DSST administered by trained interviewers in English or Spanish at Mobile Examination Center
- When combining 2 NHANES cycles, divide 2-year weights by 2 for 4-year combined analysis
- Values below LOD: use LOD/sqrt(2) for substitution in continuous analyses
- Serum iron from standard biochemistry profile; blood metals from separate heavy metals panel
