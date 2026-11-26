# Diabetes Prediction System

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![Scikit-learn](https://img.shields.io/badge/Library-scikit--learn-orange.svg)](https://scikit-learn.org/)

An end-to-end machine learning project for estimating diabetes or prediabetes risk using the **CDC BRFSS 2015 health survey dataset**. The notebook covers exploratory data analysis, preprocessing, model comparison, threshold tuning, fairness analysis, and an interactive-style risk-flagging example.

> **Disclaimer:** This project is for educational and research purposes only. It is not a medical diagnostic tool and must not replace advice from a qualified healthcare professional.

## Overview

The project builds a binary classification pipeline with the following target:

- `0` — No diabetes
- `1` — Prediabetes or diabetes

The workflow uses 253,680 survey records and 21 predictors related to blood pressure, cholesterol, BMI, lifestyle, general health, physical health, demographics, education, and income.

## Key Features

- Exploratory data analysis and descriptive statistics
- Missing-value and duplicate-record checks
- Stratified 80/20 train-test split
- Leakage-safe preprocessing with scikit-learn pipelines
- Comparison of Logistic Regression, Random Forest, and Linear SVM
- Out-of-fold probability or decision-score generation
- Classification-threshold tuning for recall and precision
- ROC-AUC and PR-AUC evaluation
- Confusion matrices and classification reports
- Fairness checks across demographic groups
- Raw-input validation and non-diagnostic risk flagging demo

## Dataset

The notebook uses the **CDC Diabetes Health Indicators (BRFSS 2015)** dataset from the UCI Machine Learning Repository.

- Records: 253,680
- Features: 21 predictors
- Target: `Diabetes_binary`
- Source file expected by the notebook:

```text
diabetes_binary_health_indicators_BRFSS2015.csv
```

Example predictors include `HighBP`, `HighChol`, `BMI`, `Smoker`, `PhysActivity`, `GenHlth`, `DiffWalk`, `Sex`, `Age`, `Education`, and `Income`.

## Project Structure

```text
.
├── Diabetes_Prediction_System_ashik.ipynb
├── LICENSE
└── README.md
```

The CSV dataset is not stored in this repository and must be downloaded separately or made available in the notebook environment.

## Notebook Workflow

1. **Data loading and understanding** — Inspect shape, types, summary statistics, missing values, and duplicates.
2. **Exploratory data analysis** — Explore distributions and relationships among health indicators and the target.
3. **Feature preparation** — Separate predictors from `Diabetes_binary` and create a stratified train-test split.
4. **Preprocessing** — Standardize features within a scikit-learn pipeline.
5. **Model development** — Train Logistic Regression, Random Forest, and Linear SVC models.
6. **Threshold tuning** — Generate out-of-fold training predictions and select a decision threshold that improves recall while considering precision.
7. **Model evaluation** — Compare accuracy, precision, recall, F1-score, ROC-AUC, PR-AUC, and confusion matrices.
8. **Fairness evaluation** — Review subgroup performance to identify potentially uneven outcomes.
9. **Risk demo** — Validate raw user inputs and produce a probability-based risk flag.

## Models and Metrics

The notebook compares the following classifiers:

- Logistic Regression
- Random Forest Classifier
- Linear Support Vector Classifier

Evaluation includes:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- PR-AUC
- Confusion matrix
- Classification report
- ROC and Precision-Recall curves

Because the positive class is imbalanced, recall and PR-AUC should be considered alongside accuracy when interpreting model performance.

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/zenithashikk/diabetes-prediction-ml-ashik-mahmud.git
cd diabetes-prediction-ml-ashik-mahmud
```

### 2. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### 3. Add the dataset

Download the **CDC Diabetes Health Indicators (BRFSS 2015)** CSV dataset and place it in the repository directory with the filename used by the notebook:

```text
diabetes_binary_health_indicators_BRFSS2015.csv
```

### 4. Run the notebook

```bash
jupyter notebook Diabetes_Prediction_System_ashik.ipynb
```

You can also open the notebook in Google Colab or another Jupyter-compatible environment.

## Important Considerations

- Survey-derived estimates may not generalize to all populations.
- The model may exhibit false positives and false negatives.
- Threshold tuning changes the balance between recall and precision.
- Fairness results should be interpreted carefully because performance differences can reflect data quality, sampling, representation, and social conditions.
- The feature set is not a complete clinical assessment, and the output should not be used for diagnosis.

## License

This project is licensed under the [MIT License](LICENSE).

## Author

**Ashik Mahmud**

## References

- [CDC Behavioral Risk Factor Surveillance System (BRFSS)](https://www.cdc.gov/brfss/)
- [UCI Machine Learning Repository — CDC Diabetes Health Indicators](https://archive.ics.uci.edu/dataset/891/cdc+diabetes+health+indicators)
