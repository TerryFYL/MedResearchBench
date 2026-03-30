# Codebook: NHANES 1999-2016 — Hepatitis B Seroprevalence and Vaccination Coverage

## Demographics (DEMO)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SEQN | Respondent sequence number | ID | - |
| RIDAGEYR | Age in years at screening | Continuous | 0-85 |
| RIAGENDR | Gender | Categorical | 1=Male, 2=Female |
| RIDRETH1 | Race/Hispanic origin | Categorical | 1=Mexican American, 2=Other Hispanic, 3=NH White, 4=NH Black, 5=Other Race/Multi-Racial |
| DMDBORN | Country of birth | Categorical | 1=Born in 50 US states or DC, 2=Others (varies by cycle) |
| INDFMPIR | Family income to poverty ratio | Continuous | 0-5 |

## Hepatitis B Serology (HEPB_D / HEPBD_E ... varies by cycle)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| LBXHBS | Hepatitis B surface antibody (anti-HBs) | Categorical | 1=Positive, 2=Negative |
| LBDHBG | Hepatitis B surface antigen (HBsAg) | Categorical | 1=Positive, 2=Negative |
| LBDHD | Hepatitis B core antibody (anti-HBc) | Categorical | 1=Positive, 2=Negative |

## Quantitative Hepatitis B Antibody (select cycles)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| LBXHBS | Anti-HBs titer | Continuous | mIU/mL (immunity threshold >= 10 mIU/mL) |

## Immunization Questionnaire (IMQ)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| IMQ011 | Received hepatitis B vaccine (3 doses) | Categorical | 1=Yes, 2=No, 3=At least 3 doses, 9=Don't know |
| IMQ020 | Received hepatitis B vaccine | Categorical | 1=Yes, 2=No, 9=Don't know |

## Derived Variables
| Variable | Description | Derivation |
|----------|-------------|------------|
| Vaccination status | Complete HBV vaccination | Self/parent-reported receipt of >= 3 doses hepatitis B vaccine |
| Vaccine-induced immunity | Serologic evidence of immunity | anti-HBs >= 10 mIU/mL AND anti-HBc negative (excludes natural immunity from past infection) |
| Past/present HBV infection | Evidence of prior or current infection | anti-HBc positive (regardless of HBsAg status) |
| Chronic HBV infection | Chronic carrier status | HBsAg positive |
| Birth cohort | Birth year grouping | Derived from RIDAGEYR and survey cycle year |
| Survey period | Grouped NHANES cycles | 1999-2002, 2003-2006, 2007-2010, 2011-2016 |

## Survey Design Variables
| Variable | Description |
|----------|-------------|
| WTMEC2YR | Full sample 2-year MEC exam weight |
| SDMVPSU | Masked variance pseudo-PSU |
| SDMVSTRA | Masked variance pseudo-stratum |

## Notes
- Nine NHANES cycles: 1999-2000 through 2015-2016
- Cycle suffixes: no suffix (1999-2000), _B (2001-2002), _C (2003-2004), _D (2005-2006), _E (2007-2008), _F (2009-2010), _G (2011-2012), _H (2013-2014), _I (2015-2016)
- Hepatitis B serology module names vary across cycles (e.g., HEPB_D, HEPBD_E, HEPB_G)
- Anti-HBs threshold of 10 mIU/mL is the standard seroprotective level per CDC/ACIP guidelines
- Study restricted to US-born persons (DMDBORN = 1) to focus on vaccination program impact
- Children aged 2-18 years are the target population
- For multi-cycle analyses, combine 2-year weights appropriately (divide by number of cycles combined)
- Complex survey design requires Taylor series linearization for variance estimation
