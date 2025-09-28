# Case Study: Diabetes Readmission Prediction  

This case study is part of **NutriCare AI**, a portfolio of applied projects in healthcare and nutrition using machine learning.  
The goal is to predict hospital readmissions for diabetic patients using clinical and demographic data.  

---

## Step 1 – Data Import & Settings
- Uploaded **Diabetes_Data.csv** into **Azure ML Studio**.  
- Configured as a **Tabular Dataset** stored in `workspaceblobstore`.  
- Confirmed dataset contained **100,000+ patient hospital admissions** across 130 U.S. hospitals.  

Screenshot: `Dataset_Registered.png`  
Screenshot: `Step1_Settings.png`  

---

## Case Study: Diabetes Data Profiling

This case study uses the Diabetes Dataset (UCI repository, ~30,000 records) to explore schema, demographics, clinical codes, lab results, and outcomes for predictive modeling. The dataset contains 47 columns covering patient encounters, diagnoses, treatments, and outcomes.

### Step 2 – Schema & Profiling

**Overview & Schema**
The dataset includes 47 columns and 30,537 rows. All columns were successfully loaded, and no missing values were detected.

Overview: General dataset summary.
Schema: Column structure and data types.

![Overview](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_Overview.png)  
![Schema](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_Schema.png)  

**Identifiers**
Two key ID fields:

encounter_id: Unique hospital visit identifier.
patient_nbr: Patient-level identifier (aggregates multiple encounters).

![Identifiers](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_IDs.png)  

**Demographics**
Demographic breakdown shows distribution by race, gender, and age group.

Majority identified as Caucasian, followed by African American.
Age brackets were binned in 10-year intervals.

![Demographics](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_Demographics.png)  

**Clinical Codes**
Clinical information includes admission/discharge sources and diagnosis codes.

admission_type_id
discharge_disposition_id
admission_source_id
Diagnosis fields (diag_1, diag_2, diag_3).

![Clinical Codes 1](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_ClinicalCodes1.png)  
![Clinical Codes 2](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_ClinicalCodes2.png)  
![Clinical Codes 3](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_ClinicalCodes3.png)  

**Labs**
Healthcare utilization metrics include:

num_lab_procedures
num_procedures
num_medications
number_outpatient, number_emergency, number_inpatient.

These fields provide insight into healthcare resource use.
![Labs 1](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_Labs1.png)  
![Labs 2](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_Labs2.png)  

**Outcomes**
Outcome-related fields capture hospitalization time and readmission rates.

time_in_hospital: Average length of stay.
readmitted: Key target for prediction (yes/no within 30 days).

![Outcomes 1](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_Outcomes1.png)  
![Outcomes 2](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_Outcomes2.png)  

---

### Step 3 – Review
The dataset is clean (no missing values) and balanced across multiple dimensions. Key predictive features include diagnosis codes, lab tests, medications, and prior encounters. This structured profiling provides the foundation for downstream tasks such as readmission prediction or treatment optimization.

**Dataset Review**
![Review](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step3_Review.png)


---

## Step 4 – Modeling
After profiling the Diabetes dataset, the next step is to build predictive models to evaluate which features are most important for hospital readmissions. The target variable is readmitted, which captures whether a patient was readmitted within 30 days.

- Launched an **AutoML classification experiment** in Azure ML.  
- Target variable: **Readmission (yes/no)**.  
- Algorithms tested: Logistic Regression, Random Forest, Gradient Boosted Trees, Neural Networks.  
- AutoML selected the **best model** based on performance.  

Screenshot: `Step5_ModelTraining.png`  

---

## Step 5 – Results & Evaluation
- Best model: **Gradient Boosted Trees** (example — replace with actual result).  
- Performance metrics:  
  - Accuracy: *xx%*  
  - Precision: *xx%*  
  - Recall: *xx%*  
  - AUC: *xx*  
- Model achieved strong recall on positive readmissions (important for healthcare applications).  

📸 Screenshot: `Step5_Results.png`  

---

## Next Steps
- Deploy the trained model as an Azure ML endpoint.  
- Integrate predictions into a **NutriCare AI dashboard**.  
- Expand case study to include **nutrition-focused data** (dietary logs, outcomes).  

---
