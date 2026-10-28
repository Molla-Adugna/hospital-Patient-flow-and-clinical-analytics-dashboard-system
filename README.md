# Hospital Patient Flow & Clinical Analytics Dashboard

## 📌 Project Overview
The **Hospital Patient Flow & Clinical Analytics Dashboard** is an interactive, end-to-end healthcare analytics solution built using **Microsoft Excel**, **Power Query**, and **Data Model (Power Pivot / DAX)**. 

This project analyzes patient admissions, clinical diagnoses, operational flow, and billing metrics to provide actionable insights into hospital performance, capacity planning, and patient demographics.

---

## 📁 Repository & Project Structure

```text
Hospital_Patient_Flow_And_Clinical_Analytics_Dashboard_System/
│
├── Hospital_Patient_Flow_And_Clinical_Analytics_Dashboard.xlsx   # Main Excel Dashboard Workbook
│
└── patient_flow_analytics_raw_data/                              # Folder containing raw datasets
    ├── dim_patients.xlsx                                          # Patient demographic data
    ├── fact_diagnoses.xlsx                                        # Primary & secondary patient diagnoses
    ├── fact_encounters.xlsx                                       # Admission, discharge, billing, & LOS details
    └── fact_medications.xlsx                                      # Prescribed medication data
```
## ⚙️ Data Pipeline & Transformation Workflow
**1. Data Ingestion:** Raw data files were extracted from the patient_flow_analytics_raw_data folder and imported into Power Query.  
**2. Dedicated Date Table:** Created a custom DimDate table in Power Query containing complete calendar hierarchies (Date, Year, QuarterNo, Quarter, MonthNo).  
**3. ETL & Data Cleaning:** Cleaned, verified data types, standardized column headers, and handled null/missing values.  
**4. Data Model Loading:** Loaded all transformed queries using "Close & Load To... -> Only Create Connection" and checked "Add this data to the Data Model".

🔗 Data Model & Entity Relationship Diagram (ERD)
The Data Model follows a Star Schema / Snowflake Hybrid Architecture centered around patient encounters:  
```text
dim_patients [1] ─── [<] fact_encounters (Joined on PatientID)

DimDate [1] ─── [<] fact_encounters (Joined on Date → AdmissionDate)

fact_encounters [1] ─── [<] fact_diagnoses (Joined on EncounterID)

fact_encounters [1] ─── [<] fact_medications (Joined on EncounterID)
```
## 🧮 Data Model Measures (DAX / Excel Data Model)
Key operational, clinical, and financial measures calculated in the data model include:
### 📈 Admission & Flow Metrics
    Total Admissions / Total Encounters: 2,500  
    Admissions YTD: 113    
    Rolling 30-Day Admissions: 6    
    Unique Patients: 1,062   
    Patients with Multiple Encounters: 730   
    Average Length of Stay (ALOS): 14.51 Days   
### 🏥 Admission Types Breakdown
    Emergency Encounters: 819 (32.76% Emergency Share)   
    Elective Encounters: 823   
    Urgent Encounters: 858    
### 🩺 Clinical & Medication Metrics
    Total Diagnoses Recorded: 3,257   
    Hypertension Count: 535   
    Cancer Count: 552   
    Arthritis Count: 516    
    Total Medications Dispensed: 4,453   
## 💰 Financial Metrics
    Total Billing Amount: $25,272,254.37    
    Average Billing per Encounter: $10,108.90   
## 🖥️ Interactive Dashboard Layout 
The Dashboard tab provides a streamlined executive view driven by synchronized Slicers (Gender, BloodGroup, AgeGroup, and Month):  
```text
========================================================================================================
                                 HOSPITAL PATIENT FLOW & CLINICAL ANALYTICS DASHBOARD
========================================================================================================
[ KPI Card: TOTAL ADMISSIONS ]  [ KPI Card: ADMISSIONS YTD ]  [ KPI Card: AVG LENGTH OF STAY ]  [ KPI Card: EMERGENCY SHARE % ]  [ KPI Card: TOTAL BILLING ]
--------------------------------------------------------------------------------------------------------
 [ SLICERS ]  │  [ CHART: Chronic Conditions by Age Group ]         │  [ CHART: Top Medications Dispensed ]       │  [ SLICERS ]
 • Gender     │  • Line chart tracking Arthritis, Cancer,          │  • Bar chart highlighting prescribed       │  • BloodGroup
 • Month      │    & Hypertension across Age Groups                 │    medications (Aspirin, Paracetamol, etc.) │  • AgeGroup
--------------│-----------------------------------------------------│---------------------------------------------│-------------
              │  [ CHART: Admission Type Distribution ]             │  [ CHART: Monthly Admission Type Trend ]    │  [ CHART: Condition by Gender ]
              │  • Stacked Bar Chart comparing Urgent,              │  • Line trend tracking Elective, Emergency, │  • Stacked Column Chart mapping
              │    Emergency, & Elective volumes                    │    & Urgent cases month-over-month          │    diagnoses by Female vs Male
================================================================================================
```
## 🚀 Key Features & Highlights
Dynamic Slicing & Filtering: Instant visual filtering across age, gender, blood group, and time periods.  
Separation of Layers: Dedicated sheets for Raw Data Connections, Data Model, Pivot Table Calculations (Analysis), and Presentation (Dashboard).  
High Performance: Designed using Data Model connections to ensure optimal workbook size and fast calculation speed.

## 🛠️ How to View & Use the Project
1. Clone or download this repository.
2. Ensure the folder structure is preserved: keep patient_flow_analytics_raw_data in the same directory as Hospital_Patient_Flow_And_Clinical_Analytics_Dashboard.xlsx.
3. Open Hospital_Patient_Flow_And_Clinical_Analytics_Dashboard.xlsx in Microsoft Excel 2016 or newer (with Power Pivot enabled).
4. Navigate to the Dashboard sheet and use the interactive slicers to explore the analytics.
