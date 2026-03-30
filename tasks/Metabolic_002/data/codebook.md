# Codebook: NHANES III (1988-1994) — Thyroid Function and Mortality

## Demographics
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SEQN | Respondent sequence number | ID | - |
| HSAGEIR | Age in years at interview | Continuous | 2 months - 90 years |
| HSSEX | Sex | Categorical | 1=Male, 2=Female |
| DMARETHN | Race/ethnicity | Categorical | 1=Non-Hispanic White, 2=Non-Hispanic Black, 3=Mexican American, 4=Other |
| DMAEDUC | Education level | Categorical | 1=Less than HS, 2=HS diploma, 3=More than HS |
| DMPPIR | Poverty-income ratio | Continuous | 0-16 |

## Thyroid Function Panel
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| TSPH | Serum TSH (mIU/L) | Continuous | mIU/L |
| T4PH | Total thyroxine, TT4 (μg/dL) | Continuous | μg/dL |
| ATPPH | Thyroid peroxidase antibodies (TPO-Ab) | Continuous | IU/mL; positive >0.5 IU/mL |

### Euthyroid Definition
- TSH within 0.39-4.60 mIU/L
- Normal TT4 range (4.5-12.5 μg/dL)
- TSH tertile boundaries (from study): Low-normal (0.39-1.29), Medium-normal (1.30-2.09), High-normal (2.10-4.60 mIU/L)

## Diabetes Identification
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| HAD1 | Doctor told you have diabetes | Categorical | 1=Yes, 2=No |
| HAD5S | Currently taking insulin | Categorical | 1=Yes, 2=No |
| HAD10 | Currently taking diabetes pills | Categorical | 1=Yes, 2=No |
| GHP | Glycated hemoglobin (HbA1c, %) | Continuous | % |
| G1P | Fasting plasma glucose (mg/dL) | Continuous | mg/dL |
| G2P | 2-hour OGTT glucose (mg/dL) | Continuous | mg/dL |

### Diabetes Case Definition
Diabetes identified by any of: self-reported physician diagnosis, fasting glucose ≥126 mg/dL, 2h OGTT glucose ≥200 mg/dL, HbA1c ≥6.5%, or current use of diabetes medication.

## Urinary Iodine
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| UIP | Urinary iodine concentration (μg/L) | Continuous | μg/L |

## Anthropometry and Examination
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| BMPBMI | Body mass index (kg/m²) | Continuous | kg/m² |
| BMPWAIST | Waist circumference (cm) | Continuous | cm |
| BMPWT | Body weight (kg) | Continuous | kg |
| BMPHT | Standing height (cm) | Continuous | cm |
| PEPMNK1R | Mean systolic BP (mmHg) | Continuous | mmHg |
| PEPMNK5R | Mean diastolic BP (mmHg) | Continuous | mmHg |

## Lifestyle and Behavioral Variables
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| HAR1 | Smoking status | Categorical | 1=Current, 2=Former, 3=Never |
| ALD100 | Had ≥12 alcoholic drinks in lifetime | Categorical | 1=Yes, 2=No |
| HAT1S-HAT10S | Physical activity frequency | Categorical | Varies by activity type |

## Comorbidities
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| HAC1E | Doctor told you have CHF | Categorical | 1=Yes, 2=No |
| HAC1F | Doctor told you have heart attack | Categorical | 1=Yes, 2=No |
| HAC1G | Doctor told you have stroke | Categorical | 1=Yes, 2=No |
| HAC1A | Doctor told you have high BP | Categorical | 1=Yes, 2=No |
| TCP | Total cholesterol (mg/dL) | Continuous | mg/dL |
| HDP | HDL cholesterol (mg/dL) | Continuous | mg/dL |
| CRP | C-reactive protein (mg/dL) | Continuous | mg/dL |

## Mortality Linkage (NDI Public-Use File)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| MORTSTAT | Final mortality status | Categorical | 0=Assumed alive, 1=Assumed deceased |
| UCOD_LEADING | Underlying cause of death (ICD-10) | Categorical | ICD-10 leading cause categories |
| PERMTH_INT | Person-months of follow-up from interview | Continuous | months |
| PERMTH_EXM | Person-months of follow-up from examination | Continuous | months |

### Mortality Endpoints
- **All-cause mortality**: MORTSTAT = 1
- **Cardiovascular mortality**: UCOD_LEADING = "Diseases of heart" (ICD-10 I00-I09, I11, I13, I20-I51)
- **Follow-up period**: Baseline interview (1988-1994) through December 31, 2019

## Survey Design Variables
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| WTPFEX6 | Examined sample final weight (6-year) | Continuous | Survey weight |
| SDPSTRA6 | Pseudo-stratum for variance estimation | Categorical | Stratum ID |
| SDPPSU6 | Pseudo-PSU for variance estimation | Categorical | PSU ID |

### Notes
- NHANES III used a complex multistage probability sampling design
- For mortality analyses, use MEC examined sample weights (WTPFEX6)
- NHANES III did not measure free T4 (FT4); total T4 (TT4) is used as a proxy
- Thyroid function measured in examinees aged 12+ years; diabetes analyses restricted to adults ≥20 years
