## Credit Risk Prediction & Model Explainability

**Project description:** 
In today's banking landscape, assessing and managing risk is crucial for maintaining financial stability and making responsible lending decisions. Traditional methods of evaluating loan risk rely on metrics like the probability of default, but with the advent of machine learning, there's an opportunity to enhance these methods. However, machine learning models can be opaque, making it difficult to understand how they arrive at their predictions.

This project aims to tackle this challenge by developing a machine-learning model to predict loan default probability accurately. More importantly, we'll make the model transparent and easy to understand using common techniques. By shedding light on how the model makes decisions, we hope to build trust and confidence among stakeholders in the banking sector.

Main objectives

- Conduct EDA to identify key risk indicators in loan default prediction.
- Develop a precise classification model for predicting potential loan defaults.
- Determine critical features using permutation importance analysis.
- Utilize SHAP to understand how model predictions are influenced by feature values.

### 1. Exploratory Data Analysis & Data Cleaning

Understand the features related to the house prices and explore the potential issues with those features that might need further clearing or processing. 

<img src="images/thumbnail_images/ml_p2_figure0.png?raw=true"/>
 
### 2. Model Development

For this project, I have tried the logistic regression model and the Random Forest Classification model. We can see there is a significant performance increase using RFC than using the LR model in all metrics we used.  

<img src="images/thumbnail_images/ml_p2_figure1.png?raw=true"/>

### 3. Model Explainability

The core focus of the project involved utilizing permutation importance and SHAP techniques to interpret the selected model. We identified which features significantly influenced the model's performance and which did not. By employing SHAP techniques, we delved deeper into understanding how the model makes its predictions. We examined specific features and their impact on the model's decision-making process, cross-referencing them with business insights to validate their accuracy.

Our overarching objective throughout this exercise was to enhance trust among business owners when dealing with 'black-box' models. Through these techniques, we were able to shed light on the inner workings of the model, providing valuable insights and guidance for future improvements should any anomalies arise during the process.

#### Here are some comparisons between the two techniques 

a. Permutation importance is calculated on the entire dataset and measures how much the accuracy of the whole dataset changes by eliminating a feature.

How it works: First, a baseline performance will be obtained. Then, to measure the importance of a feature, we will randomly shuffle that column in the training data, and get the performance for the new model. By checking how big/small the difference between the performance with baseline performance is, we can obtain the importance level for the given feature.

It can be used to:

Understand which features to keep and which to exclude.
Check for data leakage
Understand what features are most important to model accuracy
Guide additional feature engineering

b. SHAP importance SHAP importance is calculated on row level and can be used to understand what is important to a specific row. The values represent how a feature influences the prediction of a single row relative to the average outcome in the dataset.

It can be used to:

Understand which features most influence the predicted outcome.
Dive into a feature and understand how the different values of that feature affect the prediction.
Understand what is most influential on individual rows or subsets within the data.

c. Key Differences

Permutation importance can only measure the importance of features to the entire dataset, not in specific rows. SHAP importance can be used to see the feature importance in a row level.
Permutation importance does not include a direction in which SHAP importance can be directional.
The magnitude of the SHAP importance can be used to understand how the values within a feature influence the outcome, while Permutation importance values are used to estimate how important the feature is to the whole dataset.

**Permutation Importance Conclusion**

<img src="images/thumbnail_images/ml_p2_figure3.PNG?raw=true"/>

In the permutation importance table, we can see which features have the biggest impact on the overall model accuracy.

1. In our example, loan_percent_income is ranked as the top 1 most important feature for the model's accuracy. It makes sense since this feature combines the loan amount and the borrower's income, AKA debt-to-income ratio (DTI). It is one of the most commonly used values to evaluate how well / bad a person's finances.
2. From the permutation importance table, we can decide what other feature engineering steps might be needed. Such as removing some features that do not affect the model's performance.
3. Since the shuffling process is randomized, we can see the weight value is not a constant. (+-) value means the importance could change up and down within that range from one shuffle to another.

**SHAP Importance Conclution**

<img src="images/thumbnail_images/ml_p2_figure4.png?raw=true"/>

In the shap chart, we can see how each feature contributes to the final prediction of loan default.Below are a few features that we can use SHAP chart to explain how the model works and see if it aligns with business sense.

1. Notice that when we have a higher loan_percent_income value, we will see the SHAP value increase as well which means the predicted probability of loan default increases. That is what we expected from a business perspective as well. When a person's DTI is too high, they will be classified as too risky to lend money to because they have less safe margin in their finance.

2. person_home_ownership_RENT is a binary value, it is either 1 (rent) or 0 (not rent). We can see how the model treats renting as a feature to increase the predicted probability of loan default and not renting to reduce the predicted value. That makes business sense as well. Renting typically implies that the individual does not own a home or have significant assets. This could indicate a lack of financial stability or a lower ability to handle unexpected expenses.

3. For the model, the higher person_income is, the smaller the SHAP value is which means the predicted probability of loan default decreases. That makes business sense as well. When a person has a higher income, it will be easier for them to cover unexpected expenses, and this normally indicates a higher financial stability.

### 4. Conclusion

In this project, we dove into the world of data to understand what drives loan default risks. After crunching numbers and testing models, we found the random forest model to be our preferred model for predicting credit loan defaults, and it delivered solid results.

The real game-changer was using techniques like permutation importance and SHAP to demystify the model's decisions. We figured out which factors mattered most and how the model makes its predictions, all while keeping it grounded in real-world business sense.

Our goal? To build trust in these 'black-box' models and use insights to continuously improve. Armed with newfound clarity, we're ready to tackle any challenges that come our way and steer towards even better outcomes.

#### Future steps
* To reduce the running time, we did not perform any hyperparameter fine-tuning and we only compared the logistic regression model and the random forest model. To improve the performance further, we can try some other models, such as SVC, decision tree, or neural network models. And we can also try some new hyperparameter settings to see if we can increase the performance.
* For this project, we have used multiple metrics to evaluate. But in the real world, depending on the business needs, we might need to adjust the metrics accordingly. For example, if the bank wants to be more strict about only lending money to people with low risk, then we will need to increase the recall to avoid lending money to the wrong hands.

For more details see [Kaggle - Credit Risk Prediction & Model Explainability](https://www.kaggle.com/code/binfeng2021/credit-risk-prediction-model-explainability#Main-Takeaway-from-a-business-perspectie).



