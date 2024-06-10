![Logo](https://github.com/tree-shrew/regression-california-housing/blob/main/Bivariate%20Analysis.png)


# Predictive Modelling using Linear Regression on the California Housing Dataset

This repository provides a detailed analysis and implementation of a Linear Regression model to predict median household values for California districts based on the 1990 US Census data.


## Implementation Details

- `Dataset`: California Housing Dataset [(Details)](https://github.com/tree-shrew/regression-california-housing#dataset-details)
- `Model`: [Linear Regressor](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html)
- `Input`: 8 features, all numeric with no null values
- `Output`: Median House Value
- `Scale`: All features were scaled as a pre-processing step
- `Select`: Feature selection & Dimensionality reduction methods were applied on the dataset
- `Split`: For a standard test size of 0.2, random state was initialised as 8
- `Scores`: R Squared values and Mean Squared Errors were calculated for each mothod


## Evaluation and Results


| *Method*                       | *R2 Score*    | *MSE*        |
| ------------------------------ | ------------- | ------------ |
| No feature selection           | 0.6179        | 0.5015       |
| Mutual Information Regression  | 0.5966        | 0.5294       |
| f_test Regression              | 0.6182        | 0.5012       |
| Pearson's Correlation          | 0.6025        | 0.5218       |
| Recursive Feature Elimination  | 0.6023        | 0.5221       |
| Select From Model              | 0.6013        | 0.5234       |
| Sequential Feature Selection   | 0.6022        | 0.5222       |
| Intrinsic L1 Regularization    | 0.6146        | 0.5059       |
| Principal Component Analysis   | 0.6010        | 0.5238       |

The above quant results show that ≈61% of the variability observed in the target variable can be explained by the regression model. 

Feature selection through f_test (Pearson's correlation) on scaled data (MinMaxScaler) provided the best accuracy (R2 = 61.69%, MSE = 0.5029) with minimal computational cost (k = 6)

![R2 Score & MSE across different Methods](https://github.com/tree-shrew/regression-california-housing/blob/main/R2%20%26%20MSE%20across%20methods.png)


## Table of Contents

- [Getting Started](#getting-started)
- [Data Overview](#data-overview)
- [Preprocessing and Feature Selection](#preprocessing-and-feature-selection)
- [Model Training and Evaluation](#model-training-and-evaluation)
- [Results](#results)
- [Key Takeaways](#key-takeaways)
- [Contributing](#contributing)
- [Libraries](#libraries)
- [License](#license)


## Getting Started

### Prerequisites

Ensure you have the following libraries installed:

- `pandas`
- `seaborn`
- `matplotlib`
- `scikit-learn`

You can install them using pip:

```bash
pip install pandas seaborn matplotlib scikit-learn
```

### Running the Code

To run the code, execute the `california_housing_lr.py` script. The script will load the data, preprocess it, perform feature selection, and train a Linear Regression model. 

```bash
python california_housing_lr.py
```

## Data Overview

This dataset was obtained from the StatLib repository ([Link](https://www.dcc.fc.up.pt/~ltorgo/Regression/cal_housing.html))

- [California Housing Dataset in Sklearn Documentation](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.fetch_california_housing.html)
- 20640 samples
- Features: 
    - `MedInc` median income in block group
    - `HouseAge` median house age in block group
    - `AveRooms` average number of rooms per household
    - `AveBedrms` average number of bedrooms per household
    - `Population` block group population
    - `AveOccup` average number of household members
    - `Latitude` block group latitude
    - `Longitude` block group longitude
- Target: Median house value for California districts, expressed in hundreds of thousands of dollars ($100,000)

This data is fetched directly using `fetch_california_housing` from `sklearn.datasets`.


## Preprocessing and Feature Selection

### Normalization

The data is normalized using `MinMaxScaler` to prepare it for training.

### Feature Selection

Several feature selection methods are explored:
- **SelectPercentile** and **SelectKBest**: Based on mutual information and f-regression.
- **Recursive Feature Elimination**, **SelectFromModel** and **Sequential Feature Selector**: Using Lasso & Ridge regressors as estimators.
- **PCA (Principal Component Analysis)**: To test and reduce dimensionality.


## Model Training and Evaluation

The Linear Regression model is trained on the processed dataset. The model's performance is evaluated using common metrics like Mean Squared Error (MSE) and R-squared.


## Results

The model achieves reasonable accuracy in predicting housing prices. Detailed plots and evaluation metrics are provided in the script.

Best method: Feature selection through f_regression scoring function with SelectKBest as the transformer
- **k**: [6]
- **MSE**: [0.5029]
- **R-squared**: [61.69%]

Visualizations include scatter plots of predicted vs. actual values and feature importance graphs.


## Key Takeaways

- Linear Regressor seems to cap at 62% R2 score even after treating with different feature selection and dimensionality reduction methods.
- The best scores across the board of selection methods are observed when the LR model is trained on all features (R2 = 0.6179, MSE = 0.5015).
- Near best scores are observed after applying feature selection, with a 0.28% increase in MSE when 2 least important features are dropped (R2 = 0.6169, MSE = 0.503).
- Further, if the feature threshold is set to 4, feature selection through SFS still provides near to best accuracy (R2 = 60.22%, MSE = 0.5222) with only a 2.39% reduction in R2 score compared to the f_test variant with k=6.
- The scores for when selecting with RFE on a Lasso estimator significantly drop if scaled data is used. Hence RFE is build on raw data.
- Future prospects: comparing with Decision Tree and Random Forest regressors, implementing robust tuning using Cross Validation techniques, building a pipe object for simultaneously testing all methods and/or models.


## Contributing

Contributions are welcome! Please open an issue or submit a pull request with your changes.


## Libraries 

**Language:** ![Python](https://img.shields.io/badge/-Python-43B02A?style=flat&logo=python&logoColor=white)

**Packages:** ![Scikit-Learn](https://img.shields.io/badge/-Scikit%20Learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![Matplotlib](https://img.shields.io/badge/-Matplotlib-F05032?style=flat&logo=matplotlib&logoColor=white)
![Seaborn](https://img.shields.io/badge/-Seaborn-3776AB?style=flat&logo=seaborn&logoColor=white)
![Pandas](https://img.shields.io/badge/-Pandas-150458?style=flat&logo=pandas&logoColor=white)


## Acknowledgements

Below references can be used for further exploration: 

 - [Predictive Modelling with the California housing dataset](https://inria.github.io/scikit-learn-mooc/python_scripts/datasets_california_housing.html)
 - [Reference Article](https://medium.com/@basumatary18/implementing-linear-regression-on-california-housing-dataset-378e14e421b7)
 - [Multivariable Linear Regression](https://bookdown.org/ripberjt/labbook/multivariable-linear-regression.html)


## License

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)
---
