# Codebook: NHANES 2009-2016 — Sleep Duration and Depression

## Demographics (DEMO_F/G/H/I)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SEQN | Respondent sequence number | ID | - |
| RIDAGEYR | Age in years at screening | Continuous | 0-80 (80 = 80+) |
| RIAGENDR | Gender | Categorical | 1=Male, 2=Female |
| RIDRETH1 | Race/Hispanic origin | Categorical | 1=Mexican American, 2=Other Hispanic, 3=NH White, 4=NH Black, 5=Other/Multi-Racial |
| RIDRETH3 | Race/Hispanic origin with NH Asian | Categorical | 1=Mexican American, 2=Other Hispanic, 3=NH White, 4=NH Black, 6=NH Asian, 7=Other/Multi-Racial |
| DMDEDUC2 | Education level (adults 20+) | Categorical | 1=Less than 9th grade, 2=9-11th grade, 3=High school grad/GED, 4=Some college/AA, 5=College graduate+ |
| DMDMARTL | Marital status | Categorical | 1=Married, 2=Widowed, 3=Divorced, 4=Separated, 5=Never married, 6=Living with partner |
| INDFMPIR | Family income to poverty ratio | Continuous | 0-5 (5 = >=5.00) |

## Depression Screener — PHQ-9 (DPQ_F/G/H/I)
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

## Sleep Questionnaire (SLQ_F/G/H/I)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SLD012 | Sleep hours — weekdays or workdays | Continuous | Hours (2-14, typically integer or half-hour) |
| SLQ050 | Ever told doctor had trouble sleeping | Categorical | 1=Yes, 2=No |
| SLQ060 | How often feel overly sleepy during day | Categorical | 0=Never, 1=Rarely (1/month), 2=Sometimes (2-4/month), 3=Often (5-15/month), 4=Almost always (16-30/month) |

## Body Measures (BMX_F/G/H/I)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| BMXBMI | Body Mass Index (kg/m^2) | Continuous | kg/m^2 |
| BMXWAIST | Waist circumference (cm) | Continuous | cm |

## Physical Activity (PAQ_F/G/H/I)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| PAQ605 | Vigorous work activity | Categorical | 1=Yes, 2=No |
| PAQ620 | Moderate work activity | Categorical | 1=Yes, 2=No |
| PAQ650 | Vigorous recreational activity | Categorical | 1=Yes, 2=No |
| PAQ665 | Moderate recreational activity | Categorical | 1=Yes, 2=No |

## Smoking & Alcohol (SMQ_F/G/H/I, ALQ_F/G/H/I)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SMQ020 | Smoked at least 100 cigarettes in life | Categorical | 1=Yes, 2=No |
| SMQ040 | Do you now smoke cigarettes | Categorical | 1=Every day, 2=Some days, 3=Not at all |
| ALQ130 | Average # alcoholic drinks/day past 12 months | Continuous | drinks/day |

## Medical Conditions (MCQ_F/G/H/I)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| MCQ220 | Ever told you had cancer | Categorical | 1=Yes, 2=No |
| MCQ160B | Ever told had congestive heart failure | Categorical | 1=Yes, 2=No |
| MCQ160C | Ever told had coronary heart disease | Categorical | 1=Yes, 2=No |
| MCQ160F | Ever told you had a stroke | Categorical | 1=Yes, 2=No |

## Derived Variables
| Variable | Description | Derivation |
|----------|-------------|------------|
| PHQ-9 Total Score | Sum of DPQ010 through DPQ090 | Range 0-27 |
| Depression (outcome) | Binary depression status | 1 if PHQ-9 total >= 10 |
| Depression Severity | Severity categories | None (0-4), Mild (5-9), Moderate (10-14), Moderately Severe (15-19), Severe (20-27) |
| Sleep Duration Category | Categorical sleep | <6h, 6h, 7h, 8h (reference), 9h, >=10h |
| Chronic Disease Count | Comorbidity burden | Sum of self-reported chronic conditions |

## Survey Design Variables
| Variable | Description |
|----------|-------------|
| WTMEC2YR | Full sample 2-year MEC exam weight |
| SDMVPSU | Masked variance pseudo-PSU |
| SDMVSTRA | Masked variance pseudo-stratum |

## Notes
- PHQ-9 is administered to all participants aged 12+ in the Mobile Examination Center (MEC)
- Sleep duration (SLD012) refers to self-reported usual hours of sleep on weekdays/workdays
- When combining 4 NHANES cycles (2009-2016), use adjusted weights: WTMEC2YR / 4
- Items DPQ010-DPQ090: missing items coded 7=Refused, 9=Don't know — exclude from total score computation
- Complex survey design requires Taylor series linearization for variance estimation
- Caution: DPQ030 (trouble sleeping/sleeping too much) is both a PHQ-9 item and related to the exposure — some studies exclude it in sensitivity analysis to avoid circular reasoning
