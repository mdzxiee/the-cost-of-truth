# The Cost of Truth: Global Press Safety and Global Corruption (2001–2025)

**[View the Interactive Power BI Dashboard](https://app.powerbi.com/view?r=eyJrIjoiMmEyOTNjY2MtODA0NC00MzQwLTg5ZjItN2UyMDE0MDU1Yzg0IiwidCI6ImE4YWM1ODdmLWVkZTAtNDA0MS1hY2M3LWZhNmU3NDAwNWM2MiIsImMiOjEwfQ%3D%3D)** 
**[Read the Full Analytical Insights Report](insights.md)** 

## 1. Problem Statement
Is there a measurable relationship between systemic political corruption and journalist fatalities worldwide?

While armed conflict is widely recognized as a major threat to press safety, the role of long-standing institutional corruption in shaping journalist vulnerability during non-war periods remains less systematically examined. This project evaluates whether a country’s Corruption Perceptions Index (CPI) score is statistically associated with increased journalist fatality rates over a 25-year period.

*Note: This analysis focuses on identifying patterns and correlations, not establishing direct causation.*

## 2. Project Objective & Context
Press freedom plays a critical role in democratic accountability and institutional transparency. The objective of this project is to develop an interactive, data-driven analytical model that integrates:

* Global corruption indicators
* Confirmed journalist fatality records

By merging these datasets, the project moves beyond anecdotal claims and examines long-term structural patterns between institutional integrity and press safety outcomes from 2001 to 2025.

## 3. Data Sources
This analysis integrates two internationally recognized datasets:

### 3.1 Corruption Perceptions Index (CPI)
* **Source:** Transparency International
* The CPI scores 181 countries and territories annually based on perceived levels of public sector corruption using a 0–100 scale (higher scores indicate lower perceived corruption).

### 3.2 Journalist Fatalities Database
* **Source:** Committee to Protect Journalists (CPJ)
* The CPJ database documents confirmed work-related journalist deaths, including:
  * Targeted killings
  * Crossfire casualties
  * Fatalities during dangerous assignments

## 4. Analytical Methodology
To build a unified relational dataset suitable for Power BI modeling, several transformation steps were performed.

### 4.1 Data Extraction & Normalization
* Extracted the `Year` variable from CPJ timestamp fields to enable time-based joins.
* Standardized historical CPI scores (2001–2011), which used alternative scaling systems, into the modern 0–100 format for consistency across the 25-year dataset.

### 4.2 Handling Missing Data & Data Integrity

**Trend Estimation** Missing CPI values were estimated using linear regression via Excel’s `FORECAST.LINEAR` function:
```excel
=FORECAST.LINEAR(2015, H2:R2, H1:R1)
```
This method preserved trend continuity while minimizing distortion of long-term averages.

**Data Exclusion** Countries with substantial and irreconcilable data gaps that significantly skewed trend interpretation were excluded from aggregated analysis to preserve statistical integrity.

### 4.3 Feature Engineering
Several analytical variables were constructed:
* `Safety_Rating` (based on fatality thresholds)
* `Corruption_Level` (categorical grouping)
* `Country_CPI_Score_Average`
* `Log_Journalists` (logarithmic transformation to reduce extreme outlier distortion in scatter visualizations)

*Example classification logic:*
```excel
=IFS(F2 > 5, "Critical Risk", F2 >= 4, "High Risk", F2 >= 1, "Moderate Risk", F2 = 0, "Safe")
```

## 5. Final Data Schema
The cleaned dataset contains the following primary dimensions and measures:  
`Country`, `ISO3`, `Region`, `Year`, `Era`, `CPI_Score`, `Number_of_Journalists_Killed`, `Log_Journalists`, `Safety_Rating`, `Corruption_Level`, `Country_CPI_Score_Average`, `CPI_Rank`, `Total_Deaths`, `Death_Rank`

## 6. Tools & Techniques
* **Data Processing:** Microsoft Excel
* **Modeling & Visualization:** Microsoft Power BI
* **Language:** DAX (Data Analysis Expressions)
* **Techniques Applied:**
  * Time-Series Analysis
  * Logarithmic Scaling
  * Relational Data Modeling
  * Conditional Risk Categorization

## 7. Key Analytical Findings
* Approximately 80% of recorded journalist fatalities (2001–2025) occurred in countries categorized under lower CPI score ranges (CPI < 40).
* Corruption levels remained relatively stable over time, while fatality counts fluctuated significantly.
* Periods of armed conflict produced temporary concentration spikes in specific regions.
* However, elevated fatality counts were also observed in non-war contexts where long-term institutional weaknesses were present.

These findings suggest a strong statistical association between lower institutional integrity and elevated journalist risk exposure.

## 8. Repository Setup
To explore this project locally:

1. Clone the repository.
2. Navigate to the `/data` folder for cleaned `.csv` datasets.
3. Open `The_Cost_Of_Truth.pbix` in Microsoft Power BI Desktop.
4. Review `insights.md` for a detailed analytical narrative.
5. Alternatively, view `dashboard_preview.pdf`.

## 9. Project Contribution
This project demonstrates how integrating independent global datasets can generate structured, data-driven insight into institutional risk environments. Rather than focusing solely on conflict zones, the analysis highlights the importance of examining long-term governance conditions when evaluating press safety risks.

## 10. References
* **Committee to Protect Journalists. (2025).** *Explore CPJ’s database of attacks on the press.* [https://cpj.org/data/](https://cpj.org/data/)
* **Transparency International. (2017).** *Corruption Perceptions Index 2001–2016.* [https://datahub.io/core/corruption-perceptions-index](https://datahub.io/core/corruption-perceptions-index)
* **Transparency International. (2026).** *Corruption Perceptions Index 2025.* [https://www.transparency.org/en/cpi/2025](https://www.transparency.org/en/cpi/2025)
