# Breast Cancer Prediction

## Overview
This project builds a machine learning classification pipeline to predict breast cancer diagnosis (malignant or benign) using tumor feature data.

The objective is to develop a predictive model that can support early detection and clinical decision-making.

## Dataset
The dataset contains features extracted from digitized images of breast tumors:

- diagnosis — target variable (malignant or benign)
- radius_mean, texture_mean, perimeter_mean, area_mean, smoothness_mean
- compactness_mean, concavity_mean, concave points_mean, symmetry_mean, fractal_dimension_mean
- radius_se, texture_se, perimeter_se, area_se, smoothness_se
- compactness_se, concavity_se, concave points_se, symmetry_se, fractal_dimension_se
- radius_worst, texture_worst, perimeter_worst, area_worst, smoothness_worst
- compactness_worst, concavity_worst, concave points_worst, symmetry_worst, fractal_dimension_worst

The dataset is included in the repository.

## Project Structure

notebooks:
1. Data ingestion,Preprocessing & feature engineering – Loading , inspecting , cleaning and preparing features
3. Model training – Building and evaluating the classifier

## Modeling Approach

Several classifiers were considered.  
The final model uses [you can specify: e.g., KNN / Logistic Regression / Random Forest] achieving strong performance on the dataset.

## Model Performance

- Accuracy: 0.991%

The classifier demonstrates reliable ability to distinguish malignant from benign tumors.

## Tools & Technologies

- Python
- Pandas
- NumPy
- Matplotlib / Seaborn
- Scikit-learn
- Jupyter Notebook

## Conclusion

This project demonstrates an end-to-end machine learning workflow, from structured clinical data to predictive modeling.

Future improvements may include hyperparameter tuning, feature selection, and validation on larger medical datasets.
