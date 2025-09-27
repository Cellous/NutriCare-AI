# Case Study: Diabetes Readmission Prediction  

This case study is part of **NutriCare AI**, a portfolio of applied projects in healthcare and nutrition using machine learning.  
The goal is to predict hospital readmissions for diabetic patients using clinical and demographic data.  

---

## Step 1 – Data Import & Settings
- Uploaded **Diabetes_Data.csv** into **Azure ML Studio**.  
- Configured as a **Tabular Dataset** stored in `workspaceblobstore`.  
- Confirmed dataset contained **100,000+ patient hospital admissions** across 130 U.S. hospitals.  

📸 Screenshot: `Dataset_Registered.png`  
📸 Screenshot: `Step1_Settings.png`  

---

## Step 2 – Schema Review
- Validated schema with **48 columns**.  
- Key features include:  
  - `encounter_id`, `patient_nbr`, `race`, `gender`, `age`,  
  - `admission_type_id`, `discharge_disposition_id`, `time_in_hospital`,  
  - lab/procedure counts, outpatient/inpatient/emergency visits.  
- Verified data types (Integer, String, Decimal).  
- No schema conflicts detected before preprocessing.  

📸 Screenshot: `Step2_Schema.png`  

---

## Step 3 – Data Cleansing & Normalization
- Handled **missing values** (e.g., `weight = 'unknown'`).  
- Normalized continuous variables (e.g., `num_lab_procedures`, `num_procedures`).  
- Encoded categorical variables (`gender`, `race`, `payer_code`).  
- Removed duplicates and irrelevant features (if any).  

📸 Screenshot: `Step3_Cleansing.png`  
📸 Screenshot: `Step4_Normalization.png`  

---

## Step 4 – Modeling
- Launched an **AutoML classification experiment** in Azure ML.  
- Target variable: **Readmission (yes/no)**.  
- Algorithms tested: Logistic Regression, Random Forest, Gradient Boosted Trees, Neural Networks.  
- AutoML selected the **best model** based on performance.  

📸 Screenshot: `Step5_ModelTraining.png`  

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
