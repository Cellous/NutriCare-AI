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

Summary

Overall, these three fields provide complementary insights into patient readmission risk. Payer code captures potential socioeconomic and access-to-care patterns, A1C result reflects clinical health status and disease control, and number inpatient measures historical patterns of hospitalization. Together, they represent financial, medical, and behavioral dimensions of healthcare use. Including all three in the predictive model can improve its ability to identify patients at high risk of readmission.

Having explored the key fields (payer_code, A1Cresult, number_inpatient) and summarized their potential impact on predicting readmissions, the next step was to train and evaluate predictive models. Using Azure Automated ML, the diabetes dataset was profiled and prepared for classification, with readmission (yes/no within 30 days) selected as the target variable. This allowed the AutoML process to test multiple algorithms and identify the best-performing model for predicting hospital readmissions.

### Feature Review: Key Predictors of Readmission  

**Payer Code**  
![Payer Code](docs/screenshots/CaseStudy_Diabetes/payer_code.png)  

The `payer_code` field captures the type of insurance or payment source for the patient.  
This can reflect socioeconomic status and access-to-care patterns, which influence the likelihood of readmission.  
For example, patients with limited coverage may face delays or barriers to care, increasing the risk of hospital return.  

---

**A1C Result**  
![A1C Result](docs/screenshots/CaseStudy_Diabetes/A1Cresult.png)  

The `A1Cresult` field reflects blood sugar control over time. Poor A1C results can indicate higher risk of complications,  
making this field a strong predictor of readmission. Since A1C values change over time, they provide ongoing insight into  
a patient’s diabetes management and potential hospital readmission.  

---

**Number Inpatient**  
![Number Inpatient](docs/screenshots/CaseStudy_Diabetes/number_inpatient.png)  

The `number_inpatient` field tracks the number of prior hospitalizations. A higher count is a strong indicator of chronic  
health issues and greater likelihood of future readmissions, making it one of the most important predictors in the dataset.  

---

**Summary**  
Together, these three fields provide complementary insights into patient readmission risk:  
- `payer_code` highlights socioeconomic and financial aspects,  
- `A1Cresult` represents clinical lab-based health indicators, and  
- `number_inpatient` reflects historical patterns of hospitalization.  

Including all three fields in the predictive model improves the ability to identify patients at high risk of readmission.

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

- **Best model:** Gradient Boosted Trees  
- **Performance metrics (from AutoML results):**  
  - Accuracy: **0.628**  
  - Precision: **0.618**  
  - Recall: **0.514**  
  - F1 Score: **0.561**  
  - AUC: **0.672**  

Screenshot:  
![Step 5 Results](docs/screenshots/CaseStudy_Diabetes/Step5_Results.png)  

### Evaluation Results Explanation  

The model achieved an overall **accuracy of 62.8%**, which means it correctly predicted readmission outcomes in roughly two-thirds of the cases.  
While this accuracy is moderate, the **AUC score of 0.672** shows that the model has some ability to distinguish between patients who are likely  
to be readmitted and those who are not.  

Looking deeper into the metrics:  
- **Precision (0.618):** When the model predicts a readmission, it is correct about 62% of the time.  
- **Recall (0.514):** The model identifies about half of all actual readmissions, showing room for improvement in sensitivity.  
- **F1 Score (0.561):** Balances precision and recall, highlighting a fair trade-off between identifying true readmissions and avoiding false alarms.  

**Interpretation:**  
These results suggest that while the model provides useful insights, additional improvements — such as feature engineering,  
hyperparameter tuning, or using more advanced algorithms — could enhance prediction performance in future iterations.  

---

## Step 6 – Conclusion & Next Steps  

### Conclusion  
This case study demonstrated the use of **Azure Machine Learning AutoML** to predict hospital readmissions for diabetic patients.  
By exploring key features such as `payer_code`, `A1Cresult`, and `number_inpatient`, we identified meaningful patterns that reflect  
financial, clinical, and historical aspects of patient care.  

The best-performing model, **Gradient Boosted Trees**, achieved:  
- Accuracy: **62.8%**  
- AUC: **0.672**  
- Precision: **0.618**, Recall: **0.514**, F1 Score: **0.561**  

These results highlight the model’s ability to capture important trends while also showing the need for further optimization.  

---

### Next Steps  
To improve prediction accuracy and clinical usefulness, the following steps are recommended:  
1. **Feature Engineering:** Create new features such as time since last admission, medication adherence measures, or comorbidity indices.  
2. **Data Enrichment:** Integrate external data sources (e.g., socioeconomic indicators, patient lifestyle data) to improve predictive power.  
3. **Model Optimization:** Perform hyperparameter tuning or experiment with advanced models such as XGBoost, LightGBM, or Neural Networks.  
4. **Class Imbalance Handling:** Apply resampling techniques (SMOTE, class weights) to address imbalances in readmission vs. non-readmission cases.  
5. **Deployment & Monitoring:** Deploy the model in a clinical setting using Azure endpoints, and set up monitoring for real-time performance tracking.  
6. **Ethical & Practical Considerations:** Ensure fairness across patient groups and evaluate how predictions can support — not replace — clinical decision-making.  

---

**Takeaway:**  
This project lays a strong foundation for predictive healthcare analytics. With additional data, refined features, and advanced modeling,  
the readmission prediction system can evolve into a valuable decision-support tool to improve patient outcomes and reduce healthcare costs.  

---
