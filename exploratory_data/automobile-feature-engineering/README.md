# Automobile Feature Engineering & Correlation Analysis

This project demonstrates a complete data preprocessing, feature engineering, and exploratory analysis pipeline for an automotive dataset using Python, Pandas, Seaborn, and Matplotlib.

## 📊 Project Workflow

The analysis is split into two sequential steps to keep the data pipeline clean and modular:

### 1. Data Transformation & Feature Engineering (`01-automobile-data-transformation.ipynb`)
* **Missing Value Imputation:** Handled structural data gaps (e.g., replacing missing door counts based on car body styles).
* **Data Type Formatting:** Cleaned and cast numerical columns originally loaded as objects.
* **Feature Scaling & Normalization:** * Applied Min-Max Scaling to the vehicle length.
    * Applied Standard Scaling (Z-score) to the width.
    * Log-transformed the vehicle height to handle skewness.
* **Binning:** Segmented vehicle prices into 10 uniform deciles (`price_decile`).
* **Output:** Generated the processed dataset `automobile-transformed.csv`.

### 2. Exploratory Analysis & Statistical Correlations (`02-automobile-correlation-analysis.ipynb`)
* **Statistical Profiling:** Evaluated data groupings and value frequencies by car manufacturers and price points.
* **Correlation Matrix:** Constructed a correlation heatmap to analyze how engine specifications and dimensions affect the final market price.
* **Key Insight:** Vehicle price shows an extremely strong positive correlation (> 0.80) with engine size, curb weight, and horsepower, while attributes like the number of doors or height show negligible impact.

## 🛠️ Technologies Used

* **Python 3**
* **Pandas & NumPy** (Data manipulation & scaling formulas)
* **Matplotlib & Seaborn** (Correlation heatmaps & visualizations)

## 📂 How to Run

1. Navigate to this folder inside your cloned laboratory:
   ```bash
   cd exploratory-data-analysis/automobile-feature-engineering
