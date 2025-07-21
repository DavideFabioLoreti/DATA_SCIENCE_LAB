# Predictive Analytics for Pension Preparedness

**Data Science Lab Project – Master's Degree in Data Science**  
**Università degli Studi di Milano - Bicocca**  
**Author**: Davide Fabio Loreti  

## Overview

This project develops a comprehensive machine learning framework for customer segmentation in the Italian insurance market, focusing on pension preparedness assessment. Using financial literacy data from a national banking survey, the analysis identifies customers at high risk of inadequate pension preparation to support targeted educational campaigns and personalized product offerings.

The analysis combines:
- **Advanced Feature Engineering** with demographic and behavioral indicators
- **Class Imbalance Handling** optimized for minority class detection  
- **Dynamic Threshold Optimization** for business-specific performance targets
- **Multi-Algorithm Evaluation** across different operational scenarios

---

## Objectives

- Develop a binary classification system to identify customers with low financial literacy
- Engineer sophisticated features capturing complex financial behavior patterns
- Compare multiple machine learning algorithms with comprehensive trade-off analysis
- Implement dynamic threshold optimization prioritizing target segment identification
- Provide quantitative insights for insurance business strategy without prescriptive recommendations

---

## Dataset Description

- **Source**: 2023 IACOFI (International Adult Competency Framework on Financial Inclusion) survey
- **Sample size**: 4,553 individuals (after data cleaning from 4,862 original observations)
- **Variables**: 29 carefully selected features from 219 original variables including:
 - Personal and demographic characteristics (Gender, Age, Geographic Area)
 - Employment and income (Work Sector, Income Bracket)
 - Financial behavior and responsibility patterns
 - Financial resilience and stress indicators
 - Economic vulnerability measures
- **Target Distribution**: 77% High Financial Literacy, 23% Low Financial Literacy

---

## Methodology

### Preprocessing Pipeline
- **Target Transformation**: 5-point financial literacy scale → binary classification (1-2: Low FL, 3-5: High FL)
- **Advanced Feature Engineering**: Multi-layered approach generating 29 variables including:
 - Age segmentation (Very Young, Young Adult, Middle Age, Senior)
 - Financial responsibility indicators (sole vs. shared management)
 - Composite features (Education_Income_Ratio, Financial_Stress_Score)
 - Strategic interactions (Young_High_Ed, Senior_High_Income)
- **Feature Selection**: Two-stage pipeline (SelectKBest → RFE) reducing 32 → 20 optimal features
- **Class Balancing**: SMOTE (k=3, 90% target) + Conservative UnderSampling (1.05:1 ratio)

### Machine Learning Models
- **XGBoost Balanced**: `n_estimators=180, max_depth=4, learning_rate=0.07`
- **Random Forest**: `n_estimators=250, max_depth=9, max_features='sqrt'`  
- **Logistic Regression**: Aggressive class weighting (3.0:1 ratio)
- **Gradient Boosting**: `n_estimators=150, learning_rate=0.08`
- **Ensemble Voting**: Probabilistic combination with optimized thresholds

**Evaluation Metrics**:
- Test Accuracy
- Low FL Recall (primary target metric)
- Precision and F1-score
- Cross-validation stability
- Custom composite scoring function

### Dynamic Threshold Optimization
Custom scoring prioritizing minority class identification:
Score = 0.8 × Sensitivity_class_0 + 0.15 × Accuracy + 0.05 × Specificity  (TN ≥ 150)
= 0.7 × Sensitivity_class_0 + 0.2 × Accuracy + 0.1 × Specificity   (TN ≥ 120)
= 0.4 × Sensitivity_class_0 + 0.3 × Accuracy + 0.3 × Specificity   (otherwise)
**Best Performance by Scenario**:
- **Target Coverage**: Logistic Regression (97.6% recall, Custom Score: 0.866)
- **Balanced Trade-off**: Random Forest (77.1% recall, 42.3% accuracy)
- **Overall Accuracy**: Gradient Boosting (60.9% accuracy, 43.3% recall)

---

## Results

| Model | Test Accuracy | Low FL Recall | Precision | True Negatives | Optimal Threshold |
|-------|---------------|---------------|-----------|----------------|-------------------|
| Logistic Regression | 24.4% | **97.6%** | 23.1% | **205** | 0.69 |
| Random Forest | 42.3% | 77.1% | 25.3% | 162 | 0.42 |
| Ensemble Voting | 40.6% | 75.2% | 24.4% | 158 | 0.31 |
| XGBoost | **55.5%** | 48.1% | 25.4% | 101 | 0.31 |
| Gradient Boosting | **60.9%** | 43.3% | **27.7%** | 91 | 0.28 |

### Strategic Trade-offs Analysis
- **Target Coverage-Oriented**: Maximum minority class identification (97.6% recall) with broader targeting implications
- **Balanced Trade-off**: Intermediate performance balancing coverage and precision (75-77% recall)  
- **Accuracy-Oriented**: Highest overall classification accuracy (55-61%) with reduced target coverage

---

## Conclusion

The experimental analysis demonstrates distinct algorithmic approaches for customer segmentation in financial literacy identification, each associated with different performance profiles suitable for varying business priorities and operational constraints. The framework provides a comparative basis for deployment decisions across three strategic orientations: target coverage maximization, balanced trade-offs, and overall accuracy optimization.

Key findings:
- Dynamic threshold optimization enables performance-based metric weighting aligned with business objectives
- Feature selection reduced dimensionality while maintaining predictive utility across all algorithms
- Class imbalance handling through combined SMOTE and undersampling improved minority class detection
- Cross-validation confirmed model stability and reproducibility

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
