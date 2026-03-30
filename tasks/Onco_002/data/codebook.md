# Codebook: SEER-Medicare Linked Data (1991-2010) — CRC Staging Disparities

## Patient Demographics
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| Patient ID | Unique de-identified patient identifier | ID | - |
| Age at diagnosis | Age at cancer diagnosis | Continuous | 65-100+ (Medicare eligible) |
| Sex | Patient sex | Categorical | Male, Female |
| Race/Ethnicity | Race and ethnicity | Categorical | Non-Hispanic White, Non-Hispanic Black, Hispanic, Asian/Pacific Islander, Other/Unknown |
| Year of diagnosis | Calendar year of CRC diagnosis | Continuous | 1991-2010 |

## Tumor Characteristics
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| Primary site | Anatomic location | Categorical | Colon (proximal, distal), Rectum, Rectosigmoid junction |
| SEER historic stage | Stage at diagnosis | Categorical | Localized, Regional, Distant, Unstaged |
| Grade | Tumor differentiation | Categorical | Well (I), Moderate (II), Poor (III), Undifferentiated (IV), Unknown |

## Area-Level Socioeconomic Variables
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| County FIPS code | Federal Information Processing Standards county code | ID | 5-digit code |
| Median household income | County-level median household income from US Census | Continuous | USD (categorized into quartiles or quintiles) |
| Income area category | Grouped median household income | Categorical | Low, Medium-Low, Medium-High, High (quartiles) |
| Rural-urban designation | County urbanization level | Categorical | Metro, Urban, Rural (based on USDA rural-urban continuum codes) |

## Medicare Coverage Variables
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| Medicare Part A enrollment | Part A (hospital) coverage | Binary | Yes/No |
| Medicare Part B enrollment | Part B (physician) coverage | Binary | Yes/No |
| HMO indicator | Enrolled in Medicare HMO | Binary | Yes/No |
| Medicaid dual eligible | Dual Medicaid-Medicare enrollment | Binary | Yes/No |

## Treatment Variables
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| Surgery | Surgical treatment received | Categorical | None, Local excision, Partial colectomy, Total colectomy, Other |
| Radiation | Radiation therapy received | Binary | Yes/No |
| Chemotherapy | Chemotherapy received (from Medicare claims) | Binary | Yes/No |

## Comorbidity
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| Charlson Comorbidity Index | Comorbidity burden from Medicare claims | Continuous | 0, 1, 2, 3+ |

## Survival and Outcome Variables
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| Survival months | Months from diagnosis to death or last follow-up | Continuous | 0+ |
| Vital status | Alive or dead at last follow-up | Categorical | Alive, Dead |
| CRC-specific death | Death attributable to CRC | Binary | Yes/No |

## Derived Variables
| Variable | Description | Derivation |
|----------|-------------|------------|
| Analysis period | Screening coverage era | Period 1 (1991-1997): pre-screening; Period 2 (1998-Jun 2001): FOBT+sigmoidoscopy; Period 3 (Jul 2001-2005): colonoscopy added; Period 4 (2006-2010): high uptake |
| Late-stage indicator | Distant vs. non-distant disease | Binary: 1 if SEER historic stage = Distant, 0 otherwise |
| Income quartile | Area-level income grouping | Quartile of county median household income distribution |

## Notes
- SEER-Medicare linkage requires both SEER registry and Medicare enrollment; approximately 93% of cancer patients aged 65+ in SEER registries are matched to Medicare records
- Patients enrolled in HMO plans should be excluded from claims-based treatment analyses (incomplete claims)
- Continuous Medicare Part A+B enrollment for 12 months prior to diagnosis is typically required for comorbidity ascertainment
- The four time periods reflect changes in Medicare CRC screening reimbursement policy
- Area-level income is an ecological (aggregate) measure and does not represent individual patient income
- Cases diagnosed by DCO or autopsy only are excluded from survival analysis
