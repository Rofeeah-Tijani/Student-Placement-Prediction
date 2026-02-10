
# Student Placement Prediction Using Machine Learning

## Overview
This project aims to predict whether a student will receive a job placement based on their academic, cognitive, and extracurricular attributes.  
The target variable is **Placement**, which is categorized into two: Yes/No

---

## Dataset Description

The dataset contains **10,000 student records** with the following features:

| Feature Name | Description |
|--------------|-------------|
| College_ID | Unique identifier for each student |
| IQ | Cognitive ability score |
| Prev_Sem_Result | Previous semester academic result |
| CGPA | Cumulative Grade Point Average |
| Academic_Performance | Overall academic performance score |
| Internship_Experience | Whether the student has internship experience |
| Extra_Curricular_Score | Participation in extracurricular activities |
| Communication_Skills | Communication skill rating |
| Projects_Completed | Number of academic/projects completed |
| Placement | **Target variable** |

The dataset was split into **training** (8,000 samples) and **testing** (2,000 samples).

---

## Objective
To build a machine learning model that predicts whether a student will get a placement based on the given features.

---

## Methodology

### 1. Data Preparation
- Features (`X`) and target (`y`) were separated
- Dataset was split into **training** (80%) and **testing** (20%) sets
- Categorical variables was encoded 

---

### 2. Decision Tree Classifier

- A **Decision Tree** classifier was trained first because it is simple and interpretable.
- **Results on the test set (2,000 samples):**

**Accuracy:** `1.0`  

**Confusion Matrix:**
[[1674 0]
[ 0 326]]


**Classification Report:**

| Class | Precision | Recall | F1-score | Support |
|-------|-----------|--------|----------|---------|
| No    | 1.00      | 1.00   | 1.00     | 1674    |
| Yes   | 1.00      | 1.00   | 1.00     | 326     |
| **Accuracy** | - | - | 1.00 | 2000 |
| **Macro Avg** | 1.00 | 1.00 | 1.00 | 2000 |
| **Weighted Avg** | 1.00 | 1.00 | 1.00 | 2000 |

**Observation:**  
- Perfect accuracy suggests the model may be **overfitting**, memorizing training data rather than generalizing patterns.

---

### 3. Random Forest Classifier

- To reduce overfitting, trained a **Random Forest** classifier:
```python
RandomForestClassifier(
    max_depth=5,
    min_samples_leaf=10,
    random_state=42
)
Test Set Results (2,000 samples):

Accuracy: 0.999

Confusion Matrix:

### Classification Report

| Class | Precision | Recall | F1-score | Support |
|------|-----------|--------|----------|---------|
| No | 1.00 | 1.00 | 1.00 | 1674 |
| Yes | 1.00 | 0.99 | 1.00 | 326 |
| **Accuracy** | - | - | **0.999** | **2000** |
| **Macro Avg** | 1.00 | 1.00 | 1.00 | 2000 |
| **Weighted Avg** | 1.00 | 1.00 | 1.00 | 2000 |

-----

Observation:

Only 2 samples misclassified, showing improved robustness while retaining high accuracy.

Random Forest reduces overfitting compared to a single Decision Tree.


-----

Conclusion

Decision Tree achieved perfect accuracy on the test set but is prone to overfitting.

Random Forest maintained near-perfect accuracy while improving generalization.

Features in this dataset are highly predictive of student placement.
