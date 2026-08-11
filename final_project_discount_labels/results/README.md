# Results & Business Insights

This folder documents the main outputs of the final project without publishing the original datasets or binary deliverables.

## Store segmentation

The final segmentation contains three K-Means profiles plus an atypical group identified with DBSCAN:

| Segment | Stores | Interpretation |
|---|---:|---|
| High Conversion | 142 | Strong sell-through and profitability |
| Waste Risk | 150 | High activity with weaker sell-through and profitability |
| Conservative | 23 | Lower activity with a more conservative discount profile |
| Outliers | 17 | Atypical behaviour requiring individual investigation |

The K-Means solution used **K = 3** and achieved a **silhouette score of 0.408** on the normal stores.

## Predictive model

**Random Forest** was selected as the final classifier after comparing Logistic Regression, Decision Tree, Random Forest and Gradient Boosting.

### Final test performance

| Metric | Result |
|---|---:|
| Accuracy | 0.6952 |
| Precision | 0.6980 |
| Recall | 0.7609 |
| **F1** | **0.7281** |
| **ROC-AUC** | **0.7627** |

## Business takeaway

The project connects descriptive analytics, segmentation and predictive modelling into one decision-support workflow. The segmentation supports differentiated commercial actions, while the predictive model adds a way to identify patterns associated with successful discount-label sales.

> Feature importance and model associations indicate predictive usefulness, not causality. Future-period validation is required before operational deployment.

## Analysis workflows

- [Data cleaning notebook](../notebooks/data_cleaning.ipynb)
- [Store segmentation notebook](../notebooks/store_segmentation.ipynb)
- [Sales prediction notebook](../notebooks/sales_prediction_model.ipynb)
