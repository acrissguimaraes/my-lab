# 🧠 Mental Health Analytics & Predictive Modeling

[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/)
[![PowerBI](https://img.shields.io/badge/Tools-Power%20BI-yellow.svg)](https://powerbi.microsoft.com/)
[![Jupyter Notebook](https://img.shields.io/badge/Tools-Jupyter%20Notebook-orange.svg)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)

An end-to-end data science and analytics project designed to map, understand, and visualize the complex variables influencing psychological conditions (such as **Anxiety, Depression, Burnout, and Normal** states). This repository combines exploratory data analysis (EDA), custom feature engineering, linear regression models, and an interactive business intelligence dashboard to uncover how modern lifestyle habits and environmental pressures impact mental well-being.

---

## 📊 Dashboard Overview

The project includes an interactive Power BI dashboard designed to translate multi-dimensional socio-emotional data into highly accessible, visual insights:

![Mental Health Dashboard](dashboard.png)

### Key Metrics & Views Monitored:
* **Clinical Condition Distribution:** Proportional breakdown of clinical classifications (Burnout, Depression, Anxiety, and Normal).
* **Stress & Pressure Vectors by Occupation:** Comparative analysis evaluating how academic work pressure and stress metrics fluctuate among Students, Working Professionals, and individuals managing both.
* **Behavioral Correlation Matrices:** Granular tracking of the relationship between sleep quality, social media consumption, physical activity, and overall mood scores.

---

## 🛠️ Tech Stack & Ecosystem

* **Language & Analysis Pipeline:** Python 3.9+
* **Data Manipulation:** `pandas`, `numpy`
* **Statistical Visualizations:** `matplotlib`, `seaborn`
* **Business Intelligence & Dashboards:** Microsoft Power BI Desktop (`.pbix`)
* **Environment:** Jupyter Notebook / Interactive Python Kernel

---

## ⚙️ Advanced Feature Engineering

To capture underlying behavioral patterns more effectively, the data pipeline calculates and integrates two distinct custom metrics:

1.  **Lifestyle Score:** A composite metric aggregating regular physical activity frequency with self-reported sleep quality to establish an individual's behavioral resilience baseline.
2.  **Burnout Risk Index:** A weighted metric that combines perceived daily stress indicators with current academic or professional workload pressures.

*The pipeline leverages customized `sns.regplot` visualizations to demonstrate mathematically how increments in the calculated **Lifestyle Score** actively work to mitigate the **Burnout Risk Index** across various demographic segments.*

---

## 📁 Repository Structure

```text
├── mental_health_prediction_raw_data.csv   # Structured dataset containing lifestyle and socio-emotional metrics
├── mental_health_prediction_analyses.ipynb # Jupyter Notebook executing data cleaning, engineering, and plotting
├── mental_health_prediction.pbix          # Native Power BI Desktop model file containing data relationships and reports
├── dashboard.png                          # High-resolution capture of the interactive dashboard layout
└── README.md                              # Main project documentation
