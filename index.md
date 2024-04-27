## Portfolio

### Professional Experience

**Business Intelligence Engineer @ TopRx, LLC (Apr 2022 - Present)**
-	Developed and implemented a classification model for personalized customer recommendations, resulting in a 50% increase in success rates compared to previous methods.
-	Designed and constructed data dashboards to monitor key performance indicators (KPIs) for executive decision-making, enhancing data-driven insights and strategic planning.
-	Spearheaded the creation of customer segmentation tools for the sales department's promotional campaigns, contributing to a revenue increase of over 10% through targeted marketing strategies. 
-	Engineered tools to analyze customer interactions with sales representatives, facilitating the generation of optimized call schedules to boost customer engagement and satisfaction levels.

**Research Assistant @ University of Memphis (Jun 2020 - Dec 2021)**
-	Developed an automated marker-less motion capture system to collect over 200,000 image frames of athletes' physical motions.
-	Achieved 80% accuracy in identifying improper knee placement during vertical jumps using a trained KNN classifier.
-	Conducted a comparative analysis of our marker-less gait analysis system with QUALYSIS, identifying areas for improvement.
-	Effectively communicated research findings to stakeholders, translating complex data into actionable insights.

---
### Education
					       		
- M.S., Electrical and Computer Engineering	| University of Memphis (_December 2021_)	 			        		
- B.S., Electrical and Computer Engineering	| University of Memphis (_May 2020_)

---
### Projects

**Machine Learning**

[Nature Language Processing: Build GPT Tokenizer from Scratch](https://www.kaggle.com/code/binfeng2021/what-is-bbpe-tokenizer-behind-llms)

In this post, we have gone through the BBPE tokenizer with many details. First, in order to understand why BBPE tokenizer is a popular choice for LLMs, we have checked other types of tokenizer, such as word-level tokenizer, character-level tokenizer, or byte level using UTF-8 directly. All of those tokenizers have their own advantage, but when used in the LLMs task, they all lack some key factors. On the other hand, the BBPE tokenizer starts with a very small base vocabulary but also provides the flexibility to add new vocabulary by merging frequently appeared pairs. So the LLMs research can find a good balance between the good size of vocabulary and the good size of encoded tokens. This is the one advantage BBPE tokenizer can provide while other methods lack. Then, we went through the initial BPE algorithm, and the byte-level implementation step by step. To train a BBPE tokenizer, all training texts will be encoded into raw bytes first (normally in UTF-8). Next, we will perform the BPE algorithm to find the most frequently appeared pairs to merge. We will repeat this step until we reach the desired vocabulary size. Finally, we will create the final vocabulary dictionary and all merge rules. Those two things will be stored for future encoding and decoding tasks.

[Computer Vision: YOLOv8 on Traffic Detection](https://www.kaggle.com/code/binfeng2021/computer-vision-yolov8-on-traffic-detection?rvi=1)

In this project, we utilized the YOLO model for traffic detection, starting with familiarization and testing of a pre-trained model. Then, we have fine-tuned the model with our dataset. The retrained model shows a significantly improved performance. We have also analyzed different metrics and plots obtained during the training process. All of those plots show the confirmation of enhanced accuracy.

**Skills: Python, Computer Vision, Model Finetuning, Metrics Evaluation**

<img src="images/thumbnail_images/yolo_with_traffic_detection.png?raw=true"/>

[Regression Problem: House Price Prediction](https://www.kaggle.com/code/binfeng2021/regression-problem-house-price-prediction?rvi=1)

Throughout the project, we have performed exploration data analysis to understand the dataset and the relationship between given features and the house price. Then, we cleaned and preprocessed the dataset. Lastly, We aimed to create a model that can predict house prices with only the provided features. As we can see from the final results, we can obtain a pretty decent performance using the random forest regression model on the unseen data.

**Skills: Python, Regression Model, EDA, Data Cleaning, Feature Engineer**

<img src="images/thumbnail_images/house_price_prediction.png?raw=true"/>

---
**Data Analysis**

[Gait Analysis Performance Comparison](https://www.kaggle.com/code/binfeng2021/running-analysis)

We have a running dataset that was collected using our proposed markerless gait analysis system, and another dataset was collected simultaneously by Qualisys(a marker-based gait analysis system that is the standard of the current market). We want to compare the accuracy of our system using the Qualisys system as the golden rule and find the areas of improvement. 

<img src="images/thumbnail_images/running_analysis.png?raw=true"/>

---
[Data Science Salary Analysis](https://www.kaggle.com/code/binfeng2021/data-visualization-data-science-salary-analysis)
<img src="images/thumbnail_images/data_science_salary_analysis.png?raw=true"/>

---

### Publications
- [Marker-less motion capture system using OpenPose](https://www.spiedigitallibrary.org/conference-proceedings-of-spie/12101/121010B/Marker-less-motion-capture-system-using-OpenPose/10.1117/12.2619059.short/)
  
---
