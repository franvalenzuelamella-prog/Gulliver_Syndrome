# Gulliver_Syndrome
Modelling cumulative cardiovascular risk using a composite “Gulliver Score” and machine learning to identify subclinical disease patterns.

# The “Gulliver Score”: Modelling Cumulative Subclinical Cardiovascular Risk

## Abstract
Cardiovascular disease (CVD) risk is traditionally assessed using discrete clinical thresholds. However, emerging evidence suggests that multiple mildly abnormal cardiovascular risk factors (CVRFs), even within non-pathological ranges, can synergistically elevate disease risk. [1]

This project operationalises the recently proposed *Gulliver syndrome* framework by constructing a quantitative **Gulliver Score** and evaluating its ability to capture cumulative cardiovascular risk. Using a large-scale patient dataset (~70,000 individuals)[2], we demonstrate that aggregated subclinical abnormalities show a strong monotonic relationship with cardiovascular disease and improve predictive modelling performance.

---

## Introduction
Preventive cardiology has historically relied on binary diagnostic thresholds (e.g., hypertension, diabetes). However, cardiovascular pathophysiology exists on a continuum, where even modest elevations in blood pressure, glucose, or lipid levels can interact and accelerate disease progression. 

The **Gulliver syndrome** has been proposed as a conceptual framework to describe individuals with multiple borderline abnormalities that, collectively, generate significant cardiovascular risk despite the absence of overt disease. 

These patients are often underdiagnosed due to *therapeutic inertia*, where no single variable exceeds clinical thresholds. 

### Aim
This study aims to:
- Translate the Gulliver syndrome into a **data-driven composite score**
- Quantify cumulative cardiovascular risk
- Evaluate predictive performance using machine learning
- Explore whether multiple subclinical factors outperform individual predictors

---

## Methods

### Dataset
- ~70,000 patient records  
- Features include:
  - Age  
  - BMI  
  - Blood pressure (`ap_hi`, `ap_lo`)  
  - Cholesterol  
  - Lifestyle indicators  
  - Cardiovascular outcome (`cardio`)  

---

### Feature Engineering: Gulliver Score
Inspired by clinical criteria proposed in the literature, the Gulliver Score was constructed by assigning risk levels to:

- Blood pressure (systolic)
- BMI (proxy for adiposity)
- Cholesterol levels

These were aggregated into a composite score representing **cumulative subclinical burden**, consistent with the syndrome’s definition of multiple mildly abnormal CVRFs acting synergistically. 

---

### Exploratory Data Analysis
- Correlation matrix  
- Distribution analysis (KDE)  
- Pairwise KDE visualisation  

---

### Machine Learning Models
- Logistic Regression  
- Random Forest  

Evaluation metrics:
- Accuracy  
- Precision / Recall  
- ROC Curve (AUC)  

---

## Results

### Multivariate Risk Structure
Pairwise KDE analysis revealed that cardiovascular risk emerges from **interactions between multiple variables**, rather than isolated extremes.

- Age and BMI showed strong distributional shifts  
- Blood pressure and cholesterol displayed progressive risk gradients  
- The **Gulliver Score exhibited clear monotonic separation**

---

### Cumulative Risk (Key Finding)
| Gulliver Score | Cardiovascular Risk |
|---------------|--------------------|
| 0 | 0.17 |
| 1 | 0.30 |
| 2 | 0.45 |
| 3 | 0.60 |
| 4 | 0.78 |
| 5+ | >0.80 |

👉 Risk increases **non-linearly and cumulatively**, supporting the Gulliver hypothesis.

---

### Model Performance
| Model | Accuracy | AUC |
|------|--------|-----|
| Logistic Regression | ~0.72 | ~0.79 |
| Random Forest | ~0.69 | ~0.75 |

Logistic regression slightly outperformed Random Forest, suggesting that aggregated risk behaves in a **structured, near-linear manner**.

---

## Discussion
Our findings provide empirical support for the Gulliver syndrome framework, demonstrating that:

- Cardiovascular risk is **distributed and cumulative**, not binary  
- Multiple borderline variables interact synergistically  
- A composite score captures risk better than individual features  

This aligns with prior evidence that even sub-threshold elevations in CVRFs contribute to endothelial dysfunction, inflammation, and long-term cardiovascular disease progression. :contentReference[oaicite:5]{index=5}  

Importantly, the results highlight the limitation of current clinical thresholds, which may fail to identify high-risk individuals in early stages.

---

## Conclusion
This study demonstrates that the aggregation of mildly abnormal cardiovascular risk factors significantly increases disease risk, even when individual variables remain within normal ranges.

The **Gulliver Score** provides a simple, interpretable, and clinically relevant tool for early risk detection, supporting a shift toward **continuous and multifactorial risk assessment**.

---

## Future Work
- Validation using NHS or longitudinal datasets  
- Integration with wearable health data  
- Development of clinical decision-support tools  
- Incorporation of glucose and waist circumference for full clinical alignment  

---

## Tech Stack
- Python (Pandas, NumPy)  
- Scikit-learn  
- Seaborn / Matplotlib  

---

## Key Insight
> Cardiovascular disease is not caused by a single abnormality, but by the accumulation of many small imbalances acting together.

---
# References
[1] López-Gil, J. F., Abellán-Huerta, J., & Abellán-Alemán, J. (2025). The Gulliver syndrome: a conceptual framework to address therapeutic inertia in patients with borderline cardiovascular risk profiles. Frontiers in cardiovascular medicine, 12, 1652447. https://doi.org/10.3389/fcvm.2025.1652447
[2] Sulianova, S. (2018). Cardiovascular disease dataset [Data set]. Kaggle. https://www.kaggle.com/datasets/sulianova/cardiovascular-disease-dataset
---

## Author
**Francisca Valenzuela-Mella**  
MSc Health Data Science | Computational Biology & Multi-omics  

ORCID: 0009-0002-0187-5880
