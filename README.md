# Heart Disease Prediction (Task 3)

## Task Objective
Build a binary classification model to predict whether a patient has heart disease based on clinical health parameters. The goal is to identify high‑risk individuals using a clean, interpretable machine learning pipeline and to compare two different algorithms.

## Dataset Used
**Source:** UCI Heart Disease dataset (Cleveland) – `heart_disease_uci.csv`  
**Samples:** 303 patient records  
**Features:** 13 clinical attributes including age, sex, chest pain type (cp), resting blood pressure (trestbps), cholesterol (chol), maximum heart rate (thalch), ST depression (oldpeak), number of major vessels (ca), etc.  
**Target:** Binary (0 = no heart disease, 1 = presence of heart disease) – derived from the original `num` column.

## Models Applied
| Model | Description | Preprocessing |
|-------|-------------|----------------|
| **Logistic Regression** | Linear classifier, L2 regularization, max_iter=1000 | Feature scaling (StandardScaler) |
| **Decision Tree** | Non‑linear tree with max_depth=5 to avoid overfitting | No scaling, handles mixed data types |

## Key Results and Findings

### Model Performance
| Metric | Logistic Regression | Decision Tree (depth=5) |
|--------|---------------------|--------------------------|
| **Test Accuracy** | ~0.85 – 0.88 | ~0.82 – 0.85 |
| **ROC‑AUC** | > 0.90 | > 0.88 |
| **Training Accuracy** | ~0.86 | ~0.90 |

*Exact values may vary slightly due to random split, but both models show strong discriminative ability.*

### Feature Importance
- **Logistic Regression (top 5):** `cp` (chest pain type), `thalch` (max heart rate), `ca` (number of major vessels), `oldpeak` (ST depression), `sex`
- **Decision Tree (top 5):** `thalch`, `cp`, `oldpeak`, `ca`, `trestbps`

### Key Insights
- Chest pain type and maximum heart rate are the strongest predictors across both models.
- Logistic Regression is more interpretable (coefficients show direction of influence) and generalizes slightly better on test data.
- Decision Tree captures non‑linear interactions but requires pruning (`max_depth=5`) to prevent overfitting.
- ROC‑AUC > 0.85 indicates excellent separation between healthy and diseased patients.

### Visual Outputs
The notebook produces:
- Correlation heatmap, age distribution, chest pain type bar chart
- Box plots of key features vs. target
- Confusion matrices and ROC curves for both models
- Feature importance bar charts
- Visualized decision tree (depth‑limited)

## How to Run

1. **Clone the repository** and navigate to this folder:
   ```bash
   cd task3_heart_disease_prediction