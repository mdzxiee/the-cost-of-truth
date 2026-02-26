# Data Dictionary

This directory contains the raw extraction files, historical data subsets, and the final merged dataset used to build the "Cost of Truth" Power BI dashboard. 

### 🌟 The Final Production File
* **`cpi&cpj.xlsx - cpi&cpj.csv`**: The final, cleaned, and merged dataset powering the Power BI dashboard. This file contains the normalized 2001-2025 CPI scores, matched fatality metrics, and custom DAX/Excel engineered columns (e.g., Log_Journalists, Safety_Rating).

### 📰 Committee to Protect Journalists (CPJ) Data
* **`cpj-people-list-2026-02-24_05-44-51.csv`** & **`cpi&cpj.xlsx - cpj-rawdata.csv`**: The original, uncleaned extraction records of work-related journalist fatalities. 

### 🏛️ Corruption Perceptions Index (CPI) Data
* **`cpi&cpj.xlsx - cpi-0111-rawdata.csv`**: Historical CPI scores from 2001–2011 (prior to 0-100 scale normalization).
* **`cpi&cpj.xlsx - cpi-1225-rawdata.csv`**: Modern CPI scores from 2012–2025.
* **`cpi&cpj.xlsx - cpi-0125-rawdata.csv`**: The combined, pre-ETL CPI scores spanning the full 25 years.
* **`CPI2025_Results.xlsx - ... .csv`** *(Various)*: Raw supporting data sheets directly from Transparency International, including regional averages, historical trends, and significant year-over-year changes.

### 🛠️ Exploratory Files
* **`cpi&cpj.xlsx - pivot-table.csv`**: Aggregated pivot table generated during the initial exploratory data analysis (EDA) phase.
