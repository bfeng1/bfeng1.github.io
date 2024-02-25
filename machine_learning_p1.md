## House Price Prediction-Model Selection

**Project description:** 
This project aims to practice regression model development skills using structured datasets. 

This project will contain three main parts with focuses on EDA and feature engineering:
* Exploratory Data Analysis (EDA)
* Feature Engineering
* Model development

### 1. Exploratory Data Analysis

Understand the features related to the house prices and explore the potential issues with those features that might need further clearing or processing. 

<img src="images/thumbnail_images/house_price_prediction.png?raw=true"/>

### 2. Feature Engineering

To address the issues of features we have found during the EDA process and improve the model performance, some further data cleaning and preprocessing are necessary. 

* First, drop the samples that do not contain much valuable information
* Filling the missing values for bedroom and bathroom columns:
  1. Find out the median values for bedroom/bathroom counts using bathroom/bedroom or zip code as a group
  2. Fill the missing values for bedroom or bathroom with median values
* Fill in missing values for house size and acre lot
* Convert feature types
  
### 3. Model Building

1. Develop a baseline model using the median home price for each zip code. In case there are some missing zip codes in the testing set, we will fill them with median home prices for all areas.
2. Built a random forest model and compare the performance

```
Baseline performance:
{'MAE': 477345.5724341369,
 'MSE': 7138874827616.381,
 'R2-Score': 0.07159109108370909}

Model performance:
{'MAE': 38292.631562224946,
 'MSE': 193723909889.47775,
 'R2-Score': 0.9748062533446128}
```
The comparison between two performance:
```
MAE improvement: -91.98%
MSE improvement: -97.29%
R2-Score improvement: 1261.63%
```

### 4. Conclusion

This exercise has mainly focused on EDA and feature engineering practices. After cleaned and preprocessing the given dataset, we then built a basic random forest model to estimate the house price. As we can see from the final results, we can obtain a pretty decent performance.

We can improve the performance by further hyperparameters tuning, instead of using default values for the model.

For more details see [Kaggle - House Price Prediction](https://www.kaggle.com/code/binfeng2021/house-price-prediction-eda-feature-engineering).


