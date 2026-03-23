# The “Gulliver Score”: Modelling Cumulative Subclinical Cardiovascular Risk

Modelling cumulative cardiovascular risk using a composite “Gulliver Score” and machine learning to identify subclinical disease patterns.

---

## Abstract
Cardiovascular disease (CVD) risk is traditionally assessed using discrete clinical thresholds. However, emerging evidence suggests that multiple mildly abnormal cardiovascular risk factors (CVRFs), even within non-pathological ranges, can synergistically elevate disease risk [1].

This project operationalises the *Gulliver syndrome* framework by constructing a quantitative **Gulliver Score** and evaluating its ability to capture cumulative cardiovascular risk. Using a large-scale dataset (~70,000 individuals) [2], we demonstrate that aggregated subclinical abnormalities show a strong monotonic relationship with cardiovascular disease and improve predictive modelling performance.

---

## Introduction
Preventive cardiology has historically relied on binary diagnostic thresholds (e.g., hypertension, diabetes). However, cardiovascular pathophysiology exists on a continuum, where modest elevations in multiple variables can interact to accelerate disease progression.

The **Gulliver syndrome** describes individuals with multiple borderline abnormalities that collectively generate significant cardiovascular risk despite the absence of overt disease.

These individuals are often underdiagnosed due to *therapeutic inertia*, where no single variable exceeds clinical thresholds.

### Aim
This study aims to:
- Translate the Gulliver syndrome into a **data-driven composite score**
- Quantify cumulative cardiovascular risk
- Evaluate predictive performance using machine learning
- Assess whether combined subclinical factors outperform individual predictors

---

## Methods

### Dataset
- ~68,000 patient records (after cleaning)  
- Features include:
  - Age  
  - BMI  
  - Blood pressure (`ap_hi`, `ap_lo`)  
  - Cholesterol  
  - Cardiovascular outcome (`cardio`)  

---

### Feature Engineering: Gulliver Score
The **Gulliver Score** was constructed by assigning risk levels to:

- Systolic blood pressure  
- BMI  
- Cholesterol  

These were aggregated into a composite score representing **cumulative subclinical burden**, consistent with the Gulliver syndrome hypothesis.

---

### Data Cleaning
Physiologically implausible values (e.g., negative blood pressure, extreme BMI) were removed to ensure biological plausibility and numerical stability.

---

### Exploratory Data Analysis
- Correlation matrix  
- KDE distributions  
- Pairwise multivariate analysis  

---

### Machine Learning Models
- Logistic Regression  
- Random Forest  

Evaluation metrics:
- Accuracy  
- ROC Curve (AUC)  
- Cross-validation  

---

## Results

### Multivariate Risk Structure
Pairwise analysis revealed that cardiovascular risk emerges from **combined moderate elevations across multiple variables**, rather than isolated extremes.

- Age and BMI show clear distributional shifts  
- Systolic blood pressure demonstrates strong separation  
- The **Gulliver Score shows the clearest monotonic relationship**

---

### Cumulative Risk (Key Finding)

| Gulliver Score | Cardiovascular Risk |
|---------------|--------------------|
| 0 | 0.17 |
| 1 | 0.30 |
| 2 | 0.45 |
| 3 | 0.61 |
| 4 | 0.78 |
| 5+ | >0.80 |


---

### Model Performance

| Model | Accuracy | AUC |
|------|--------|-----|
| Logistic Regression | 0.73 | 0.79 |
| Random Forest | 0.70 | 0.76 |

Logistic regression slightly outperformed Random Forest, suggesting that cardiovascular risk is largely **linear and additive**, consistent with cumulative risk modelling.

---

### Cross-Validation
- Random Forest mean AUC: ~0.75  
- Logistic Regression mean AUC: ~0.79  

These results confirm **stable and robust performance across folds**.

---

## Discussion
Findings support the Gulliver syndrome framework:

- Cardiovascular risk is **cumulative rather than binary**  
- Multiple borderline variables act synergistically  
- Composite scoring improves interpretability and prediction  

Importantly, results highlight limitations of traditional threshold-based diagnosis, which may fail to detect early high-risk individuals.

---

## Conclusion
This study demonstrates that cardiovascular risk is driven by the **accumulation of mildly abnormal variables**, rather than single pathological thresholds.

The **Gulliver Score** provides a simple, interpretable, and clinically relevant approach for early risk detection, supporting a shift toward **continuous and multifactorial risk assessment**.

---

## Future Work
- Validation using NHS or longitudinal datasets  
- Integration with wearable health data  
- Inclusion of glucose and waist circumference  
- Development of clinical decision-support tools  

---

## Tech Stack
- Python (Pandas, NumPy)  
- Scikit-learn  
- Seaborn / Matplotlib  

---

## Key Insight
> Cardiovascular disease is not caused by a single abnormality, but by the accumulation of many small imbalances acting together.

---

## References
[1] López-Gil, J. F., Abellán-Huerta, J., & Abellán-Alemán, J. (2025). The Gulliver syndrome: a conceptual framework to address therapeutic inertia in patients with borderline cardiovascular risk profiles. *Frontiers in Cardiovascular Medicine*, 12, 1652447. https://doi.org/10.3389/fcvm.2025.1652447  

[2] Sulianova, S. (2018). *Cardiovascular disease dataset* [Data set]. Kaggle. https://www.kaggle.com/datasets/sulianova/cardiovascular-disease-dataset  

---

## Author
**Francisca Valenzuela-Mella**  
MSc Health Data Science | Computational Biology & Multi-omics  

ORCID: 0009-0002-0187-5880
