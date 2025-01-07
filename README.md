# MLCompetition-FluShot
 This repository contains the code and analysis for a machine learning project designed to predict the likelihood of individuals receiving H1N1 and Seasonal Influenza vaccines. The project utilizes a dataset provided by the U.S. National Center for Health Statistics and applies a variety of preprocessing techniques and machine learning models to achieve optimal results.

The FluShot Learning project leverages machine learning techniques to predict the likelihood of individuals receiving H1N1 and Seasonal Influenza Vaccines based on demographic, behavioral, and medical attributes.

## **Project Overview**

The goal of this project is to build predictive models that estimate the likelihood of vaccination for H1N1 and Seasonal Influenza based on demographic, behavioral, and health-related data. This work aims to provide insights into vaccination trends and support public health initiatives.

### **Dataset**
- **Source**: [DrivenData Flu Shot Learning](https://www.drivendata.org/competitions/66/flu-shot-learning/)
- **Size**: 26,707 rows, 36 features
- **Targets**:
  - `h1n1_vaccine`: Whether the respondent received the H1N1 flu vaccine (binary).
  - `seasonal_vaccine`: Whether the respondent received the Seasonal flu vaccine (binary).
  
### **Evaluation Metric**
The models are evaluated using the **Area Under the Receiver Operating Characteristic Curve (AUC-ROC)**. The final performance is determined by the mean AUC score for both target variables.

---

## **Methodology**

### **1. Data Preprocessing**
- **Handling Missing Values**:
  - Numerical columns: Filled with mean, median, or interpolated values.
  - Categorical columns: Filled with mode or random values based on class distribution.
  - Best combination: **Mean (numerical) + Random (categorical)**.

- **Encoding Categorical Variables**:
  - Methods: One-hot encoding and label encoding.
  - Best performance: **One-hot encoding**.

- **Scaling**:
  - Standardization (mean=0, std=1).
  - Normalization (scaled between 0 and 1).
  - Best method: **Normalization**.

- **Feature Extraction**:
  - Principal Component Analysis (PCA).
  - Linear Discriminant Analysis (LDA).
  - Results: Neither method improved AUC scores, suggesting no significant multicollinearity in the data.

### **2. Model Development**
- **Algorithms Used**:
  - Logistic Regression
  - Support Vector Machine (SVM)
  - K-Nearest Neighbors (KNN)
  - Multi-Layer Perceptron (MLP)
  - Random Forest
  - XGBoost
  - Ensemble Model (combining multiple algorithms)

- **Hyperparameter Tuning**:
  - Grid Search
  - Randomized Search

### **3. Scoring and Validation**
- **Cross-Validation**:
  - Stratified K-Fold (k=10) to ensure robust evaluation.

---

## **Results**

### **Best Models**
- **For H1N1 Vaccine Prediction**:
  - **Best Model**: XGBoost
  - **AUC Score**: **0.8668**
  - XGBoost consistently provided the highest AUC score for this target variable due to its superior handling of structured data.

- **For Seasonal Vaccine Prediction**:
  - **Best Model**: Ensemble Model
  - **AUC Score**: **0.8588**
  - The ensemble approach outperformed XGBoost for this target variable, indicating that combining multiple models improved generalization.

### **Overall Performance Comparison**
| Model              | H1N1 AUC Score | Seasonal AUC Score |
|--------------------|----------------|--------------------|
| XGBoost           | 0.8668         | 0.8568            |
| Ensemble Model     | 0.8530         | 0.8588            |