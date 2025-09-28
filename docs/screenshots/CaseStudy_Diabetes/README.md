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

## 📊 Case Study: Diabetes Data Profiling

### Step 2 – Schema & Profiling

**Overview & Schema**
![Overview](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_Overview.png)  
![Schema](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_Schema.png)  

**Identifiers**
![Identifiers](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_IDs.png)  

**Demographics**
![Demographics](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_Demographics.png)  

**Clinical Codes**
![Clinical Codes 1](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_ClinicalCodes1.png)  
![Clinical Codes 2](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_ClinicalCodes2.png)  
![Clinical Codes 3](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_ClinicalCodes3.png)  

**Labs**
![Labs 1](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_Labs1.png)  
![Labs 2](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_Labs2.png)  

**Outcomes**
![Outcomes 1](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_Outcomes1.png)  
![Outcomes 2](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step2_Outcomes2.png)  

---

### Step 3 – Review
**Dataset Review**
![Review](docs/screenshots/CaseStudy_Diabetes/CaseStudy_Diabetes_Step3_Review.png)


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
