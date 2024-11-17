## Portfolio

### Professional Experience

**Business Intelligence Engineer @ TopRx, LLC (Apr 2022 - Present)**
-	Developed and implemented a classification model using TensorFlow and SQL to generate personalized purchase lists, increasing the sales success rate by 50% for phone-based channels.
-	Leveraged Census geospatial data to enhance customer insights, improving product recommendations and pitch lists, resulting in a 20% increase in new item success rates and stronger customer relationships.
-	Created a predictive model in Scikit-learn leveraging historical trends and current customer buying habits to identify high-risk customers, enabling proactive risk mitigation strategies that reduced customer churn by 10%.
-	Utilized DOMO and Python to extract, transform, and visualize data from multiple sources, providing executives with comprehensive and intuitive insights that informed strategic decisions.


**Research Assistant @ University of Memphis (Jun 2020 - Dec 2021)**
-	Developed an automated markerless motion capture system to collect over 200,000 image frames of athletes' physical motions.
-	Achieved 80% accuracy in identifying improper knee placement during vertical jumps using a trained KNN classifier.
-	Compared our markerless gait system versus QUALYSIS, identified improvements, and communicated findings to stakeholders with actionable insights.

---
### Education
					       		
- M.S., Electrical and Computer Engineering	| University of Memphis (_December 2021_)	 			        		
- B.S., Electrical and Computer Engineering	| University of Memphis (_May 2020_)

---
### Certifications

**Machine Learning & Data Science**
- [DeepLearning.AI TensorFlow Developer Professional Certificate](https://www.coursera.org/account/accomplishments/professional-cert/Z5UVZJAB7MP2?utm_source=link&utm_medium=certificate&utm_content=cert_image&utm_campaign=sharing_cta&utm_product=prof)
- [Google Data Analytics Professional Certificate](https://www.coursera.org/account/accomplishments/verify/G5V2UUC7X43M?utm_source=link&utm_medium=certificate&utm_content=cert_image&utm_campaign=sharing_cta&utm_product=course)

**SQL**
- [SQL (Advanced) Certificate](https://www.hackerrank.com/certificates/a10305eaa375)
- [SQL (Intermediate) Certificate](https://www.hackerrank.com/certificates/b16aa56d0f1c)

**Cloud Services**
- [AWS Certified Cloud Practitioner (expires on 05/2026)](https://www.credly.com/badges/5de091c9-1567-4bb2-86e2-c09f007b9c8c/linked_in_profile)


---
### Projects

**Machine Learning**

[Question Answering with Chinese History Book](https://www.kaggle.com/code/binfeng2021/question-answering-with-chinese-history-book#Main-Goal)

- Process a pdf document of a Chinese hitory book, and use it as reference to answer fact-based questions related to Chinese history.
- Embed the texts from the book and find the most similar text chunk as context to answer provided questions.
- Build a questions answering bot that can process the information and find the most likely answer based on contexts

**Skills: Python, Nature Language Processing, Language Model, Question Answering, Text Embedding**

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
**Data Visualization**

[Superstore Sales Overview](https://public.tableau.com/app/profile/bin.feng6585/viz/SalesBIDashboardSample/Dashboard2#1)

Create an interactive dashboard in Tableau to draw insights into the overview of superstore sales.  

**Skills: Tableau, Data Visualization, Reporting**

<img src="images/thumbnail_images/superstore sales overview.png?raw=true"/>

[Genative AI Search Trend in the US](https://public.tableau.com/app/profile/bin.feng6585/viz/GenerativeAISearchTrend2024/Dashboard1)

Create an interactive dashboard in Tableau to draw insights into the search trend for different generative AI models in early 2024.  

**Skills: Tableau, Data Visualization, Reporting**

<img src="images/thumbnail_images/gen AI search in US.png?raw=true"/>

[New York Airbnb Investment by Location](https://public.tableau.com/app/profile/bin.feng6585/viz/NewYorkAirBnBAnalysis/Dashboard1)

By looking into the New York Airbnb records from 2008 to 2015, I built a dashboard in Tableau to enhance the decision-making process for choosing locations and properties for Airbnb investment in New York. 

**Skills: Tableau, Data Visualization, Reporting**

<img src="images/thumbnail_images/Airbnb_in_new_york.png?raw=true"/>

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
