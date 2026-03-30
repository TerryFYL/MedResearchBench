# Codebook: SEER 12 Registries (1992-2018) — Colorectal Cancer Survival Trends

## Patient Demographics
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| Patient ID | Unique patient identifier | ID | - |
| Age at diagnosis | Age at cancer diagnosis | Continuous | 0-100+ |
| Sex | Patient sex | Categorical | Male, Female |
| Race/Ethnicity | Race and ethnicity combined | Categorical | Non-Hispanic White (NHW), Non-Hispanic Black (NHB), Non-Hispanic American Indian/Alaska Native (AIAN), Hispanic, Non-Hispanic Asian/Pacific Islander (API) |
| Year of diagnosis | Calendar year of CRC diagnosis | Continuous | 1992-2018 |
| SEER registry | Registry of diagnosis | Categorical | 12 SEER registries (Alaska, Connecticut, Atlanta, Rural Georgia, SF-Oakland, San Jose-Monterey, Hawaii, Iowa, Los Angeles, New Mexico, Seattle-Puget Sound, Utah) |

## Tumor Characteristics
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| Primary site | ICD-O-3 topography code | Categorical | C18.0-C18.9 (colon), C19.9 (rectosigmoid), C20.9 (rectum) |
| Histology | ICD-O-3 morphology code | Categorical | 8140-8389 (adenocarcinoma and subtypes) |
| SEER historic stage | Stage at diagnosis (SEER summary staging) | Categorical | Localized, Regional, Distant, Unstaged/Unknown |
| Grade | Tumor differentiation | Categorical | Well differentiated (I), Moderately differentiated (II), Poorly differentiated (III), Undifferentiated (IV), Unknown |
| Tumor size | Size of primary tumor | Continuous | mm |

## Survival and Outcome Variables
| Variable | Description | Type | Values |
|----------|-------------|------|--------|
| Survival months | Months from diagnosis to death or last follow-up | Continuous | 0-359 |
| Vital status | Alive or dead at last follow-up | Categorical | Alive, Dead |
| Cause of death | Underlying cause of death from death certificate | Categorical | CRC-specific, Other cancer, Non-cancer, Unknown |
| SEER cause-specific death classification | Whether death is attributable to the cancer | Categorical | Dead (attributable to this cancer), Dead (other cause), Alive or censored |

## Derived Variables
| Variable | Description | Derivation |
|----------|-------------|------------|
| 1-year CRC survival | Survived >= 12 months without CRC death | Kaplan-Meier estimate using cause-specific death classification |
| 5-year CRC survival | Survived >= 60 months without CRC death | Kaplan-Meier estimate using cause-specific death classification |
| Diagnosis era | Grouped year of diagnosis | Categorized into multi-year periods for trend analysis |
| CRC subsite | Proximal colon vs. distal colon vs. rectum | Grouped from primary site codes |

## Notes
- SEER historic staging groups cancers into localized, regional, and distant based on extent of disease; this differs from AJCC TNM staging
- Cause-specific survival counts deaths attributable to the specific cancer as events, censoring deaths from other causes
- SEER*Stat software can be used for standardized survival calculations
- Race/ethnicity categorization follows NAACCR standards; persons of Hispanic origin can be of any race
- Survival months are calculated from the date of diagnosis to the date of death or date of last known vital status
- Cases diagnosed by death certificate only (DCO) or autopsy only should be excluded from survival analysis
