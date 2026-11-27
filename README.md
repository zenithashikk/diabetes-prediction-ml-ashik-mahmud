# Diabetes Prediction System

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![scikit-learn](https://img.shields.io/badge/Library-scikit--learn-orange.svg)](https://scikit-learn.org/)

An end-to-end machine learning project for estimating diabetes or prediabetes risk using the **CDC BRFSS 2015 Health Indicators dataset**. The project explores the data, compares multiple classifiers, tunes a decision threshold, evaluates model performance, and conducts subgroup fairness checks.

> **Disclaimer:** This project is for educational and research purposes only. It is not a medical diagnostic tool and must not replace advice from a qualified healthcare professional.

## Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Project Workflow](#project-workflow)
- [Models and Evaluation](#models-and-evaluation)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Running the Notebook](#running-the-notebook)
- [Results and Interpretation](#results-and-interpretation)
- [Limitations](#limitations)
- [License](#license)
- [Author](#author)
- [References](#references)

## Overview

This notebook builds a binary classification pipeline to identify survey respondents with diabetes or prediabetes from 21 health, lifestyle, and demographic indicators.

The target variable is `Diabetes_binary`:

- `0` — No diabetes
- `1` — Prediabetes or diabetes

The full workflow includes exploratory data analysis, missing-value and duplicate checks, stratified train-test splitting, leakage-safe preprocessing, model comparison, threshold tuning, fairness evaluation, and a raw-input risk flagging demonstration.

## Dataset

The project uses the **CDC Diabetes Health Indicators** dataset derived from the 2015 Behavioral Risk Factor Surveillance System (BRFSS) and made available through the UCI Machine Learning Repository.

| Property | Value |
|---|---|
| Records | 253,680 |
| Columns | 22 |
| Predictors | 21 |
| Target | `Diabetes_binary` |
| Missing values | None detected |
| Duplicate rows | 24,206 |

Example predictors include:

- `HighBP` — high blood pressure
- `HighChol` — high cholesterol
- `BMI` — body mass index
- `Smoker` — smoking history
- `PhysActivity` — physical activity
- `GenHlth` — general health rating
- `MentHlth` — days of poor mental health
- `PhysHlth` — days of poor physical health
- `DiffWalk` — difficulty walking
- `Sex`, `Age`, `Education`, and `Income`

The CSV is not stored in this repository. Download it and place it in the repository root with the following name:

```text
diabetes_binary_health_indicators_BRFSS2015.csv
```

## Project Workflow

1. **Data loading** — Import the BRFSS CSV and inspect its shape, types, and first rows.
2. **Data understanding** — Check summary statistics, missing values, and duplicate records.
3. **Exploratory data analysis** — Visualize distributions, correlations, and relationships with the target.
4. **Train-test split** — Use an 80/20 stratified split to preserve class proportions.
5. **Preprocessing** — Standardize predictors through scikit-learn pipelines to prevent training-data leakage.
6. **Model development** — Train Logistic Regression, Random Forest, and Linear SVM classifiers.
7. **Threshold tuning** — Generate out-of-fold predictions and tune the decision threshold to improve recall while considering precision.
8. **Model evaluation** — Compare accuracy, precision, recall, F1-score, ROC-AUC, PR-AUC, and confusion matrices.
9. **Fairness analysis** — Measure subgroup performance across demographic groups.
10. **Risk demo** — Validate raw inputs and return a probability-based, non-diagnostic risk flag.

## Models and Evaluation

The following classifiers are compared:

| Model | Purpose |
|---|---|
| Logistic Regression | Interpretable linear baseline |
| Random Forest Classifier | Nonlinear ensemble baseline |
| Linear Support Vector Classifier | Margin-based linear classifier |

The evaluation includes:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Precision-Recall AUC
- Confusion matrix
- Classification report
- ROC curve
- Precision-Recall curve
- Cross-validated out-of-fold predictions
- Demographic subgroup analysis

Because the positive class is much less frequent than the negative class, accuracy alone is not sufficient. Recall and PR-AUC should be considered together with precision and false-positive costs.

## Project Structure

```text
.
├── Diabetes_Prediction_System_ashik.ipynb
├── "Diabetes Prediction System Report Summary.pdf"
├── LICENSE
├── README.md
└── requirements.txt
```

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/zenithashikk/diabetes-prediction-ml-ashik-mahmud.git
cd diabetes-prediction-ml-ashik-mahmud
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate it on macOS or Linux:

```bash
source .venv/bin/activate
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Add the dataset

Download the CDC Diabetes Health Indicators dataset and place `diabetes_binary_health_indicators_BRFSS2015.csv` in the repository root.

## Running the Notebook

Start Jupyter Notebook:

```bash
jupyter notebook Diabetes_Prediction_System_ashik.ipynb
```

Alternatively, open the notebook in Google Colab or another Jupyter-compatible environment and ensure the CSV file is mounted or uploaded to the working directory.

## Results and Interpretation

The notebook compares classifiers on a held-out test set and examines the effect of changing the classification threshold. Threshold tuning is especially important for imbalanced medical-risk datasets:

- A lower threshold generally increases recall but may also increase false positives.
- A higher threshold generally increases precision but may miss more positive cases.
- The appropriate threshold depends on the use case and the relative cost of false positives and false negatives.

Always review ROC-AUC, PR-AUC, confusion matrices, subgroup metrics, and the full classification report rather than relying on accuracy alone.

## Limitations

- The dataset is derived from a cross-sectional self-reported survey.
- Population-level survey estimates may not generalize to individual patients or other populations.
- The target combines prediabetes and diabetes into one positive class.
- Duplicate records and class imbalance require careful interpretation.
- Fairness gaps may reflect data quality, sampling, representation, or social conditions.
- The model cannot capture every clinical factor relevant to diabetes risk.
- Outputs should not be used for diagnosis or to replace clinical screening.

## License

This project is licensed under the [MIT License](LICENSE).

## Author

**Ashik Mahmud**

## References

- [CDC — Behavioral Risk Factor Surveillance System](https://www.cdc.gov/brfss/)
- [UCI Machine Learning Repository — CDC Diabetes Health Indicators](https://archive.ics.uci.edu/dataset/891/cdc+diabetes+health+indicators)
- [Scikit-learn Documentation](https://scikit-learn.org/stable/)
