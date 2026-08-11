# 📊 Discount Label Optimization — End-to-End Data Analytics Project

> **Final project — Data Science & Business Analytics**
>
> An end-to-end analytics project combining data preparation, exploratory analysis, Power BI, store segmentation and predictive modelling to support data-driven commercial decisions.

## 🎯 Project Overview

The objective was to analyse discount-label activity across stores and products, identify operational patterns, segment stores according to their behaviour, and build a predictive model to understand factors associated with successful discount-label sales.

**Data → Cleaning → EDA → Power BI → Segmentation → Predictive Modelling → Business Recommendations**

## 📌 Business Problem

**How can discount-label and store-level data be transformed into actionable insights that help improve conversion, reduce waste and support more targeted commercial decisions?**

After cleaning and validation, the analytical dataset contained **150,023 label records**, **342 registered stores**, **332 stores with label history**, and **318 SKUs**.

---

## 🔎 Project Workflow

### 1. Data Cleaning & Preparation

- Audited data types, missing values and duplicates
- Standardised categorical and numeric fields
- Applied business rules and validation checks
- Integrated product-level and store-level data using `Store ID`
- Created analytical features for downstream analysis

➡️ [Data cleaning notebook](notebooks/data_cleaning.ipynb)

### 2. Exploratory Analysis & Power BI

The analysis examined operational and commercial KPIs across stores, products and time periods. The Power BI component was designed for interactive exploration of store performance, product behaviour and discount-label activity.

➡️ [Power BI documentation](powerbi/README.md)

### 3. Store Segmentation

Store behaviour was analysed using **DBSCAN** for outlier detection and **K-Means** for segmentation of non-outlier stores. The final K-Means solution used **K = 3**, complemented by the DBSCAN outlier group.

| Segment | Stores | Interpretation |
|---|---:|---|
| 🟢 **High Conversion** | 142 | Strong sell-through and profitability |
| 🟠 **Waste Risk** | 150 | High activity with weaker sell-through and profitability |
| 🔵 **Conservative** | 23 | Lower activity with a more conservative discount profile |
| 🔴 **Outliers** | 17 | Atypical behaviour requiring individual investigation |

➡️ [Store segmentation notebook](notebooks/store_segmentation.ipynb)

### 4. Predictive Modelling

Four classification models were evaluated:

- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting

The final **Random Forest** model achieved on the test set:

| Metric | Result |
|---|---:|
| Accuracy | 0.6952 |
| Precision | 0.6980 |
| Recall | 0.7609 |
| **F1 Score** | **0.7281** |
| **ROC-AUC** | **0.7627** |

The workflow included cross-validation, model comparison, tuning, test-set evaluation, confusion matrix analysis and permutation feature importance.

➡️ [Sales prediction notebook](notebooks/sales_prediction_model.ipynb)

---

## 💡 Key Business Insights

- **High Conversion:** 60.7% sell rate and approximately €0.102 profit per label. A potential opportunity is to test slightly lower discounts while protecting margin.
- **Waste Risk:** the largest segment, with 150 stores and a 43.6% sell rate. Recommended focus: product selection, waste reduction and earlier promotional actions.
- **Conservative:** 47.5% sell rate with a lower average discount of 26.1%, suggesting aggressive discounts may not always be necessary.
- **Outliers:** relatively low volume but high average discount; better suited to exception-based analysis than broad strategic changes.

> **Analytical note:** feature importance and model associations indicate predictive usefulness, not causality. Future-period validation is required before operational deployment.

---

## 🛠️ Tools & Technologies

**Python** · **Pandas** · **NumPy** · **Matplotlib** · **Seaborn** · **Scikit-learn** · **Jupyter Notebook** · **Power BI** · **Excel**

### Key competencies demonstrated

- Data cleaning & preprocessing
- Data integration & feature engineering
- Exploratory Data Analysis (EDA)
- KPI analysis
- Business intelligence & dashboard development
- Unsupervised learning
- Supervised machine learning
- Model evaluation & validation
- Business segmentation
- Data storytelling
- Translating analytical findings into business recommendations

---

## 📂 Repository Structure

```text
final_project_discount_labels/
├── README.md
├── data/
├── images/
├── notebooks/
│   ├── data_cleaning.ipynb
│   ├── store_segmentation.ipynb
│   ├── sales_prediction_model.ipynb
│   └── README.md
├── powerbi/
├── results/
└── portfolio_note.md
```

### Data policy

The original Excel datasets and other binary project deliverables are intentionally **not included** in this public repository. This keeps the portfolio shareable while avoiding unnecessary redistribution of source data.

The notebooks document the analytical workflow and the README documents the principal results and business interpretation.

---

## 📈 Future Improvements

- Validate the predictive model on future time periods
- Add automated data-quality checks
- Track model drift and KPI changes over time
- Improve segmentation with additional behavioural features
- Connect the dashboard to a refreshable data source
- Test business interventions against measurable conversion and waste outcomes

---

## 👩‍💻 Author

**Cris Guimarães**  
Data Analyst | Python | SQL | Power BI

This project was developed as the final project of my Data Science & Business Analytics programme.
