# Codebook: NHANES 2003-2018 — HPV Vaccine Effectiveness and Genotype Prevalence

## Demographics (DEMO)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SEQN | Respondent sequence number | ID | - |
| RIDAGEYR | Age in years at screening | Continuous | 14-24 (study range) |
| RIAGENDR | Gender | Categorical | 1=Male, 2=Female |
| RIDRETH1 | Race/Hispanic origin | Categorical | 1=Mexican American, 2=Other Hispanic, 3=NH White, 4=NH Black, 5=Other/Multi-Racial |
| DMDEDUC2 | Education level (adults 20+) | Categorical | 1-5 scale |
| DMDEDUC3 | Education level (youth 6-19) | Categorical | 0-66 (grade completed) |
| INDFMPIR | Family income to poverty ratio | Continuous | 0-5 |

## HPV DNA — Vaginal Swab (HPVSWR / varies by cycle)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| ORXHPV06 | HPV type 6 DNA result | Categorical | 1=Positive, 2=Negative |
| ORXHPV11 | HPV type 11 DNA result | Categorical | 1=Positive, 2=Negative |
| ORXHPV16 | HPV type 16 DNA result | Categorical | 1=Positive, 2=Negative |
| ORXHPV18 | HPV type 18 DNA result | Categorical | 1=Positive, 2=Negative |
| ORXHPV31 | HPV type 31 DNA result | Categorical | 1=Positive, 2=Negative |
| ORXHPV33 | HPV type 33 DNA result | Categorical | 1=Positive, 2=Negative |
| ORXHPV45 | HPV type 45 DNA result | Categorical | 1=Positive, 2=Negative |
| ORXHPV52 | HPV type 52 DNA result | Categorical | 1=Positive, 2=Negative |
| ORXHPV58 | HPV type 58 DNA result | Categorical | 1=Positive, 2=Negative |

## HPV DNA — Penile Swab (HPVP_H / varies by cycle, males only, 2013+)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| ORXHPV06 | HPV type 6 DNA result (penile) | Categorical | 1=Positive, 2=Negative |
| ORXHPV11 | HPV type 11 DNA result (penile) | Categorical | 1=Positive, 2=Negative |
| ORXHPV16 | HPV type 16 DNA result (penile) | Categorical | 1=Positive, 2=Negative |
| ORXHPV18 | HPV type 18 DNA result (penile) | Categorical | 1=Positive, 2=Negative |

## Sexual Behavior Questionnaire (SXQ)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| SXQ021 | Ever had vaginal sex | Categorical | 1=Yes, 2=No |
| SXQ101 | Number of male sexual partners (lifetime, females) | Continuous | count |
| SXQ450 | Age at first sexual intercourse | Continuous | years |
| SXD171 | Number of sexual partners (past 12 months) | Continuous | count |

## Immunization Questionnaire (IMQ, 2007+ cycles)
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| IMQ060 | Received HPV vaccine (females, 2007+) | Categorical | 1=Yes, 2=No, 9=Don't know |
| IMQ070 | Received HPV vaccine (males, 2011+) | Categorical | 1=Yes, 2=No, 9=Don't know |
| IMQ090 | Age at first HPV vaccine dose | Continuous | years |

## Derived Variables
| Variable | Description | Derivation |
|----------|-------------|------------|
| 4vHPV positive | Any quadrivalent vaccine-type infection | Positive for HPV 6, 11, 16, or 18 |
| 9vHPV positive | Any nonavalent vaccine-type infection | Positive for HPV 6, 11, 16, 18, 31, 33, 45, 52, or 58 |
| Non-4vHPV positive | Any non-quadrivalent-type infection | Positive for any detected HPV type NOT in 4vHPV |
| Sexually experienced | Eligible for analysis | Reported ever having vaginal, anal, or oral sex |
| Vaccinated | Received >= 1 HPV vaccine dose | IMQ060=1 (females) or IMQ070=1 (males) |
| Study era | Temporal grouping | Prevaccine (2003-2006), Vaccine Era 1 (2007-2010), Era 2 (2011-2014), Era 3 (2015-2018) |
| Vaccine impact | Population-level prevalence reduction | (Prevalence_prevaccine - Prevalence_era) / Prevalence_prevaccine × 100% |
| Vaccine effectiveness | Individual-level protection | 1 - (Prevalence_vaccinated / Prevalence_unvaccinated) within each era |

## Survey Design Variables
| Variable | Description |
|----------|-------------|
| WTMEC2YR | Full sample 2-year MEC exam weight |
| SDMVPSU | Masked variance pseudo-PSU |
| SDMVSTRA | Masked variance pseudo-stratum |

## Notes
- Eight NHANES cycles: 2003-2004 through 2017-2018
- HPV vaccine (Gardasil, quadrivalent) licensed June 2006; female recommendation June 2006, male recommendation October 2011
- Prevaccine era (2003-2006) predates vaccine availability and serves as the baseline comparator
- HPV vaccination questions added to NHANES starting 2007-2008 cycle
- Male genital HPV testing added starting 2013-2014 cycle
- Roche Linear Array HPV Genotyping Test detects 37 HPV types
- Self-collected swabs: cervicovaginal (females 14-59) and penile (males 14-59, 2013+)
- Complex survey design requires Taylor series linearization for variance estimation
- For trend analyses combining cycles, adjust 2-year weights by dividing by number of cycles
