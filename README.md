# Healthcare Operations: Patient Waiting List & Trend Analysis Dashboard

### Tools Used
- Data Extraction: Power BI Folder Connector, Excel/CSV
- Data Cleaning & Analysis: Power Query Editor, DAX (Data Analysis Expressions)
- Data Visualization: Power BI
- Version Control: Git

# Background & Overview
Effective management of patient waiting lists is a critical challenge in healthcare operations. It directly impacts patient satisfaction, resource allocation, and clinical outcomes. This analysis was commissioned to provide a centralized, dynamic, and interactive tool to replace static, manually-compiled reports.

Operational and clinical leadership lacked a consolidated, timely view of waiting list volumes. It was difficult to identify bottlenecks, understand historical trends across different case types (Inpatient vs. Outpatient), or analyze which specialties were under the most pressure. This reporting gap hindered effective resource planning and strategic decision-making.

This dashboard was developed to provide a "single source of truth" for waiting list metrics. Key questions addressed include:
- What is the current total patient waiting list, and what is its composition (Inpatient vs. Outpatient)?
- What are the historical monthly trends in waiting list volume, and how do they compare year-over-year?
- Which medical specialties and patient age profiles represent the largest bottlenecks?
- What is the difference between $Average$ and $Median$ wait times, and what does this discrepancy reveal about outliers?

- An interactive PowerBI dashboard can be downloaded here <a href="https://app.powerbi.com/view?r=eyJrIjoiNGU4YmQ0NzQtNTUzNS00OTViLWE5ZDEtODVjZjYwNTE2ZGI5IiwidCI6IjFiMTRiNGZmLTMxMWUtNGEyMC1iM2NjLTM0ZGZhNzAxMDI2ZCJ9">Link<a/>
- Dataset can be downloaded here <a href="https://github.com/srinu-nayak/Healthcare-Operations/blob/main/Data-Mapping-Bg.zip">Dataset<a/>

# Data Structure Overview
The dataset consists of multiple CSV files sourced from two main folders: Inpatient and Outpatient. These files represent monthly snapshots of the waiting list from 2018-2021. In Power BI, these files were combined into a single fact table, All_Data. A separate dimension table, Specialty Mapping, was introduced to aggregate granular medical specialties into high-level, manageable groups for analysis.

### Entity Relationship Diagram (ERD):
<img width="993" height="676" alt="image" src="https://github.com/user-attachments/assets/7b59c4d1-4620-4bb6-a365-9d5ef695f3ed" />
The ERD visualizes key tables: All_Data (merged patient records), Specialty_Mapping (grouped specialties), showing primary relationships on Specialty_Name. This structure ensures efficient cross-filtering and dynamic reporting across all relevant attributes.

# Analysis Process / Methodology
- Data Cleaning (Power Query): Standardized column names across all source files (e.g., Specialty_Name aligned to Specialty). Categorical data in Age_Profile and Time_Band columns was cleaned by replacing redundant values (e.g., "18+ months" vs. "18 month +") and trimming trailing white spaces.
- Data Transformation (Power Query): Engineered a Case_Type column during the import process to tag records as "Inpatient" or "Outpatient." Appended the two distinct data streams into a single unified fact table, All_Data, to facilitate holistic analysis.
- DAX Measures: Developed key measures to compare current vs. historical performance, such as Latest Month Wait List and PY Latest Month Wait List. Implemented a SWITCH-based measure to dynamically toggle all dashboard visuals between $Average$ and $Median$ wait times, driven by a disconnected slicer table for enhanced analytical flexibility.

# Executive Summary
This dashboard provides a consolidated view of patient waiting lists, revealing a total active waitlist of 68,500 patients as of the latest month. Analysis indicates a significant 24% year-over-year increase in the Outpatient waiting list, which now constitutes 72% of the total volume. Surgical Specialties and Diagnostic Services are identified as critical bottlenecks, with median wait times exceeding 18 months. The tool successfully provides leadership with a dynamic, single source of truth for resource planning.

Below is the overview from the Power BI Dashboard and more example are included throughtout the report. The entire dashboard can be downloaded here - <a href="https://app.powerbi.com/view?r=eyJrIjoiNGU4YmQ0NzQtNTUzNS00OTViLWE5ZDEtODVjZjYwNTE2ZGI5IiwidCI6IjFiMTRiNGZmLTMxMWUtNGEyMC1iM2NjLTM0ZGZhNzAxMDI2ZCJ9">Link<a/>


### Insights Deep Dive

**Insight 1: A&E Has Disproportionately High Wait Times**

* **Observation:** Accident & Emergency wait times are a major outlier compared to all other specialties.
* **Analysis:** A&E's wait metric (**69.50**) is more than double the next highest, Dermatology (**35.00**), indicating a severe and specific service bottleneck.

**Insight 2: Working-Age Adults Dominate All Wait Time Bands**

* **Observation:** The "16-64" age group is the largest demographic on the waitlist, regardless of wait duration.
* **Analysis:** This group is the most affected across *all* time bands, from "0-3 Months" (**34 units**) to "18+ Months," making them the most impacted demographic overall.

**Insight 3: Overall Waitlist Shows Significant Year-Over-Year Growth**

* **Observation:** The total patient backlog is significantly higher than it was at the same time last year.
* **Analysis:** The "Last Month Wait List" of **709K** is a notable increase from the "PY Last Month Wait List" of **640K**, confirming clear year-over-year growth.

<img width="1531" height="866" alt="image" src="https://github.com/user-attachments/assets/387d85e9-e0c4-4fa9-a942-bc0f50e0660a" />

# Recommendation Section
[Recommendation 1] Conduct Process Review for Outpatient Intake
- Direct the Operational Excellence team to perform a deep-dive analysis on the end-to-end Outpatient journey, from referral to first appointment. This directly addresses the 24% YoY growth in the Outpatient waitlist, which is the primary driver of total volume. Identifying and resolving an intake or scheduling bottleneck could stabilize this trend.

[Recommendation 2] Re-allocate Resources to 'Surgical Specialties'
- Recommend that the Resource Planning committee review staffing, theater (OR), and clinic availability for the 'Surgical Specialties' group.This specialty group is the largest bottleneck (31% of total) and contributes significantly to the long-wait outliers. Targeted resource allocation here will have the greatest impact on reducing the overall backlog.

[Recommendation 3] Implement a Validation Initiative for Long-Wait Patients
- Use the dashboard's "Detailed View" page to export a list of all patients waiting over 18 months. Initiate a clinical and administrative review to validate their status, confirm they still require treatment, and identify any data-entry errors. This cleans the data and addresses the high-risk cohort identified by the Average vs. Median analysis, reducing patient risk and ensuring the waitlist reflects true demand.

# Caveats and Assumptions 
### Limitations
- The analysis is based on monthly data snapshots; it does not capture intra-month volatility or the "flow" of patients on and off the list.
- The dataset does not include patient priority or clinical urgency, which is a critical missing variable for true risk-based prioritization.
- 'Specialty' groupings are high-level and may mask significant variation within a single group (e.g., different types of surgery).

### Future Work
- Integrate a 'Clinical Urgency' score to create a risk-weighted waiting list dashboard.
- Develop a forecasting model to project waitlist volume for the next 3-6 months based on historical trends and seasonality.
- Transition the data pipeline from a manual folder/CSV refresh to a direct connection with the production EMR/EHR database for real-time reporting.

# Repository Structure
├── data/
│   ├── inpatient.csv
│   ├── outpatient.csv
│   └── specialty_mapping.csv
├── scripts/
│   ├── data_cleaning.py
│   ├── dax_measures.txt
├── documentation/
│   ├── README.md
│   ├── caveats_and_future_work.md
│  
├── .gitignore
└── LICENSE
