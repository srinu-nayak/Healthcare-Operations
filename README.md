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
