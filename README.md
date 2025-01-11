# Bias Mitigation in Healthcare AI: Disease Diagnosis

This project aims to assess and mitigate biases in predictive models for disease diagnosis, with a focus on fairness across different demographic groups (e.g., age, gender, ethnicity). The goal is to build a machine learning model that predicts diseases (e.g., diabetes) and evaluates its fairness across multiple demographic groups.

## Table of Contents

- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Steps Involved](#steps-involved)
- [Fairness Metrics](#fairness-metrics)
- [Bias Mitigation Techniques](#bias-mitigation-techniques)
- [Performance Evaluation](#performance-evaluation)
- [Results](#results)
- [Future Work](#future-work)

## Project Overview

The project focuses on training a machine learning model to predict diseases (e.g., diabetes) using a publicly available dataset and evaluating fairness across different demographic groups (such as age). We apply techniques to mitigate bias in the model using fairness constraints and measure performance using several fairness metrics.

## Dataset

The dataset used in this project is the **Pima Indians Diabetes Database**, which contains the following features:

- `Pregnancies`: Number of pregnancies
- `Glucose`: Plasma glucose concentration
- `BloodPressure`: Diastolic blood pressure
- `SkinThickness`: Triceps skinfold thickness
- `Insulin`: 2-Hour serum insulin
- `BMI`: Body mass index
- `DiabetesPedigreeFunction`: A function that scores likelihood of diabetes based on family history
- `Age`: Age of the patient
- `Outcome`: Whether the patient has diabetes (1) or not (0)

The dataset was split into training and testing sets, and we created an additional **AgeGroup** feature to divide the data into two groups: age <= 30 and age > 30.

## Steps Involved

1. **Data Preprocessing**:
   - Load and clean the dataset.
   - Handle missing values.
   - Create additional demographic features (e.g., AgeGroup).

2. **Model Training**:
   - Split the dataset into training and testing sets.
   - Train a classification model (e.g., Decision Tree) using the training set.

3. **Fairness Evaluation**:
   - Evaluate the model's fairness across demographic groups (Age <= 30 vs. Age > 30).
   - Measure fairness using key metrics like **Demographic Parity** and **Equal Opportunity**.

4. **Bias Mitigation Techniques**:
   - **Reweighting**: Assign different weights to training samples based on their demographic group to reduce bias.
   - **Fairness Constraints**: Introduce fairness constraints during model training to ensure balanced performance across groups.

5. **Hyperparameter Tuning**:
   - Optimize model performance using cross-validation and grid search to find the best hyperparameters while maintaining fairness.

## Fairness Metrics

The following fairness metrics were used to evaluate the model's fairness across demographic groups:

- **Demographic Parity**: Measures whether the positive prediction rate is equal across groups.
- **Equal Opportunity**: Measures whether the true positive rate is equal across groups.
- **Equalized Odds**: Measures whether both the true positive rate and false positive rate are equal across groups.

## Bias Mitigation Techniques

We applied two primary bias mitigation techniques:

1. **Reweighting**:
   - This method involves adjusting the weight of each sample in the training set to ensure that the model's predictions are fairer. The weights are calculated based on demographic groups.

2. **Fairness Constraints**:
   - By integrating fairness constraints into the model training process, we enforced equality between different demographic groups. This was achieved through **Fairlearn**'s adversarial debiasing.

## Performance Evaluation

The model was evaluated using the following metrics:

- **Accuracy**: The percentage of correct predictions.
- **Confusion Matrix**: To understand the number of true positives, false positives, true negatives, and false negatives.
- **Classification Report**: To assess precision, recall, and F1-score for each class (diabetes/no diabetes).

We also assessed the model's fairness by comparing demographic parity and equal opportunity differences between age groups before and after applying bias mitigation techniques.

## Results

The model achieved the following results:

- **Accuracy (Unbalanced Model)**: 75.32%
- **Accuracy (Reweighted Model)**: 69.48%
- **Accuracy with Fairness Constraints**: 70.13%

The fairness metrics showed:

- **Demographic Parity** (Age <= 30) without resampling: 0.3701, with fairness constraints: 0.4545
- **Equal Opportunity** (Age <= 30) without resampling: 0.6727, with fairness constraints: 0.7091

**Conclusion**: The fairness interventions improved the balance between age groups in terms of recall and equal opportunity. The model's accuracy slightly decreased when applying fairness constraints, but fairness metrics improved significantly.

## Future Work

- **Exploring Other Bias Mitigation Techniques**: Other methods like adversarial debiasing or reweighting can be further explored.
- **Model Explainability**: Implement model interpretability to provide transparent insights into the model’s predictions (e.g., using SHAP or LIME).
- **Deployment**: Deploy the model in a real-world healthcare application to predict and monitor diseases while ensuring fairness.
