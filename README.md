# MSCS_634_Lab_4 — Regression Analysis with Regularization Techniques

**Course:** Advanced Big Data and Data Mining (MSCS-634-B01)  
**Author:** Rajiv Agrawal  
**Instructor:** Satish Penmatsa  
**Due Date:** March 29, 2026

---

## Purpose

This lab explores a range of regression techniques applied to the **Diabetes Dataset** from `sklearn.datasets`. The dataset contains 10 physiological features (age, sex, BMI, blood pressure, and six blood serum measurements) for 442 patients, with a quantitative measure of disease progression one year after baseline as the target variable.

The lab implements and compares five regression approaches:

| Model | Description |
|-------|-------------|
| Simple Linear Regression | Single feature (BMI) predicting disease progression |
| Multiple Linear Regression | All 10 features as predictors |
| Polynomial Regression | Non-linear extension of Simple LR (degrees 2, 3, 5) |
| Ridge Regression | L2 regularization with tunable alpha |
| Lasso Regression | L1 regularization with automatic feature selection |

All models are evaluated on **MAE**, **MSE**, **RMSE**, and **R²**.

---

## Key Insights

1. **BMI is the strongest single predictor** of disease progression among all features, confirmed by the correlation analysis.

2. **Multiple Regression outperforms Simple Linear Regression** considerably — using all 10 features captures more variance in the target, raising R² from ~0.38 to ~0.51.

3. **Polynomial Regression (degree 2)** marginally improves over Simple Linear Regression on one feature, but higher degrees (3, 5) begin to overfit: training error drops while test metrics worsen, illustrating the bias-variance tradeoff clearly.

4. **Ridge Regression** smoothly shrinks all coefficients toward zero without eliminating any feature. It performs comparably to Multiple Regression for alpha=1.0 and is robust to multicollinearity.

5. **Lasso Regression** drives several feature coefficients to exactly zero, performing implicit feature selection. At alpha=0.1, it retains the most predictive features and generalizes well — making it preferable when interpretability is important.

6. **Regularization is most beneficial** when the dataset is high-dimensional, has correlated features, or when overfitting is a concern. On this relatively small, well-conditioned dataset, gains are modest but the behavior is clear.

---

## Challenges and Decisions

- **Feature selection for Simple LR:** BMI was chosen based on the correlation heatmap rather than arbitrarily, ensuring the one-feature model was as meaningful as possible.
- **Alpha tuning for Ridge/Lasso:** A grid of alpha values (`0.01, 0.1, 1.0, 10.0, 100.0`) was tested and visualized to show how regularization strength affects performance, with final models selected at sensible defaults (Ridge α=1.0, Lasso α=0.1).
- **Polynomial degree selection:** Degrees 2, 3, and 5 were chosen to demonstrate the progression from mild complexity to clear overfitting without needing a very large degree.
- **Normalization:** The Diabetes dataset features are already standardized by sklearn, so no additional scaling was required for linear models.

---

## Repository Contents

```
Lab 4/
├── Lab4_Regression_Analysis.ipynb   # Main Jupyter Notebook with all steps
└── README.md                        # This file
```

---

## How to Run

1. Ensure Python 3.8+ is installed with the following packages:
   ```
   numpy pandas matplotlib seaborn scikit-learn
   ```
2. Open `Lab4_Regression_Analysis.ipynb` in Jupyter Notebook or VS Code.
3. Run all cells in order (Kernel → Restart & Run All).
