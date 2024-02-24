## House Price Prediction-EDA & Feature Engineering

**Project description:** 
Among all versions of the American dream that are out there, one of the most frequently appeared terms would-be homeowner. For many people, owning a home is a big deal not only financially, but in the whole life journey. However, it is not an easy process to obtain a house that fits your personal and financial needs. One of the major factors to consider would be the price of the house.

The goal of this project is to develop a tool to estimate house prices using some basic information that can be easily accessed. Of course, the estimation cannot be always accurate due to many other factors that can play a big part in the prices, but the home buyer can at least have a good starting point for the price negotiation process.

This project will contain three main parts with focuses on EDA and feature engineering:
* Exploratory Data Analysis (EDA)
* Feature Engineering
* Model development

### 1. Exploratory Data Analysis

Understand the features related to the house prices and explore the potential issues with those features that might need further clearing or processing. 

<img src="images/thumbnail_images/house_price_prediction.png?raw=true"/>

### 2. Feature Engineering

During the data collection process, the marker-based system has a higher frequency than the marker-less system. To make the comparison accurate, we have decided to under-sample the data points collected by the marker-based system. 

```python
from sklearn.utils import resample

# resample the golden system dataset, and then smooth the data with a low-pass filter
resample_data = resample(test_gold, n_samples = 366, replace = False, random_state = 0).sort_index()
```

### 3. Compare the knee angles and the ankle angles obtained in two systems



### 4. Conclusion

* Knee angle values measured by our system obtained a MAE of 11.07% and a RMSE of 15.59%;
* Ankle angle values measured by our system obtained a MAE of 18.94% and a RMSE of 25.45%;
* Applying a low pass filter did not change the significance of our system measurement, but it is very helpful to remove the system noise to give a smooth plot;
* The knee angle measured by our system is more accurate compared to the ankle angle measurements. The reason is that OpenPose does not perform well with foot key points detection. Since we calculate the ankle angle using the big toe estimation, the accuracy for the ankle angle measurement can be effected. 

For more details see [Kaggle - Running Analysis](https://www.kaggle.com/code/binfeng2021/running-analysis).

