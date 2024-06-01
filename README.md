![Logo](https://github.com/tree-shrew/linear-regressor-california-housing-dataset/blob/main/Bivariate%20Analysis.png)


# Project Title

Predictive Modelling using Linear Regression on the California Housing Dataset


## Implementation Details

- Dataset: California Housing Dataset [Details](https://github.com/tree-shrew/linear-regressor-california-housing-dataset#dataset-details)
- Model: [Linear Regressor](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html)
- Input: 8 features, none dropped
- Split: For a standard test size of 0.2, randon state 122 provided best results
- Scale: All features were scaled upon splitting
- Output: Median House Value


## Evaluation and Results


| *Metric*      | *Value*       |
| ------------- | ------------- |
| R2 Score      | 0.6316        |
| MSE           | 0.4713        |

The above quant results show that the Linear Regressor can represent ~63% of the variability observed in the target variable can be explained by the regression model. 

![Ground Truth vs Predicted Median Housing Values](https://github.com/tree-shrew/linear-regressor-california-housing-dataset/blob/main/Actual%20vs%20Predicted.png)


## Key Takeaways

What did you learn while building this project? What challenges did you face and how did you overcome them?
- The features 'AveRooms' & 'AveBedrms' are nearly perfectly correlated, however this multicollinearity does not impact target prediction. Infact dropping any one feature reduces the R2 score significantly. 
- Even though the features 'AveBedrms', 'AveOccup' and 'Population' have extremely low correlation with the target variable, they have an impact towards a better fit model.
- This model could be further improved upon by removing outliers from highly skewed features like 'Polpulation', 'MedInc', 'AveBedrms', 'AveRooms', 'AveOccup'.


## Dataset Details

This dataset was obtained from the StatLib repository ([Link](https://www.dcc.fc.up.pt/~ltorgo/Regression/cal_housing.html))

This dataset was derived from the 1990 U.S. census, using one row per census block group. A block group is the smallest geographical unit for which the U.S. Census Bureau publishes sample data (a block group typically has a population of 600 to 3,000 people).

A household is a group of people residing within a home. Since the average number of rooms and bedrooms in this dataset are provided per household, these columns may take surprisingly large values for block groups with few households and many empty houses, such as vacation resorts.

It can be downloaded/loaded using the sklearn.datasets.fetch_california_housing function.

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


## How to Run

Template code is provided in the `california_housing.ipynb` file. 

In a terminal or command window, navigate to the top-level project directory `linear-regressor-california-housing-dataset` (that contains this README) and run one of the following commands:

```bash
ipython notebook california_housing.ipynb
```  
or
```bash
jupyter notebook california_housing.ipynb
```
or open with Jupyter Lab
```bash
jupyter lab
```

This will open the Jupyter Notebook software and project file in your browser.


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