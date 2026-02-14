# Heart Disease Prediction 

## Overview
This project builds a machine learning classification pipeline to predict the presence of heart disease using clinical patient data.

The objective is to develop a predictive model that supports early risk detection.

## Dataset
The dataset contains medical features collected from patient examinations:

- age — patient age
- sex — biological sex
- cp — chest pain type
- trestbps — resting blood pressure
- chol — serum cholesterol
- fbs — fasting blood sugar
- restecg — resting electrocardiographic results
- thalch — maximum heart rate achieved
- exang — exercise-induced angina
- oldpeak — ST depression induced by exercise
- slope — slope of peak exercise ST segment
- thal — thalassemia indicator
- num — heart disease diagnosis (target variable)

The dataset is included in the repository.

## Project Structure

notebooks:
1. Data ingestion – Loading and inspecting the dataset
2. Preprocessing & feature engineering – Cleaning and preparing features
3. Model training – Building and evaluating the classifier

## Modeling Approach

K-Nearest Neighbors (KNN) provided great balance between performance and simplicity for this dataset.

## Model Performance

- Accuracy: 87%

The classifier demonstrates strong ability to distinguish between healthy and high-risk patients.

## Tools & Technologies

- Python
- Pandas
- NumPy
- Matplotlib / Seaborn
- Scikit-learn
- Jupyter Notebook

## Conclusion

This project demonstrates an end-to-end medical classification workflow, from structured clinical data to predictive modeling.

Future improvements may include hyperparameter tuning, ensemble models, and validation on larger healthcare datasets.
