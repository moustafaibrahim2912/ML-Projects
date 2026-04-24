# Flight Delay Prediction

## Overview
This project builds a binary classification model to predict whether a flight will be delayed on arrival, using historical flight schedule and operational data from the U.S. Bureau of Transportation Statistics (BTS).

The model predicts delay likelihood before a flight departs, using only information that would realistically be available at booking or gate time — with strict care taken to avoid data leakage from post-flight operational fields.

## Dataset
The dataset was sourced from the BTS Airline On-Time Performance dataset from Kaggle.
A sample of the raw dataset is provided in:
data/raw/

Link to the full Dataset: [The Dataset](https://www.kaggle.com/datasets/mexwell/carrier-on-time-performance-dataset)

A dataset of approximately **1.4 million flight records** was used, covering domestic U.S. flights across multiple airlines, routes, and airports.

### Target Variable
`ArrDel15` — binary indicator of whether a flight arrived 15 or more minutes late.

### Data Challenges & Processing
- Removal of post-flight leakage columns (actual departure/arrival times, taxi times, cancellation flags)
- Handling of null values in the target variable caused by cancelled and diverted flights
- High-cardinality categorical columns (airports, tail numbers, airline codes)
- Class imbalance (~20% delayed, ~80% on time)

Preprocessing was split across dedicated notebooks, with train/test split performed before any feature aggregation to prevent leakage.

## Pipeline

1. Data ingestion and column audit
2. Leakage identification and removal
3. Null value analysis and handling
4. Train/test split
5. Feature engineering (temporal, route, and historical aggregations)
6. Model training and benchmarking
7. Threshold tuning and evaluation

## Feature Engineering

Features were engineered in two phases:

**Direct derivations** (from existing columns):
- `dep_hour` — extracted from scheduled departure time
- `dep_period` — time-of-day bucket (early morning, morning, afternoon, evening, red-eye)
- `season` — derived from month
- `is_peak_month` — flags high-traffic travel periods (summer, holidays)

**Historical delay rate aggregations** (computed from training data only):
- `route_delay_rate` — historical delay rate per Origin-Dest pair
- `tail_delay_rate` — historical delay rate per aircraft
- `airline_delay_rate`, `origin_delay_rate`, `dest_delay_rate`

## Modeling & Evaluation

Two models were implemented and compared:

- **CatBoost**
- **LightGBM**

CatBoost was selected as the final model due to its superior handling of high-cardinality categorical features without explicit encoding.

| Metric | CatBoost | LightGBM |
|---|---|---|
| ROC-AUC | **0.644** | 0.624 |
| Delayed F1 | **0.38** | 0.36 |
| Delayed Recall | 0.66 | 0.77 |
| Delayed Precision | **0.27** | 0.24 |
| Best Threshold | **0.47** | 0.22 |

Class imbalance was addressed using `scale_pos_weight` (ratio ≈ 4.04), and prediction threshold was tuned to maximize F1 on the delayed class rather than defaulting to 0.5.

## Model Capabilities

- Binary classification (delayed / not delayed)
- Probability-based output for threshold flexibility
- Operates on pre-departure information only — no real-time data required
- Handles unseen airports and routes via global mean fallback in aggregated features

## Tools & Technologies

- Python
- Pandas / NumPy
- Scikit-learn
- CatBoost
- LightGBM
- Matplotlib / Seaborn
- Jupyter Notebook

## Conclusion

This project demonstrates a complete end-to-end machine learning pipeline on a large real-world dataset, with particular emphasis on leakage prevention, imbalanced classification, and honest evaluation.

The primary performance ceiling is the absence of real-time weather data, which is responsible for approximately 40% of real-world flight delays and is not present in the BTS schedule dataset. The model achieves strong results purely from schedule and historical pattern features, and provides a solid foundation for enrichment with weather or live operational data.