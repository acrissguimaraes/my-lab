# Retail Transactions Exploratory Data Analysis (EDA)

This project focuses on the initial exploration, cleaning, and normalization of a retail transactions dataset using Python and Pandas[cite: 6]. The main goal is to prepare raw transactional data for future business intelligence and analytical modeling by ensuring data consistency and integrity[cite: 6].

## 📊 Dataset Overview

The dataset (`transactions-raw.csv`) contains historical retail transactions with the following key attributes[cite: 6]:
*   **Transaction Metadata:** `transaction_id`, `tran_date`[cite: 6].
*   **Customer & Store Information:** `cust_id`, `Store_type`[cite: 6].
*   **Product Categories:** `prod_cat_code`, `prod_subcat_code`[cite: 6].
*   **Financial Metrics:** `Qty` (Quantity), `Rate`, `Tax`, and `total_amt`[cite: 6].

## 🛠️ Data Cleaning & Pipeline Steps

The Jupyter Notebook implements a structured data preprocessing pipeline[cite: 6]:

1. **Data Ingestion & Inspection:** Loading the raw transaction records and analyzing the initial data shapes, column types, and structural properties[cite: 6].
2. **Deduplication:** Checking for and removing duplicate transaction records to prevent data inflation (`drop_duplicates`)[cite: 6].
3. **Date Standardization:** Converting the transaction dates into a unified `datetime` format (`DD/MM/YYYY`) for correct chronological sorting and time-series profiling[cite: 6].
4. **Categorical Categorization & Mapping:** Standardizing the acquisition channels (`Store_type`) using a custom dictionary mapper to make classifications clearer (e.g., converting `e-Shop` to `Online`, `TeleShop` to `Telefone`)[cite: 6].

## 🚀 Technologies Used

*   **Python 3**
*   **Pandas** (Data manipulation and cleaning)[cite: 6]
*   **Jupyter Notebook**[cite: 6]

## 📁 How to Run

1. Clone the repository and navigate to this folder:
   ```bash
   cd exploratory-data-analysis/retail-transactions****
