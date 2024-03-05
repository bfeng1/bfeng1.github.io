## House Price Prediction-EDA & Feature Engineering

**Project description:** 
Among all versions of the American dream that are out there, one of the most frequently appeared terms would-be homeowner. For many people, owning a home is a big deal not only financially, but in the whole life journey. However, it is not an easy process to obtain a house that fits your personal and financial needs. One of the major factors to consider would be the price of the house.

The goal of this project is to develop a tool to estimate house prices using some basic information that can be easily accessed. Of course, the estimation cannot be always accurate due to many other factors that can play a big part in the prices, but the home buyer can at least have a good starting point for the price negotiation process.

This project will contain three main parts:

* Exploratory Data Analysis (EDA)
* Feature Engineering
* Model development

We will explore the different models and compare their performances. Once we select a model, we will fine-tune the hyperparameters to achieve the best results possible. 

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
2. Built some machine learning models and compared their performances. The ML models I have tried are linear regression, ridge regression, lasso regression, and random forest regression models. The evaluation metrics used are mean absolute error (MAE), mean squared error (MSE), and r2 score. 

<img src="images/thumbnail_images/ml_p1_figure1.png?raw=true"/>

3. In the comparison, we can see that random forest regression has significantly better results compared to others. So we will fine-tune the hyperparameters to pursue a better performance. 
<img src="images/thumbnail_images/ml_p1_figure2.png?raw=true"/>

4. Finally, we will use the model to predict the house price on the testing data that we have separated prior, here is the final result we obtained:

```
MAE on testing data: 152845.7492622322
MSE on testing data: 835146288093.7261
R2-Score on testing data: 0.9059097971404966
```

### 4. Conclusion

This exercise has mainly focused on EDA and feature engineering practices. After cleaning and preprocessing the given dataset, we then built some machine learning models to estimate the house price. As we can see from the final results, we can obtain a pretty decent performance using the random forest regression model. 

#### Limitation of this project

1. The dataset we used does not include every state or city in the USA, and most of the samples are collected in New York, New Jersey, Massachusetts, and Connecticut. So for some locations, we do not have sufficient data samples collected for the model to learn.
2. We have only tried some linear models and a random forest model, to discover potentially better results, other ML models, such as decision trees, or SVM models, or some neural networks can be tested and compared as well. 
3. Because of limited computation power, I did not run a frid search with many different hyperparameter options. But that can be done and potentially improve the performance further if we can try more combinations of hyperparameters.  

For more details see [Kaggle - House Price Prediction](https://www.kaggle.com/code/binfeng2021/house-price-prediction-eda-feature-engineering).

