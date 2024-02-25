## Credit Risk Prediction & Model Explainability

**Project description:** 

* Perform EDA to understand what features could indicate the risk of loan default
* Build a classification model to predict the potential default loans
* Use grid search for hyperparameter tuning to achieve the best performance on the random forest tree model.
* Use permutation importance to understand which features are the most critical for the overall model performance
* Use SHAP to form a better understanding of how the chosen model is working to make each prediction. This can help us understand how the values within each feature affect the prediction.
* Through the exercise, understand the process of credit risk analysis in banking.

### 1. Exploratory Data Analysis & Data Cleaning

Understand the features related to the house prices and explore the potential issues with those features that might need further clearing or processing. 

One of the techniques used in this project to fill the missing values is the KNN imputer from fancyimpute. It shows a better performance compared to other common techniques, such as filling by the median values, or highest occurred values. However, it is a relatively slow function to run, especially when we have a large data frame. 
``` python
from fancyimpute import KNN
knn_imputer = KNN()
filled_data = knn_imputer.fit_transform(df)
```
 
### 2. Model Building

For this project, I have tried logistic regression model and the Random Forest Classification model. We can see there is a significant performance increase using RFC than using LR model. However, one of the downsides is the trade of interpretation. So, this project has tried some techniques to help understand how RFC made the predictions. 

```
Logistic Regression Model performance:
the model accuracy score is  0.7982200398956575
the model f1 score is 0.2507122507122507
where recall score is 0.1510989010989011 and precision score is 0.7357859531772575

Random Forest Classification Model Performance:
the model accuracy score is  0.9350928341261316
the model f1 score is 0.8344422700587084
where recall score is 0.7321428571428571 and precision score is 0.9699727024567789
```

### 3. Model Explanation
To understand how the model made the prediction, we need to be able to know how important each feature is and how they are affecting the predicted values. Two common methods are permutation importance and SHAP importance. Here are the similarities and differences between the two importance calculations.
```
Permutation importance is calculated on the entire dataset and measures how much the accuracy of the whole dataset changes by eliminating a feature.

It can be used to:

* Understand which features to keep and which to exclude.
* Check for data leakage
* Understand what features are most important to model accuracy
* Guide additional feature engineering

SHAP importance SHAP importance is calculated on row level and can be used to understand what is important to a specific row. The values represent how a feature influences the prediction of a single row relative to the average outcome in the dataset.

It can be used to:

* Understand which features most influence the predicted outcome.
* Dive into a feature and understand how the different values of that feature affect the prediction.
* Understand what is most influential on individual rows or subsets within the data.

Key Differences

Permutation importance can only measure the importance of features to the entire dataset, not in specific rows. SHAP importance can be used to see the feature importance in a row level.
Permutation importance does not include a direction in which SHAP importance can be directional.
The magnitude of the SHAP importance can be used to understand how the values within a feature influence the outcome, while Permutation importance values are used to estimate how important the feature is to the whole dataset.
```

### 4. Conclusion
#### Permutation Importance Conclusion

In the permutation importance table, we can see which features have the biggest impact on the overall model accuracy. Based on the importance rank, we can perform feature selection to reduce the dimension of the dataset if we do not have sufficient dataset size and worry about overfitting issues.

#### SHAP Importance Conclution

In the SHAP chart, we can see how each feature contributes to the final prediction of loan default. As we can see each feature contributes in a way that makes business sense.

For example:

a person who rents (person_home_ownership_RENT = 1) shows a higher chance of loan default.
loan with grade A (loan_grade_A = 1) has a smaller chance of loan default.
higher personal income (person_income) shows a smaller chance of loan default.

#### Main Takeaway from a business perspective
A person's annual income, employment history length, loan grade, and credit history length have a negative relationship with the risk of loan default. The higher the annual income, the longer the employment length, the higher the loan grade or longer credit history a person has, the less likely a loan default might happen for that person.
The loan's interest rate and loan percent income have a positive relationship with the risk of loan default. The higher a loan's interest rate or higher the loan percent income ratio is, the loan will have a higher risk of loan default.
A person's age and loan amount do not seem to have a strong correlation with the potential loan default risk.
In addition, there are other factors that can differentiate a person with a higher risk of loan default and the one with lower risk:
Having a home or mortgage could indicate a lower loan default risk compared to the ones who rent;
Different types of loans could associate different levels of loan default risks;
Having a default on file could indicate a higher loan default risk compared to the ones without any default on files.

For more details see [Kaggle - Credit Risk Prediction & Model Explainability](https://www.kaggle.com/code/binfeng2021/credit-risk-prediction-model-explainability#Main-Takeaway-from-a-business-perspectie).



