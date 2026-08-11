# Results

This folder documents the main outputs of the final project without publishing the original datasets.

## Store segmentation

The final segmentation contains three K-Means profiles plus an atypical group identified with DBSCAN:

- High Conversion: 142 stores
- Waste Risk: 150 stores
- Conservative: 23 stores
- Outliers: 17 stores

The K-Means solution used K=3 and achieved a silhouette score of 0.408 on the normal stores.

## Predictive model

Random Forest was selected as the final classifier.

Final test performance:

- Accuracy: 0.6952
- Precision: 0.6980
- Recall: 0.7609
- F1: 0.7281
- ROC-AUC: 0.7627

See `../notebooks/02_store_segmentation.ipynb` and `../notebooks/03_sales_prediction_model.ipynb` for the analysis workflows.