# 📊 Discount Label Optimization — End-to-End Data Analytics Project

> Final project developed as part of my Data Science & Business Analytics program.

## Overview

This project explores how discount labels can be optimized to improve product sell-through and support more effective commercial decisions.

The analysis follows an end-to-end analytics workflow:

**Data Cleaning → Business Analysis → Power BI → Store Segmentation → Predictive Modeling → Business Recommendations**

The central business question was:

> **How can we increase the probability of selling discounted products by choosing appropriate discounts and actions for the context of each store and product?**

The solution combines a reliable analytical dataset, an interactive Power BI dashboard, actionable store segments, and a machine learning model that predicts whether a labelled product will be sold.

---

## 🎯 Project Objectives

- Build a reliable and consistent analytical dataset.
- Understand the performance of discount labels across stores and products.
- Create an interactive dashboard for business exploration.
- Segment stores according to their commercial behaviour.
- Predict whether a discounted product will be sold.
- Translate analytical findings into practical commercial recommendations.

---

## 📁 Project Structure

```text
final_project_discount_labels/
│
├── README.md
│
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_store_segmentation.ipynb
│   └── 03_sales_prediction_model.ipynb
│
├── data/
│   └── README.md
│
├── powerbi/
│   └── README.md
│
├── results/
│   └── README.md
│
└── images/
    └── README.md
```

The original datasets are intentionally not included in this public repository. The notebooks document the analytical workflow, while this README and the supporting documentation describe the outputs and methodology.

---

## 🧹 1. Data Cleaning & Preparation

Two complementary datasets were used: product-level discount labels and store-level characteristics.

The initial label dataset contained **150,054 records**, covering **342 stores** and **319 SKUs**. After validation, the final analytical dataset contained **150,023 records**, with **318 SKUs** and **332 stores with label history**.

Key data-quality issues included inconsistent text and numeric formats, missing values, invalid dates, invalid percentages, and missing store-area information.

The cleaning process included:

- Data type correction and normalization.
- Brand and payment-method standardization.
- Price and discount parsing.
- Date normalization.
- Missing-value treatment based on relationships observed in the data.
- Validation of sales dates against labelling dates.
- Creation of `sku_shelf_life` and `area_missing_flag` features.
- Store-level area imputation using a cascading median strategy.
- Business-rule validation before exporting the clean datasets.

Repeated labels were not automatically removed because repetitions could represent legitimate multiple labels for the same product.

---

## 📊 2. Power BI Dashboard

The Power BI component transforms the static analysis into an interactive business intelligence experience.

The dashboard was designed to support:

- Sales, margin and waste KPIs.
- Filtering by store, product, segment and date.
- Store-level performance analysis.
- Exploration of discount performance.
- Commercial prioritization and decision support.

The dashboard is documented separately in [`powerbi/README.md`](powerbi/README.md).

---

## 🏪 3. Store Segmentation

Stores were aggregated into comparable behavioural indicators and segmented according to their commercial performance rather than fixed characteristics.

### Features used

- `sold_rate` — proportion of labels sold.
- `profit_per_label` — average profit generated per label.
- `discount_avg` — average discount applied.

The workflow used **DBSCAN** to identify atypical stores before applying **K-Means** to the remaining stores. `StandardScaler` was used because the clustering variables were on different scales.

K-Means was tested across multiple values of `k`. The final solution used **K = 3**, with a silhouette score of **0.408**, plus a separate atypical group identified through DBSCAN.

### Store profiles

| Segment | Stores | Interpretation |
|---|---:|---|
| **High Conversion** | 142 | Strong sell-through and the best profit per label. |
| **Waste Risk** | 150 | High label volume but lower sell-through and profitability. |
| **Conservative** | 23 | Reasonable sell-through with lower average discounts. |
| **Outliers** | 17 | Atypical behaviour requiring separate interpretation. |

The segmentation was translated into commercial actions rather than being treated only as a technical clustering exercise.

---

## 🤖 4. Predictive Modeling

The predictive task was to classify whether a discount label would be sold:

- `0` → Not sold
- `1` → Sold

The target classes were relatively balanced, with approximately **46.35% not sold** and **53.65% sold**.

To avoid data leakage, variables only available after the sale were excluded, including `sell_date` and `Payment_method`. Identifiers such as `idstore` and `sku` were also excluded to reduce the risk of memorization.

### Models compared

- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting

A common preprocessing pipeline was used with missing-value imputation, scaling, and one-hot encoding. Model selection was based primarily on **F1 score in cross-validation**, with ROC-AUC used as a complementary metric.

### Final model — Random Forest

| Metric | Test |
|---|---:|
| Accuracy | 0.6952 |
| Precision | 0.6980 |
| Recall | 0.7609 |
| **F1** | **0.7281** |
| **ROC-AUC** | **0.7627** |

Random Forest provided the strongest overall balance among the models tested and showed a relatively small difference between cross-validation and final test performance.

The model's predictive importance analysis highlighted variables such as `brand`, `district`, `selling_square_ft`, `weight (g)`, `perc_expiring_sku`, and `type`.

> Predictive importance should not be interpreted as causal impact. The analysis describes associations observed in the available data.

---

## 💡 Business Insights

The analysis suggests that discount-label performance varies substantially between stores.

The **High Conversion** group achieved a 60.7% sell rate and approximately €0.102 profit per label, suggesting an opportunity to test slightly lower discounts while protecting margin.

The **Waste Risk** group represented the largest commercial concern: 150 stores with a 43.6% sell rate and approximately €0.073 profit per label. The recommended action is to review which products receive discounts and consider earlier promotional actions.

The **Conservative** stores achieved a 47.5% sell rate with a lower average discount of 26.1%, suggesting that aggressive discounts may not always be necessary.

The **Outlier** group had relatively low label volume but the highest average discount, making it more appropriate for exception-based analysis rather than broad strategic changes.

---

## 🚀 Deployment & Follow-up

The proposed operational workflow is:

```text
New Data
   ↓
Sales Probability Score
   ↓
Discount Scenario Analysis
   ↓
Prioritize Stores & Products
   ↓
Execute Commercial Action
   ↓
Measure Results
   ↓
Monitor Model Performance
```

Recommended monitoring includes:

- F1, ROC-AUC, precision and recall.
- Changes in prices and discount distributions.
- Changes in product mix and store behaviour.
- Performance by segment and period.
- Validation on future periods.

The project recommends starting with a controlled pilot and recalibrating the model as new data becomes available.

---

## ⚠️ Limitations

- The available data primarily represents October 2021, limiting seasonal analysis.
- There is no unique customer identifier.
- The random train/test split should be complemented by validation on future periods.
- Store segments depend on the selected behavioural variables.
- Clustering identifies patterns and associations, not causal relationships.
- Predictive importance does not establish causality.

---

## 🛠️ Tech Stack

**Languages & Analysis**
- Python
- Pandas
- NumPy

**Visualization**
- Matplotlib
- Seaborn
- Power BI

**Machine Learning**
- Scikit-learn
- K-Means
- DBSCAN
- Random Forest
- Gradient Boosting
- Logistic Regression
- Decision Tree

**Environment**
- Jupyter Notebook
- Power BI

---

## 👩‍💻 Author

**Cris Guimarães**  
Data Analyst | Python | SQL | Power BI

This project was completed as the final project of my Data Science & Business Analytics program.