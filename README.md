# Predicting Housing Prices in Ames

## 1. Project Overview

This project aims to predict residential house prices in Ames, Iowa, using housing characteristics and various machine learning techniques.

Using the Ames Housing dataset from Kaggle, we explore the relationships between housing features and sale prices, investigate the underlying data structure, and develop predictive models to compare their performance.

The project covers the complete data analysis workflow, including data preprocessing, exploratory data analysis (EDA), dimensionality reduction, clustering, predictive modeling, and model evaluation.

## 2. Dataset

**Source:** [Kaggle – House Prices: Advanced Regression Techniques](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques/)

The dataset contains 79 explanatory variables describing various aspects of residential properties in Ames, Iowa, including:

- Property characteristics and building type
- Overall quality and condition
- Living area and total square footage
- Neighborhood and location
- Garage, basement, and other facilities
  ...

The target variable is `SalePrice`, representing the sale price of each house.

After data preprocessing and feature engineering, the dataset used in the analysis contains 1,458 observations and 257 dimensions, including the target variable.

## 3. Data Preparation

The following preprocessing steps were performed:

- **Missing value treatment:** Handled missing values based on the dataset's data descriptions and the meaning of individual features.
- **Outlier treatment:** Identified and addressed outliers to reduce their potential impact on model performance.
- **Feature engineering:** Created additional variables by combining related features and transforming numerical variables into more meaningful categories. For example, `Age` was created to represent the time interval between a house's construction and sale.
- **Categorical encoding:** Converted categorical variables into numerical representations using one-hot encoding.
- **Feature scaling:** Standardized numerical features where appropriate.

These steps prepared the dataset for exploratory analysis and machine learning modeling.

## 4. Exploratory Data Analysis

We conducted exploratory data analysis to investigate feature distributions and relationships with house prices.

Key findings include:

- `TotalSF` (total square footage) has a strong positive correlation with `SalePrice` (approximately 0.83).
- `OverallQual` (overall material and finish quality) also shows a strong positive correlation with `SalePrice` (approximately 0.82).
- Other important features include `QualScore`, `GrLivArea`, and `ExterQual`.

These findings suggest that property size and overall quality are important factors associated with housing prices in the dataset.

## 5. Dimensionality Reduction and Clustering

### Principal Component Analysis (PCA)

PCA was applied to explore the high-dimensional feature space and reduce dimensionality.

- The number of features was reduced from 256 to 62.
- The retained principal components explain approximately 95% of the cumulative variance.
- The first two principal components were visualized to explore patterns in the data.

### K-Means Clustering

K-Means clustering was applied to explore potential groups of houses using the PCA-transformed data.

Five clusters were visualized using the first two principal components. Although some distributional differences can be observed, considerable overlap remains among several clusters. Therefore, the clustering results are treated as exploratory rather than evidence of clearly separated groups.

## 6. Predictive Modeling

We implemented and compared several regression and machine learning models.

| Model | Purpose |
|---|---|
| Ordinary Least Squares (OLS) | Establish a baseline regression model |
| Lasso Regression | Apply L1 regularization and perform feature selection |
| Decision Tree Regressor | Capture nonlinear relationships through tree-based modeling |
| Random Forest Regressor | Improve prediction stability using an ensemble of decision trees |
| Neural Network | Model complex nonlinear relationships |
| XGBoost | Apply gradient boosting to improve predictive performance |

### Model Evaluation

We evaluated model performance using:

- Root Mean Squared Error (RMSE)
- Mean Absolute Error (MAE)
- Coefficient of Determination (R²)
- Cross-validation

Grid search with five-fold cross-validation was used for hyperparameter tuning of the Decision Tree and Random Forest models.

### Reported Results

The following results are reported in the model evaluation sections of the project notebook.

| Model | Test RMSE | Test MAE | Test R² |
|---|---:|---:|---:|
| Lasso Regression | 0.122 | — | — |
| Decision Tree | 0.1868 | 0.1248 | 0.7930 |
| Random Forest | 0.1437 | 0.0944 | 0.8776 |
| Neural Network (shallower architecture) | 0.1641 | 0.1217 | — |


### Key Findings

- Lasso Regression improves upon the OLS baseline by introducing L1 regularization and selecting relevant features.
- Random Forest outperforms the single Decision Tree in the reported test-set metrics.
- `TotalSF` and `OverallQual` are among the most important features identified by the Random Forest model.
- Neural networks can capture nonlinear relationships, while their performance varies with network architecture and regularization settings.
- XGBoost feature importance analysis also highlights `OverallQual`, `TotalSF`, `QualScore`, and `GarageCars` as important predictors.

Overall, the results demonstrate the usefulness of regularized regression and tree-based ensemble methods for housing price prediction.

## 7. Limitations and Future Work

Several limitations should be considered:

- Model performance may be affected by the dataset size, feature selection, preprocessing decisions, and hyperparameter settings.
- Further work could explore additional machine learning algorithms, more systematic hyperparameter optimization, and datasets from other locations.
- More rigorous validation and model interpretation could help improve the reliability and generalizability of the findings.

## 8. My Contributions

My contributions to this group project included:

- **Topic and data selection:** Searched for relevant datasets and research topics on Kaggle, selected the Ames Housing dataset, and defined the house price prediction objective.
- **Data preparation:** Participated in data cleaning and preprocessing, including missing value treatment, outlier handling, feature engineering, categorical encoding, and feature scaling.
- **Data analysis:** Conducted exploratory data analysis, examined feature correlations, applied PCA and K-Means clustering, and developed and compared multiple predictive models.
- **Report writing:** Summarized the analytical process and modeling results, interpreted findings, discussed limitations, and contributed to the final project report.

## 9. Tools and Technologies

- Python
- Jupyter Notebook
- Pandas and NumPy
- Matplotlib and Seaborn
- Scikit-learn
- XGBoost

## 10. Acknowledgements

The project uses the publicly available Ames Housing dataset from the Kaggle **House Prices: Advanced Regression Techniques competition**.
This project was completed as a group academic project for ECON5181 @CUHK.
