## Portfolio

### Professional Experience

**Business Intelligence Engineer @ TopRx, LLC (Apr 2022 - Present)**
-	Implemented a classification model for personalized customer recommendations, resulting in a 50% increase in success rates compared to previous methods.
-	Performed sentiment analysis on sales call transcript data, resulting in a 10% increase in lead conversion.
-	Spearheaded the creation of customer segmentation tools for the sales department's promotional campaigns, contributing to a revenue increase of over 10% through targeted marketing strategies.
-	Oversaw the creation, management, and upkeep of company data within the database, guaranteeing the quality and integrity of data utilized daily.
-	Designed and constructed data dashboards to monitor key performance indicators (KPIs) for executive decision-making, enhancing data-driven insights and strategic planning.

**Research Assistant @ University of Memphis (Jun 2020 - Dec 2021)**
-	Developed an automated markerless motion capture system to collect over 200,000 image frames of athletes' physical motions.
-	Achieved 80% accuracy in identifying improper knee placement during vertical jumps using a trained KNN classifier.
-	Compared our markerless gait system versus QUALYSIS, identified improvements, and communicated findings to stakeholders with actionable insights.

---
### Education
					       		
- M.S., Electrical and Computer Engineering	| University of Memphis (_December 2021_)	 			        		
- B.S., Electrical and Computer Engineering	| University of Memphis (_May 2020_)

---
### Projects

**Machine Learning**

[Nature Language Processing: Build GPT Tokenizer from Scratch](https://www.kaggle.com/code/binfeng2021/what-is-bbpe-tokenizer-behind-llms)

In this post, we have gone through the BBPE tokenizer with many details. First, in order to understand why BBPE (Byte-level Byte Pair Encoding) tokenizer is a popular choice for LLMs, we have checked other types of tokenizers, such as word-level tokenizers, character-level tokenizers, or byte level using UTF-8 directly. All of those tokenizers have their own advantage, but when used in the LLMs task, they all lack some key factors. On the other hand, the BBPE tokenizer starts with a very small base vocabulary but also provides the flexibility to add new vocabulary by merging frequently appeared pairs. So the LLMs research can find a good balance between the good size of vocabulary and the good size of encoded tokens. This is the one advantage BBPE tokenizer can provide while other methods lack. Then, we went through the initial BPE algorithm, and the byte-level implementation step by step. To train a BBPE tokenizer, all training texts will be encoded into raw bytes first (normally in UTF-8). Next, we will perform the BPE algorithm to find the most frequently appeared pairs to merge. We will repeat this step until we reach the desired vocabulary size. Finally, we will create the final vocabulary dictionary and all merge rules. Those two things will be stored for future encoding and decoding tasks.

**Skills: Python, Nature Language Processing, Byte-level Byte Pair Encoding, Large Language Models**

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

**Skills: Python, Data Analysis, Data Cleaning, Feature Engineer, Data Collection, Data Visualization**

<img src="images/thumbnail_images/running_analysis.png?raw=true"/>

---

### Publications
- [Marker-less motion capture system using OpenPose](https://www.spiedigitallibrary.org/conference-proceedings-of-spie/12101/121010B/Marker-less-motion-capture-system-using-OpenPose/10.1117/12.2619059.short/)

**Abstract:**

Motion capture systems are widely used for measuring athletic performance and as a diagnostic
tool in sports medicine. Standard motion capture systems record body movement using: (1) a set
of cameras to localize body segments; or (2) specialized suits in which inertial measurement
units are directly attached to body segments. Major drawbacks of these systems are limited
portability, affordability, and accessibility. This contribution presents a markerless motion
capture system using a commercially available sports camera and the OpenPose human pose
estimation algorithm. We have validated the proposed markerless system by analyzing the
human biometrics during running and jumping movements. The findings of this study
demonstrate that pairing a low-cost sports camera with artificial intelligence allows for highquality analysis of human movement. 
  
---
