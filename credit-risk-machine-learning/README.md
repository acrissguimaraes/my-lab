# Credit Risk Segmentation - Machine Learning 💳📊

This project marks the transition from manual, rule-based heuristics to automated **Machine Learning** for credit risk segmentation. Using a dataset of 500 customers, we train a **Decision Tree Classifier** to automatically discover the best splitting criteria (such as credit score thresholds or recent payment delays) to predict customer default.

---

## 📁 Repository Structure

* **`data/clientes_credito.csv`**: The primary dataset containing customer financial metadata (age, monthly income, credit score, 12-month payment delays, requested loan amount, and the binary target `inadimplente`).
* **`notebooks/01_decision_tree_segmentation.ipynb`**: The main Jupyter Notebook where the Machine Learning pipeline is built, evaluated, and visualized.

---

## 🛠️ Pipeline Steps

1. **Data Ingestion**: Loading the customer credit historical data into a Pandas DataFrame.
2. **Feature & Target Selection**: Dropping non-predictive administrative columns (like `id`) and separating features ($X$) from the target variable ($y$: `inadimplente`).
3. **Train/Test Split**: Allocating 80% of the dataset for training the model and reserving 20% as an unseen test set to evaluate real-world performance.
4. **Model Training**: Initializing and fitting a `DecisionTreeClassifier` with a controlled `max_depth=3` to guarantee model interpretability and avoid overfitting.
5. **Evaluation**: Computing model accuracy and analyzing detailed classification metrics (Precision, Recall, and F1-Score).
6. **Tree Visualization**: Exporting and plotting the resulting decision flow chart to audit the automated rules discovered by Spark/Scikit-Learn.

---

## 🚀 Key Libraries & Tech Stack

* **Python 3**
* **Pandas**: For data loading and preprocessing.
* **Scikit-Learn**: For dataset splitting, tree modeling, and evaluation metrics.
* **Matplotlib**: For rendering the structural diagram of the trained Decision Tree.

---

## 🧠 Core Machine Learning Concepts Covered

### Why split the data into Training and Testing sets?
To evaluate the model's true generalization power. If we test the model using the exact same data it used to learn, it might achieve a perfect score simply by memorizing the data (a problem known as *overfitting*). Testing on an unseen 20% subset acts like an external exam, proving whether the algorithm genuinely understood patterns or just memorized the past.

### What does `max_depth=3` represent?
The `max_depth` parameter defines the maximum distance between the root node (the very first question) and the farthest leaf node (the final decision). Restricting depth to 3 levels prevents the tree from creating highly specific, noisy rules for individual clients. This guarantees a clean, interpretable flowchart that can be easily explained to risk managers and business stakeholders.
