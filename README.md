[NovaHealth Healthcare Performance Dashboard.png]
📌 Project Overview
	
Client	NovaHealth Medical Network — a regional healthcare provider founded in 2014, operating hospitals and outpatient clinics across six U.S. states with ~1,400 employees
My Role	Healthcare Data Analyst
Business Focus	Patient care and operational efficiency
Tool Used	Microsoft Excel (Tables, PivotTables, GETPIVOTDATA, Slicers, nested logical functions)
Dataset Size	2,505 patient appointment records across 8 medical departments, 2023–2026
🎯 The Business Problem

NovaHealth was experiencing poor data quality and fragmented patient records as a result of inconsistent data capture across multiple legacy EHR systems. This was creating four interconnected issues:

Poor data quality — inconsistent formats, duplicate entries, and missing information in patient records
Inconsistent financial & workforce data — non-standardized billing and staff overtime logs, making cost tracking difficult
Unstructured patient care data — clinical information stored inconsistently across facilities
Limited operational visibility — delayed reporting and inaccurate performance metrics slowing down decision-making

The Chief Operations Officer commissioned a full analysis of patient, clinical, and operational data to identify root causes, quantify their impact, and support data-driven decisions at the executive level.

🧹 Data Cleaning & Preparation

Before any analysis, the raw dataset was converted into a structured Excel Table and standardized. Key cleaning steps performed:

Converted the raw range into an Excel Table (Patient_Data) to support structured references and dynamic formulas
Parsed the Admission_Date field into usable time dimensions using TEXT(), LEFT(), and MONTH() to derive Month, Short_Month, Month_Num, and Date_Year columns — enabling month-over-month and year-over-year analysis
Split the combined CareStage_Location field (which mixed care stage and department into one text string) into two clean, independent columns: CareStage and Medical_Department
Standardized department names into short codes (MD_Short, e.g. "Intensive Care Unit" → "ICU") using a nested IF() lookup for consistent, compact chart labels
Audited for duplicate and blank records — identified and reviewed repeat Patient_ID entries against their admission dates to distinguish genuine duplicate rows from legitimate repeat patient visits, and removed a blank record row before analysis
Trimmed and formatted text fields (patient names, facility names) for consistent casing and no stray whitespace
🧮 Excel Functions & Techniques Applied
Function / Feature	Purpose
TEXT, LEFT, MONTH	Extract month name, short month, and admission year from raw dates
Nested IF	Classify patients into Risk Tier (Low / Moderate / High Risk) based on Care Stage, classify Age Group (Pediatric / Adult / Geriatric), and map department names to short codes
Excel Tables	Structured references for reliable, self-expanding formulas
PivotTables	Aggregate appointments, revenue, operational cost, and overtime by department, month, year, and clinical status
GETPIVOTDATA	Pull live KPI figures from the PivotTables into a dedicated KPI summary sheet
Slicers	Enable interactive filtering on the dashboard
Conditional formatting / calculated fields	Highlight risk tiers and support dashboard visuals

Logic used for Risk Tier classification:

=IF(CareStage<2, "Low Risk", IF(CareStage<4, "Moderate Risk", "High Risk"))

Logic used for Age Group classification:

=IF(Age<=18, "Pediatric", IF(Age<=64, "Adult", "Geriatric"))
📊 The Dashboard

The final dashboard is built entirely from PivotTable-driven charts on a dark, branded NovaHealth theme, with five headline KPI cards and six supporting visuals.

Headline KPIs
Metric	Value
Total Appointments	2,505
Total Revenue (Patient Billing)	$22,826,272.36
Total Operational Cost	$15,473,834.90
Total Profit	$7,352,437.46 (≈ 32.2% margin)
Total Staff Overtime Logged	21,025.4 hrs
Visuals included
Monthly Appointment Volume (bar chart) — appointments by month, Jan–Dec
Monthly Revenue Trend (line chart) — revenue by month, Jan–Dec
Patients by Department (horizontal bar) — appointment volume per department
Revenue vs. Operational Cost by Year (combo chart) — 2023–2026 trend
Clinical Status Distribution (donut chart) — Discharged / In-Patient Care / Readmitted
Staff Overtime Hours by Year (bar chart) — 2023–2026 trend
🔍 Key Insights
Profitability is healthy but cost-heavy: NovaHealth converts revenue to profit at a ~32% margin, with operational cost tracking closely alongside revenue growth year over year — 2025 was the network's strongest year on both fronts ($8.18M revenue vs. $7.42M peak overtime hours).
August is a clear operational dip: Appointments fell to their lowest point of the year (135, vs. a ~215 monthly average) and revenue dropped to $1.24M — well below every other month suggesting a seasonal staffing or capacity gap worth investigating.
ICU and Surgery are the highest-value departments per case: despite moderate appointment volumes (341 and 298 respectively), ICU and Surgery generate the highest revenue per appointment (~$16.4K and ~$17.0K), making them the network's most resource-intensive and highest-yield service lines.
Pediatrics is high-volume but low-yield: 301 appointments generated only ~$1.7K average revenue per case — the lowest of any department — reflecting lower-acuity, lower-cost care.
17% of patients are being readmitted: against 54.7% successfully discharged and 28.3% still in in-patient care, the readmission rate is a meaningful clinical quality signal for the Clinical Management team to monitor.
Overtime is rising faster than headcount would suggest: overtime hours jumped from 2.3K (2023) to a peak of 7.4K (2025), indicating growing workforce strain that operational cost alone doesn't fully capture.
Data quality issue confirmed: several Patient_IDs appeared more than once in the raw data; on inspection these reflected genuine repeat admissions on different dates rather than duplicate entries — validating the decision to report "Total Appointments" rather than "Total Patients" as the primary volume KPI.
✅ Stakeholder Business Questions — Answered
Requesting Team	Question	Answer
Hospital Administration	Total patients/appointments recorded	2,505
Finance	Total patient billings across all facilities	$22,826,272.36
Operations	Unique medical departments in the network	8 (Cardiology, ER, General Medicine, ICU, Neurology, Orthopedics, Pediatrics, Surgery)
Clinical Management	Patients classified as High-Risk	754 patients
Finance	Total patient bill generated by Emergency Room	$2,190,568.71
Human Resources	Average overtime hours — female staff	8.67 hrs

(The Medical Records lookup task, Risk Tier classification, and duplicate-record audit were built directly into the cleaned dataset via XLOOKUP/VLOOKUP and nested IF logic described above, rather than as one-off answers.)

💡 Recommendations
Investigate the August volume/revenue dip — determine whether it's driven by staffing shortages, seasonal patient behavior, or scheduling gaps, and plan capacity accordingly for future Augusts.
Review the 17% readmission rate by department to identify whether specific care pathways (e.g., Cardiology, ICU) are disproportionately driving readmissions, and target discharge-planning improvements there.
Monitor overtime growth against headcount — the sharp overtime rise from 2023–2025 suggests it may be more cost-effective to expand staffing in high-overtime departments than to continue absorbing overtime costs.
Standardize data entry at the source — enforce structured fields (rather than combined text fields like the original CareStage_Location) in the EHR intake process to reduce future cleaning overhead.
Rebalance service-line focus where appropriate — ICU and Surgery are the highest revenue-per-case departments and may warrant additional capacity investment, while Pediatrics' high volume/low yield profile should be reviewed for cost-efficiency opportunities.
🛠️ Skills Demonstrated

Data Cleaning · Data Standardization · Excel Tables · Nested IF Logic · Lookup Functions (VLOOKUP/XLOOKUP) · PivotTables · GETPIVOTDATA · Dashboard Design · KPI Development · Healthcare Analytics · Business Insight Generation

📁 Repository Contents
Novahealth_Medical_Network_Dataset_Class_3.xlsx — full workbook (raw data, cleaning, PivotTables, KPI sheet, dashboard)
README.md — this write-up

Case study based on the "Data Analytics for Healthcare Management" program by 10Alytics. #HealthTechAnalytics #Decisionmaking
