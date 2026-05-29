# Credit Card Fraud Detection at Scale
### Distributed SMOTE Bagging on Apache Spark | Azure Databricks

## Overview
This project investigates techniques for handling severe class imbalance in large-scale fraud detection using Apache Spark on Azure Databricks. Three distributed SMOTE Bagging variants are implemented and compared across performance, scalability, and partition sensitivity.

**Dataset:** [Credit Card Fraud Detection — Kaggle](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)  
284,807 transactions | 1:592 class imbalance | 30 features (PCA-transformed)

## Variants Implemented
| Variant | Approach | Author |
|---|---|---|
| Variant 1 | Local SMOTE Bagging (baseline) | Mustafa Talat |
| Variant 2A | Stratified Repartition via `sortBy` | Sofia Saeed Ahmed |
| Variant 2B | Stratified Repartition via `mapPartitions` | Sofia Saeed Ahmed |
| Variant 3 | Global Minority Broadcast SMOTEBagging | Umrah |

Cross-variant results summary and scalability experiments also authored by Sofia Saeed Ahmed.

## Key Results
- Best AUC-ROC: **0.98** (Variant 3)
- Best F1: **0.85** (Variant 2A at optimal threshold)
- Max speed-up: **14.9x** scaling from 2 → 16 partitions
- Ensemble: 80 Decision Trees across 8 partitions

## Tech Stack
`PySpark` `Azure Databricks` `Scikit-learn` `SMOTE` `Pandas` `NumPy` `Matplotlib`

## How to Run
1. Upload notebook to Azure Databricks workspace
2. Download dataset from Kaggle and mount to `/mnt/your-path/creditcard.csv`
3. Run cells sequentially — Section 2 preprocesses and saves to Parquet, subsequent sections load from there

## Authors
Group 7 — COMP4124, University of Nottingham UK  
- Sofia Saeed Ahmed (Variant 2A, 2B, cross-variant summary)
- Mustafa Talat (Variant 1)
- Umrah (Variant 3)
