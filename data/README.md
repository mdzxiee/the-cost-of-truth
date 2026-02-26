# Data Dictionary

This directory contains all raw source files, intermediate transformation outputs, and the final analytical dataset used to develop the **“Cost of Truth”** Power BI dashboard. The structure documents the complete ETL process from extraction to the final analytical model.

---

## Final Production Dataset

- **`cpi&cpj.csv`**  
  The cleaned and merged dataset that powers the Power BI dashboard.

  This file includes:
  - Corruption Perceptions Index (CPI) scores (2001–2025) converted to a consistent 0–100 scale  
  - Journalist fatality counts aggregated by country and year  
  - Engineered analytical variables (e.g., `Log_Journalists`, `Safety_Rating`)  
  - Standardized country names  
  - Structured country-year panel format  

  This is the primary dataset for analysis and reporting.

---


## Committee to Protect Journalists (CPJ) Data  
Source:[https://cpj.org/data/](https://cpj.org/data/)

- **`cpj-people-list-2026-02-24_05-44-51.csv`**  
- **`cpj-rawdata.csv`**

  Original extraction of confirmed work-related journalist fatalities. These files contain case-level records including:
  - Journalist name  
  - Country  
  - Year of death  
  - Confirmation status  
  - Work-related classification  

  These records were aggregated into country-year fatality totals during data processing.

---

## 🏛️ Corruption Perceptions Index (CPI) Data  
Sources: [https://datahub.io/core/corruption-perceptions-index](https://datahub.io/core/corruption-perceptions-index)  & [https://www.transparency.org/en/cpi/2025](https://www.transparency.org/en/cpi/2025)

- **`cpi-0111-rawdata.csv`**  
  CPI scores from 2001–2011 (pre-2012 methodology; reverse-scaled format).

- **`cpi-1225-rawdata.csv`**  
  CPI scores from 2012–2025 (standardized 0–100 scale).

- **`cpi-0125-rawdata.csv`**  
  Combined CPI dataset covering the full 25-year study period prior to transformation.

- **`CPI2025_Results.xlsx` (multiple extracted sheets)**  
  Supplementary CPI materials including:
  - Regional averages  
  - Historical trends  
  - Year-over-year changes  

These files provide the corruption measurement component of the study.

---

## Country Name Standardization

Country names were standardized before merging the datasets to ensure accurate country-year matching.

This process included:
- Aligning alternative spellings (e.g., “United States” and “USA”)  
- Updating legacy country names  
- Ensuring consistent naming conventions across all files  
- Verifying one unique country identifier per country-year record  

This step ensured accurate joins and prevented duplication or data loss.

---

## Exploratory & Intermediate Files

- **`pivot-table.csv`**  
  Aggregated output generated during exploratory data analysis (EDA).  
  Used to verify:
  - Country-level fatality totals  
  - Yearly aggregation logic  
  - CPI alignment prior to final merging  

---

## Data Integration Process

The final dataset was constructed as follows:

1. Aggregated journalist fatalities into country-year totals.  
2. Converted CPI scores to a consistent 0–100 scale.  
3. Standardized country names across datasets.  
4. Merged CPI and fatality data using country-year keys.  
5. Created analytical variables for modeling and visualization.  
6. Validated completeness across the 2001–2025 panel.

---

## Time Coverage

- **2001–2025**  
- 25-year longitudinal cross-national panel dataset  

---

This directory documents the full data preparation process for the “Cost of Truth” corruption and journalist safety analysis.
