# Crime Arrest Prediction Using Distributed Spark ML

## Project Overview
This project investigates arrest prediction using large-scale urban crime data (8.4 million records) from Data.gov. The objective is to evaluate distributed machine learning models using PySpark and assess scalability, stability, and computational trade-offs.

## Dataset
- Source: Data.gov
- Records: 8,398,434 after cleaning
- Features: 258 engineered features
- Storage format: Partitioned Parquet (partitioned by Year)

## Research Question
Can arrest outcomes be predicted using spatial, temporal, and categorical crime features at scale using distributed Spark ML?

## Methods
- Data Engineering: Parquet conversion, partitioning, null handling
- Feature Engineering: Temporal extraction (Hour, Month, DayOfWeek)
- Models:
  - Logistic Regression
  - Random Forest
  - Gradient Boosted Trees
- Hyperparameter tuning via CrossValidator
- Stability analysis (3 random splits)
- Scalability testing (25%, 50%, 100%)

## Results
| Model | ROC-AUC |
|--------|----------|
| Logistic Regression | 0.8707 |
| Random Forest | 0.8666 |
| GBT (30%) | 0.8711 |

Logistic Regression selected as final model due to stability and scalability.

## Stability
Standard deviation of ROC across splits: 0.00014 (highly stable)

## Scalability
Training time increased sublinearly with dataset size, demonstrating efficient distributed scaling.

## Reproducibility
- Spark config included in config/
- Environment dependencies in environment.yml
- Model saved for reuse

## AI Usage
AI assistance was used for guidance in structuring code and debugging, while all implementation decisions and interpretations were independently validated.
