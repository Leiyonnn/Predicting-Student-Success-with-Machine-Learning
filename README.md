# Predicting Student Success with Machine Learning

A third-year group project at **City, University of London** applying data science and predictive analytics to the **Open University Learning Analytics Dataset (OULAD)**.

---

## Project Overview
Learning Analytics leverages educational data to understand student behavior and optimize learning outcomes. In this project, we predict student success (Pass, Fail, Distinction, or Withdrawn) using early-course activity and demographic indicators. 

By analyzing interactions during the first half of a course, the goal is to build predictive models that enable timely academic interventions for at-risk students.

---

## Dataset
This project utilizes the **Open University Learning Analytics Dataset (OULAD)**, which includes data on courses, student demographics, Virtual Learning Environment (VLE) engagement logs, and assessment scores across 32,593 students.

The pipeline processes and aggregates data across seven relational CSV tables:
- `studentInfo.csv` — Demographics & final results
- `studentRegistration.csv` — Registration & unregistration dates
- `studentAssessment.csv` & `assessments.csv` — Assessment scores and weights
- `studentVle.csv` & `vle.csv` — Clickstream interactions in the VLE
- `courses.csv` — Course modules and presentation lengths

---

## Workflow & Methodology

### 1. Data Cleaning & Preprocessing
- **Missing Value Imputation:** Handled missing data logically across tables (e.g., median imputation for registration dates, filling missing assessment scores with `0` to denote non-submission, and setting missing VLE click counts to `0`).
- **Deduplication:** Filtered data to retain each student's latest course attempt to remove redundant records.

### 2. Feature Engineering (First-Half Activity Window)
To ensure practical early-warning predictions, features were engineered strictly using data from the **first half** of each module presentation:
- **`score`**: Mean assessment score accumulated in the first half.
- **`weight`**: Total weight of completed assessments in the first half.
- **`sum_click`**: Aggregated VLE interaction clicks up to the module halfway point.

### 3. Model Development & Evaluation
We built and evaluated multiple machine learning models using `scikit-learn`:
- **Logistic Regression**
- **Decision Trees**
- **Random Forest**
- **Gradient Boosting**
- **Support Vector Machines (SVM)**

### Evaluation Metrics
Models were assessed using standard classification performance metrics:
- **Accuracy**
- **Precision**
- **Recall**
- **F1-Score**
- **ROC-AUC Curves** (Evaluating trade-offs between True Positive Rate and False Positive Rate)

---
