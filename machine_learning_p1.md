## House Price Prediction-Model Selection

**Project description:** 

This project focuses on utilizing machine learning regression models to predict house prices based on provided features. We will build and evaluate several different models to determine their effectiveness in accurately forecasting housing prices. By comparing the performance of various algorithms, we aim to identify the most reliable method for predicting real estate values. This project offers a professional exploration of predictive modeling techniques applied to the real estate domain, providing valuable insights into the factors influencing house prices. 

This project has tried out the following regression models:
* Linear Regression
* GLM
* Lasso
* SVM Regression
* Random forest
* XGboost
* Boost

### 1. Exploratory Data Analysis & Data Cleaning

Understand the features related to the house prices and explore the potential issues with those features that might need further clearing or processing. 

Here are performed data cleaning steps:
1. Removing outliers
2. Imputate missing values
3. Change some numerical variables that are supposed to be categorical
4. Fix the skewness of variables

<img src="images/thumbnail_images/house_price_prediction_model_selection.drawio.png?raw=true"/>

 
### 2. Model Building

1. Develop different regression models to make the prediction, and obtain its performance:

I have used the RMSE as the metrics to determine the performance:

```python
n_folds = 5
def rmsle_cv(model, name):
    kf = KFold(n_folds, shuffle = True, random_state = 42).get_n_splits(train_X)
    rmse = np.sqrt(-cross_val_score(model, train_X.values, train_y.values, scoring = "neg_mean_squared_error", cv = kf))
    print('score for the model {} is {} ({})'.format(name, round(rmse.mean(),4), round(rmse.std(),4)))
    return rmse.mean()
```
With the provided function, we can generate all RMSE scores for all provided models as following:
```
[(Pipeline(steps=[('standardscaler', StandardScaler()),
                  ('lasso', Lasso(alpha=0.0005, random_state=1))]),
  0.138540903420309,
  'Lasso Regression'),
 (Pipeline(steps=[('standardscaler', StandardScaler()),
                  ('randomforestregressor',
                   RandomForestRegressor(max_depth=35, random_state=0))]),
  0.1489204951346239,
  'Random Forest Regressor'),
 (XGBRegressor(base_score=None, booster=None, colsample_bylevel=None,
               colsample_bynode=None, colsample_bytree=0.4603,
               enable_categorical=False, gamma=0.0468, gpu_id=None,
               importance_type=None, interaction_constraints=None,
               learning_rate=0.05, max_delta_step=None, max_depth=3,
               min_child_weight=1.7817, missing=nan, monotone_constraints=None,
               n_estimators=100, n_jobs=None, nthread=-1, num_parallel_tree=None,
               predictor=None, random_state=None, randome_state=7,
               reg_alpha=0.464, reg_lambda=0.8571, scale_pos_weight=None,
               silent=1, subsample=0.5213, tree_method=None,
               validate_parameters=None, ...),
  0.16832474491753882,
  'XGBoost'),
 (Pipeline(steps=[('standardscaler', StandardScaler()),
                  ('svr', SVR(epsilon=0.2))]),
  0.22148051312875766,
  'Support Vector Regression'),
 (Pipeline(steps=[('standardscaler', StandardScaler()),
                  ('ridge', Ridge(alpha=0.002))]),
  0.22274294684680757,
  'Ridge Regression'),
 (Pipeline(steps=[('standardscaler', StandardScaler()),
                  ('linearregression', LinearRegression())]),
  0.22605354393768406,
  'Linear Regression')]
```

By comparing the results, the best performance model is 

```
Pipeline(steps=[('standardscaler', StandardScaler()),
                ('lasso', Lasso(alpha=0.0005, random_state=1))])
```

### 3. Conclusion

In summary, this project aimed to create a high-performance regression model to forecast house prices using given features. I've had the chance to explore different models, learning their upsides and downsides along the way. It's been a learning experience that's improved my skills and understanding of predictive modeling.

For more details see [Kaggle - (Structured Data project) House Price Prediction](https://www.kaggle.com/code/binfeng2021/structured-data-project-house-price-prediction).


