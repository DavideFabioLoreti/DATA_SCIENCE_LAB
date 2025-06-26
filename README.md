# Financial Literacy Data Analysis  
**Data Science Lab Project – Master's Degree in Data Science**  
**Università degli Studi di Milano - Bicocca**  
**Author**: Davide Fabio Loreti  
**Date**: June 14, 2025  

## Overview

This project investigates the financial literacy of the Italian adult population using data provided by the Bank of Italy. The goal is to explore demographic and socio-economic patterns and develop predictive models to classify individuals' financial literacy levels.

The analysis combines:
- **Exploratory Data Analysis (EDA)** to understand variable distributions,
- **Supervised Machine Learning** models for classification,
- **Unsupervised Learning** techniques for clustering and segmentation.

---

## Objectives

- Understand the structure of the dataset and clean/preprocess the data.
- Predict gender (used as a proxy target variable) using various ML models.
- Segment the population based on socio-economic features using clustering.
- Identify the best-performing models based on evaluation metrics.
- Provide policy-relevant insights regarding financial literacy.

---

## Dataset Description

- **Source**: Bank of Italy – Financial Literacy Survey
- **Sample size**: 4,862 individuals
- **Variables**: 219 features including:
  - Gender
  - Age
  - Geographic Area
  - Education Level
  - Income Bracket
  - Work Sector
  - Questionnaire Responses (qd5_1, qd5_2, …)

---

## Methodology

### Preprocessing
- Handled missing values (e.g., median imputation for numeric values).
- Label encoding for categorical features with < 50 categories.
- Scaling for models sensitive to magnitude (e.g., SVM, KNN).
- Target variable: **Gender**.

### Supervised Models
- Random Forest  
- Logistic Regression  
- Gradient Boosting  
- SVM  
- Naive Bayes  
- K-Nearest Neighbors  

Metrics used:
- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix
- ROC Curve / AUC

**Best Model**: Gradient Boosting (Accuracy: 94.76%, AUC: 0.98)

### Unsupervised Clustering
- K-Means (with k=2 and k=3)
- DBSCAN
- Gaussian Mixture Model (GMM)
- Spectral Clustering

**Best Clustering Method**: Spectral Clustering (Silhouette Score: 0.452)

---

## Results

- **Supervised Learning**: Gradient Boosting achieved the best classification performance with high interpretability (feature importance analyzed).
- **Clustering**: Spectral Clustering provided the most meaningful segmentation, revealing two distinct socio-economic profiles.
- **Visualization**: PCA was used for dimensionality reduction; multiple plots were used to interpret clusters and model outcomes.

---

## Conclusion

The project effectively integrates supervised and unsupervised learning techniques on socio-economic data. The analysis provides actionable insights into financial literacy segmentation, supporting the development of targeted financial education strategies.

---


## Project Structure

```bash
📁 project/
├── Database.csv/                        # Raw dataset
├── DS LAB PROJECT.ipynb/                # Jupyter notebooks for EDA and modeling
├── DATA SCIENCE LAB PROJECT.pdf/        # PDF of final report
├── variable_description (italian)       # PDF with the descptition variables in Italian
└── README.md                            # This file
```

##  License

This project is developed for academic purposes and is shared under the MIT License.

---
