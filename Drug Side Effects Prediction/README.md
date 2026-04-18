# Drug Side Effects Prediction System

## Overview
This project develops a robust multi-label machine learning system to predict drug side effects based on active ingredient compositions.

Unlike simple classification tasks, the model predicts multiple side effects simultaneously and provides probability estimates to quantify the likelihood and prevalence of each effect.

## Dataset
The dataset was sourced from Kaggle and required extensive preprocessing due to its size and inconsistency.

A sample of the raw dataset is provided in:
data/raw/

Link to the full Dataset: [The Dataset](https://www.kaggle.com/datasets/imtkaggleteam/medical-information-dataset)

### Data Challenges & Processing
- Inconsistent naming of active ingredients
- Variations in side effect terminology
- Noisy and duplicated records
- Unstructured text patterns

Extensive preprocessing was performed, including normalization, text cleaning, and standardization using regex and custom logic.

## Pipeline

1. Data ingestion and validation  
2. Advanced data cleaning and normalization  
3. Feature engineering for multi-label learning  
4. Model training and benchmarking  
5. Evaluation using multiple metrics  

## Modeling & Evaluation

Multiple models were implemented and compared:

- Logistic Regression  
- XGBoost  
- LightGBM  
- CatBoost  

Performance ranged between **87% and 99% accuracy**.

- **CatBoost** achieved the best overall balance across metrics  
- **Logistic Regression** achieved higher **accuracy and recall** in some cases  
- Trade-offs observed in **precision and F1-score**, highlighting model selection complexity  

## Model Capabilities

- Multi-label classification (predicting multiple side effects per drug)
- Probability-based outputs for each label
- Supports ranking side effects by likelihood
- Designed for real-world noisy medical data

## Tools & Technologies

- Python
- Pandas / NumPy
- Scikit-learn
- CatBoost / XGBoost / LightGBM
- SciPy
- Regex 
- SpellChecker 
- tqdm 
- JSON 
- Jupyter Notebook

## Conclusion

This project demonstrates handling of a complex real-world dataset with significant data quality challenges.

It highlights the importance of:
- Deep data preprocessing
- Careful model comparison
- Understanding metric trade-offs in multi-label problems

The system provides a strong foundation for building real-world drug safety and decision-support applications.