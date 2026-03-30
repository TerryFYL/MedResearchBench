# Codebook: NHANES 2005-2016 — Depression Prevalence Trends

## Demographics (DEMO_D/E/F/G/H/I)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SEQN | Respondent sequence number | ID | - |
| SDDSRVYR | Data release cycle | Categorical | 4=2005-2006, 5=2007-2008, 6=2009-2010, 7=2011-2012, 8=2013-2014, 9=2015-2016 |
| RIDAGEYR | Age in years at screening | Continuous | 0-80 (80 = 80+) |
| RIAGENDR | Gender | Categorical | 1=Male, 2=Female |
| RIDRETH1 | Race/Hispanic origin | Categorical | 1=Mexican American, 2=Other Hispanic, 3=NH White, 4=NH Black, 5=Other/Multi-Racial |
| DMDEDUC2 | Education level (adults 20+) | Categorical | 1=Less than 9th grade, 2=9-11th grade, 3=High school grad/GED, 4=Some college/AA, 5=College graduate+ |
| DMDMARTL | Marital status | Categorical | 1=Married, 2=Widowed, 3=Divorced, 4=Separated, 5=Never married, 6=Living with partner |
| INDFMPIR | Family income to poverty ratio | Continuous | 0-5 (5 = >=5.00) |

## Depression Screener — PHQ-9 (DPQ_D/E/F/G/H/I)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| DPQ010 | Little interest or pleasure in doing things | Ordinal | 0=Not at all, 1=Several days, 2=More than half the days, 3=Nearly every day |
| DPQ020 | Feeling down, depressed, or hopeless | Ordinal | Same as above |
| DPQ030 | Trouble sleeping or sleeping too much | Ordinal | Same as above |
| DPQ040 | Feeling tired or having little energy | Ordinal | Same as above |
| DPQ050 | Poor appetite or overeating | Ordinal | Same as above |
| DPQ060 | Feeling bad about yourself | Ordinal | Same as above |
| DPQ070 | Trouble concentrating on things | Ordinal | Same as above |
| DPQ080 | Moving or speaking slowly/being fidgety | Ordinal | Same as above |
| DPQ090 | Thoughts of being better off dead | Ordinal | Same as above |

## Blood Pressure & Diabetes Questionnaire (BPQ_D-I, DIQ_D-I)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| BPQ020 | Ever told you had high blood pressure | Categorical | 1=Yes, 2=No |
| DIQ010 | Doctor told you have diabetes | Categorical | 1=Yes, 2=No, 3=Borderline |

## Physical Activity (PAQ_D/E/F/G/H/I)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| PAQ605 | Vigorous work activity | Categorical | 1=Yes, 2=No |
| PAQ650 | Vigorous recreational activity | Categorical | 1=Yes, 2=No |

## Smoking & Alcohol (SMQ_D-I, ALQ_D-I)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SMQ020 | Smoked at least 100 cigarettes in life | Categorical | 1=Yes, 2=No |
| SMQ040 | Do you now smoke cigarettes | Categorical | 1=Every day, 2=Some days, 3=Not at all |
| ALQ130 | Average # alcoholic drinks/day past 12 months | Continuous | drinks/day |

## Body Measures (BMX_D/E/F/G/H/I)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| BMXBMI | Body Mass Index (kg/m^2) | Continuous | kg/m^2 |

## Derived Variables
| Variable | Description | Derivation |
|----------|-------------|------------|
| PHQ-9 Total Score | Sum of DPQ010 through DPQ090 | Range 0-27 |
| Depression (any) | Binary depression status | 1 if PHQ-9 total >= 10 |
| Depression Severity | Severity categories | None (0-4), Mild (5-9), Moderate (10-14), Moderately Severe (15-19), Severe (20-27) |
| Survey Cycle | NHANES cycle indicator | Derived from SDDSRVYR for trend analysis |
| Age Group | Age categories | 20-39, 40-64, 65+ |
| Income Group | Income categories | Low (<1.0 PIR), Middle (1.0-3.0 PIR), High (>3.0 PIR) |
| Smoking Status | 3-level | Never, Former, Current |

## Survey Design Variables
| Variable | Description |
|----------|-------------|
| WTMEC2YR | Full sample 2-year MEC exam weight |
| SDMVPSU | Masked variance pseudo-PSU |
| SDMVSTRA | Masked variance pseudo-stratum |

## Notes
- PHQ-9 was first administered in NHANES starting with the 2005-2006 cycle (DPQ_D)
- PHQ-9 is administered to participants aged 12+ in the MEC; this analysis restricts to adults 20+
- For trend analysis, each cycle uses its own 2-year weight (WTMEC2YR) — do NOT divide by 6
- When computing prevalence for each cycle separately, use the cycle-specific WTMEC2YR directly
- Standard severity cutoffs: None (0-4), Mild (5-9), Moderate (10-14), Mod. Severe (15-19), Severe (20-27)
- P-for-trend is computed by modeling survey cycle as a continuous ordinal variable (1-6) in weighted logistic regression
- Note: NHANES 2005-2006 through 2015-2016 spans the 2008-2009 Great Recession; economic context may influence depression trends
- Race/ethnicity variable RIDRETH1 is available across all 6 cycles; RIDRETH3 (with NH Asian) is only available from 2011-2012 onward
