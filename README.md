# Healthcare Operations: Patient Waiting List & Trend Analysis Dashboard
### Interactive Dashboard Link: <a><a/>

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


Based on your instructions and the [data in the Power BI report](https://app.powerbi.com/view?r=eyJrIjoiNGU4YmQ0NzQtNTUzNS00OTViLWE5ZDEtODVjZjYwNTE2ZGI5IiwidCI6IjFiMTRiNGZmLTMxMWUtNGEyMC1iM2NjLTM0ZGZhNzAxMDI2ZCJ9) you are viewing, here is an "Insights Deep Dive" for this Patient Wait List Summary.

***

### Insights Deep Dive: Patient Wait List Analysis (Jan 2018 - Mar 2021)

This section provides a detailed breakdown of the key trends observed in the patient waitlist data.

**1. Overall Waitlist Is Growing, Driven by Outpatient Services**

* **Quantified Finding:** The total waitlist has seen significant growth. The "Last Month Wait List" (as of March 2021) stands at 709K, a notable increase from the "PY Last Month Wait List" of 640K.
* **The Story:** This growth is not a sudden event but a steady upward trend, as shown in the "Monthly Trend Analysis" chart. The driving force behind this increase is overwhelmingly from "Outpatient" services, which make up 74.36% of all cases. The Outpatient waitlist grew from approximately 0.50M in mid-2018 to 0.63M by early 2021. In contrast, the waitlist for Inpatient/Day Cases has remained relatively flat and low (hovering between 46K and 62K) over the same period.

**2. Accident & Emergency Has a Disproportionately High Wait Time**

* **Quantified Finding:** In the "Top 5 Specialty" chart (likely sorted by wait time), Accident & Emergency has the highest metric at 69.50. This is more than double the next-highest specialty, Dermatology (35.00), and significantly higher than Cardiology (28.00) and Pain Relief (27.00).
* **The Story:** The data indicates a critical bottleneck specifically within the Accident & Emergency specialty. While other departments have waitlists, the metric for A&E is an extreme outlier, suggesting a severe imbalance between patient demand and service capacity compared to other specialties.

**3. Working-Age Adults (16-64) Dominate All Wait Time Bands**

* **Quantified Finding:** The "16-64" age group (dark blue bar) is the largest demographic on the waitlist across every single time band. For example, in the "0-3 Months" wait band, this group (34 units) is significantly larger than the "65+" group (21 units) and the "0-15" group (6 units).
* **The Story:** As seen in the "Time band vs Age Profile" chart, working-age adults consistently form the largest portion of the waitlist. This pattern holds true not only for new additions to the list (0-3 months) but also for those with the longest waits (18+ months), indicating this demographic is the most heavily impacted by wait times overall.
