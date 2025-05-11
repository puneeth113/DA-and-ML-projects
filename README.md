Here's your complete and polished **README.md** for your healthcare mini project, integrating **clustering** and **Random Forest classification** models:

---

# 🏥 Healthcare Data Analysis & ML Project

This project explores inpatient hospital discharge data to extract insights, handle outliers, perform clustering, and build predictive models. The focus is on analyzing patterns in patient stays, treatment costs, and risk levels.

---

## 📁 Dataset

* **Source**: NY Statewide Planning and Research Cooperative System (SPARCS)
* **Format**: JSON (converted to DataFrame)
* **Rows**: \~50,000+ (sample)
* **Target Variables**: `length_of_stay`, `total_costs`, `apr_risk_of_mortality`

---

## 🔧 Data Preprocessing

* Handled missing/null values
* Converted `length_of_stay`, `total_costs`, and other numerics to appropriate formats
* Handled categorical encoding using:

  * Label Encoding for modeling
  * One-hot for EDA (optional)
* Outliers detected using IQR on `length_of_stay` and marked via `is_outlier` column

---

## 📊 Exploratory Data Analysis

Visualized:

* Length of stay distribution by age, gender, severity
* Average costs by race, hospital, admission type
* Pie & bar charts showing insurance types and costs
* Violin plots to show spread of stay across severity levels

**Sample Insight**:

* Elderly patients (`70+`) tend to stay longer
* Emergency patients incur higher total costs
* Medicare payments have highest average charges (\~19k)

---

## 🤖 Modeling

### 1. 📌 **Clustering (Unsupervised Learning)**

* **Model**: KMeans Clustering
* **Goal**: Group patients by `length_of_stay`
* **Clusters**: 3 groups identified
* **Use Case**: Classify new patients into stay-duration segments
  *Example*: `kmeans.predict([[6]]) → Cluster 1`

---

### 2. 🌲 **Random Forest Classifier**

* **Objective**: Predict `apr_risk_of_mortality` (Multiclass)
* **Features**:

  * `'apr_severity_of_illness_code', 'apr_mdc_code', 'ccs_procedure_code', 'ccs_diagnosis_description', 'patient_disposition', 'gender', 'age_group', 'emergency_department_indicator', 'total_costs', 'length_of_stay', 'apr_severity_of_illness_description', 'apr_drg_description', 'apr_drg_code', 'ccs_diagnosis_code'`
* **Final Accuracy**: **0.812**
* **Model Evaluation**:

  * Good classification for `Minor`, `Moderate`, and `Major`
  * `Extreme` cases slightly underpredicted
  * Clear confusion matrix and classification report used
* **Important Features**:

  * `length_of_stay`, `total_costs`, `age_group`, `emergency_department_indicator` ranked highest

---

## ✅ Conclusion

* Successfully extracted valuable patterns from hospital discharge data.
* Built two ML models:

  * A clustering model for patient stay duration categorization
  * A Random Forest classifier to predict mortality risk with >81% accuracy
* The project demonstrates a full ML pipeline: **EDA → Preprocessing → Modeling → Evaluation**

---

## 📌 Future Enhancements

* Include more feature engineering (e.g., diagnosis grouping)
* Use SHAP/LIME for interpretability
* Tune hyperparameters further for better accuracy

---
