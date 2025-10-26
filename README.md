# ✈️ Flight Delay Prediction — On-Premises and On-Cloud

### 🎓 University of Canberra — Final Project (Data Science Pipeline)
**Author:** Mohit Singh Mandota (u3278214)  
**GitHub:** [Singh8888](https://github.com/Singh8888)  
**Email:** dragonlightisback@gmail.com  
**Submission:** Week 13 (on-premises) + Week 14 (on-cloud)  

---

## 📘 Project Overview
This project implements a complete **end-to-end data science pipeline** to predict whether a domestic flight in the United States will be **delayed by more than 15 minutes**.

Two environments were explored:

- 🖥️ **Part A — On-Premises:**  
  Built and evaluated locally using Jupyter Notebook with pandas, scikit-learn, and matplotlib.

- ☁️ **Part B — On-Cloud:**  
  Deployed and executed using **AWS SageMaker**, following the same ML workflow.

---

## 🧠 Business Problem
The company operates a travel booking website and wants to **enhance user experience** by informing customers about the likelihood of a flight delay before booking.  
This model uses weather and flight performance data (from the **US Bureau of Transportation Statistics**) to classify flights as **on-time (0)** or **delayed (1)**.

---

## 🗂️ Dataset
**Source:** U.S. Department of Transportation — Bureau of Transportation Statistics (BTS)  
**Years covered:** 2014–2018  
**Files:** 60 monthly CSVs (~1.6 million rows)  

**Selected Features:**
- Temporal: `Year`, `Month`, `DayofMonth`, `DayOfWeek`, `Quarter`
- Categorical: `Reporting_Airline`, `Origin`, `Dest`
- Numerical: `Distance`, `DepHourofDay`
- Target: `is_delay` (1 if `ArrDel15` ≥ 15 minutes, else 0)

---

## 🧩 Folder Structure

---

## ⚙️ Steps Performed (On-Premises)

1. **Data Extraction**
   - Extracted all monthly ZIP files to `data_raw/extracted_csv/`
   - Combined 60 CSVs → 1,658,130 rows × 20 columns.

2. **Exploratory Data Analysis**
   - Inspected missing values, top airlines, busiest airports.
   - Visualized delay patterns across:
     - Month, Day of Week, Hour of Day, Airline, Airport, Distance.

3. **Feature Engineering**
   - Derived `DepHourofDay` from `CRSDepTime`.
   - One-hot encoded categorical features.
   - Removed missing or irrelevant columns.
   - Created binary target `is_delay`.

4. **Model Building (Logistic Regression)**
   - Split data (80/20 stratified).
   - Trained logistic regression with balanced class weights.
   - Evaluated using Accuracy, Precision, Recall, F1, ROC-AUC.

5. **Model Performance**
   | Metric      | Train | Test  |
   |--------------|-------|-------|
   | Accuracy     | 0.59  | 0.59  |
   | Precision    | 0.28  | 0.28  |
   | Recall       | 0.63  | 0.63  |
   | F1-Score     | 0.39  | 0.39  |
   | ROC-AUC      | 0.64  | 0.65  |

   - **Sensitivity (Recall):** 0.634  
   - **Specificity:** 0.575  

   > The model shows moderate discriminative ability, reflecting the complex, stochastic nature of flight delays.

6. **Model Saving**
   - Saved processed data, figures, and model artifacts under `/data_processed`, `/figs`, and `/artifacts`.

---

## ☁️ Part B — AWS SageMaker (Cloud)
The same pipeline was replicated using **Amazon SageMaker Studio**:
- Data uploaded to S3 bucket.
- Training and testing executed via SageMaker notebook instance.
- Model deployed as a **real-time inference endpoint** for predictions.

Key comparison metrics were recorded between local and cloud runs.

---

## 🧮 Tools and Libraries
- **Language:** Python 3.11  
- **Environment:** Jupyter Notebook  
- **Core Libraries:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`  
- **Cloud:** AWS SageMaker (for Part B)

---

## 📊 Results Summary
- Delays are most frequent during **evening hours (6–9 PM)** and **summer months (June–August)**.  
- Top delay airports include **ATL, DFW, ORD, LAX**.  
- **Shorter flights** tend to have fewer delays.  
- Logistic regression yields balanced performance with fair generalization across train/test.

---

## 💡 Future Improvements
- Introduce weather features (temperature, visibility, precipitation).  
- Use ensemble models (Random Forest, XGBoost).  
- Perform hyperparameter tuning and feature selection.  
- Deploy REST API endpoint for real-time delay prediction.

---

## 🧠 Reflection
> This project provided hands-on experience across the **full data science lifecycle**—from raw data ingestion and feature engineering to ML modeling and cloud deployment.  
> It reinforced the importance of reproducible pipelines, feature design, and deployment scalability.

---

## 📜 License
This repository is for **academic purposes only** under the University of Canberra Data Science unit.

---

### ✅ Author
**Mohit Singh Mandota**  
Master of Data Science — University of Canberra  
📧 *dragonlightisback@gmail.com*
