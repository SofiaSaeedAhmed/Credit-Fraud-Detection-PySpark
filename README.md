# Credit Card Fraud Detection at Scale
### Distributed SMOTE Bagging on Apache Spark | Azure Databricks

## Overview
This project investigates techniques for handling severe class imbalance in large-scale fraud detection using Apache Spark on Azure Databricks. Three distributed SMOTE Bagging variants are implemented and compared across performance, scalability, and partition sensitivity.

**Dataset:** [Credit Card Fraud Detection — Kaggle](https://www.kaggle.com/datasets/mlgulb/creditcardfraud)  
284,807 transactions | 1:592 class imbalance | 30 features (PCA-transformed)

## Variants Implemented
| Variant | Approach |
|---|---|
| Variant 1 | Local SMOTE Bagging (baseline) |
| Variant 2A | Stratified Repartition via `sortBy` |
| Variant 2B | Stratified Repartition via `mapPartitions` |
| Variant 3 | Global Minority Broadcast SMOTEBagging |

## Key Results
- Best AUC-ROC: **0.98** (Variant 3)
- Best F1: **0.85** (Variant 2A at optimal threshold)
- Max speed-up: **14.9x** scaling from 2 → 16 partitions
- Ensemble: 80 Decision Trees across 8 partitions

## Tech Stack
`PySpark` `Azure Databricks` `Scikit-learn` `SMOTE` `Pandas` `NumPy` `Matplotlib`

## Structure
fraud_detection_smote_bagging.ipynb  # Main notebook
README.md

## How to Run
1. Upload to Azure Databricks workspace
2. Download dataset from Kaggle and mount to `/mnt/your-path/creditcard.csv`
3. Run cells sequentially — Section 2 preprocesses and saves to Parquet, subsequent sections load from there

