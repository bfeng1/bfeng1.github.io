## Computer Vision: YOLOv8 on Traffic Detection

**Project description:** 
In today's digitally driven world, computer vision stands as a cornerstone of technological innovation, offering machines the ability to perceive and interpret visual information much like the human eye. From autonomous vehicles navigating bustling city streets to facial recognition systems securing our smartphones, the applications of computer vision are ubiquitous and far-reaching.

Among the myriad algorithms powering computer vision systems, one standout is YOLO—You Only Look Once. YOLO represents a paradigm shift in object detection, offering unparalleled speed and accuracy by simultaneously predicting bounding boxes and class probabilities for multiple objects within a single pass through the neural network. In simple terms, YOLO enables machines to swiftly identify and categorize objects in images or video streams with remarkable efficiency.

Now, imagine leveraging the capabilities of YOLO to tackle a pressing real-world challenge: traffic sign detection. In a world where road safety is paramount, accurately identifying and interpreting traffic signs is crucial for ensuring smooth traffic flow and preventing accidents. This is where our project comes into play.

**Main Objectives**

* Check the datasets
* Understand Model YOLOv8
* Train the YOLOv8 model and analyze the results
* Test the final model

### 1. Check the datasets

- In the provided dataset, there are a total of 4969 samples that are images containing different traffic signs. We have 3530 images in the training dataset and 801 images for validation. 
- For this dataset, there are a total of 15 different classes used for labels. Those are: ['Green Light', 'Red Light', 'Speed Limit 10', 'Speed Limit 100', 'Speed Limit 110', 'Speed Limit 120', 'Speed Limit 20', 'Speed Limit 30', 'Speed Limit 40', 'Speed Limit 50', 'Speed Limit 60', 'Speed Limit 70', 'Speed Limit 80', 'Speed Limit 90', 'Stop']

Here are some examples of the input images for the model training:

<img src="images/thumbnail_images/ml_p0_figure1.png?raw=true"/>

### 2. Understand Model YOLOv8

YOLO, which stands for "You Only Look Once," is a groundbreaking object detection algorithm in computer vision. Unlike traditional object detection algorithms that involve multiple stages of processing, YOLO processes the entire image in a single pass through a convolutional neural network (CNN). This approach allows YOLO to achieve real-time object detection with impressive speed and accuracy.

Here are some technical details of the YOLO model's object detection method:

1. The algorithm will take the input image and split it into a grid of cells. Each cell will predict bounding boxes and a confidence score for each box. The bounding boxes indicate the location of the detected object in the images and the confidence value indicates the model's certainty of the prediction.

2. Other than the confidence score for each bounding box, YOLO also predicts an "objectness" score for each box that indicates the likelihood that the box contains a meaningful object, not just background clutter.

3. Last but not least, YOLO also predicts the class for each bounding box detected. The probability generated measures the likelihood of the detected object belonging to different predefined classes.

4. To generate the final output, YOLO will combine a set of bounding boxes from previous steps, each bounding box is associated with its class label and confidence score. Those combined bounding boxes then can represent the objects detected along with their location in the image and classified label. To prevent redundancy and improve localization accuracy, YOLO applied a technique called Non-Maximum Suppression (NMS) to those predicted bounding boxes. NMS selects the most confident bounding boxes while suppressing overlapping detections with lower confidence scores.

**Before fine-tuning, the YOLOv8 model did not perform very well on the traffic detections that we labeled**, here are some examples of the prediction from a pre-trained model:

<img src="images/thumbnail_images/ml_p0_figure2.png?raw=true"/>
  
### 3. Train the YOLOv8 model and analyze the results

#### Interpretation of the plots

<img src="images/thumbnail_images/ml_p0_figure3.png?raw=true"/>

Precision-confidence Curve: a graphical representation of how the precision of the model changes at different confidence levels. In the first plot, we can see that the precisions of the model increase for all classes as the confidence increases. We can reach to precision score of 1 for all classes when the confidence threshold is 0.932.

<img src="images/thumbnail_images/ml_p0_figure4.png?raw=true"/>

Recall-confidence Curve: a graphical representation of how recall of the model changes at different confidence levels. In the second plot, we can see that the recall of the model decreases for all classes as the confidence increases. The recall for all classes is 0.95 when the confidence threshold is 0.

<img src="images/thumbnail_images/ml_p0_figure5.png?raw=true"/>

Precision-Recall Curve: a graphical representation of the trade-off between precision and recall for different thresholds used. From the third plot, we see that the model's precision decreases as the recall increases. When using the IoU threshold (intersection over Union) of 0.5, the model can achieve mAP (mean average precision) of 0.901.

<img src="images/thumbnail_images/ml_p0_figure6.png?raw=true"/>

F1-Confidence Curve: a graphic representation of how the F1 score of the model changes at different confidence levels. Since the F1 score is calculated using both precision and recall scores, it can be a good visualization of how the model is performing overall. From the fourth plot, we can see that the F1 score increases and then decreases as the confidence threshold increases. When setting the confidence threshold as 0.465, we can achieve an F1 score of 0.87 for all classes.

<img src="images/thumbnail_images/ml_p0_figure7.png?raw=true"/>

Confusion Matrix: a table that allows visualization of the performance of a classification model by summarizing the correct and incorrect classifications. The diagonal of the table shows all the positives made by the model. As we can see from the fifth plot, most of the high-value numbers in the table are in the diagonal line, so we can conclude that the model can make correct predictions in most cases.

<img src="images/thumbnail_images/ml_p0_figure8.png?raw=true"/>

Results plot during training: a combination of different metrics measured during the training process. In the sixth plot, we can see multiple visualizations of different metrics values changes over different epochs. To better understand the results, we need to understand the different loss values measured first.

box_loss: is also known as localization loss or regression loss. It measures the discrepancy between the predicted bounding box coordinates and the ground truth bounding box coordinates for each object in the image.

cls_loss: is known as classification loss. It measures the accuracy of the predicted class labels assigned to each bounding box.

dfl_loss: is known as domain-fused loss. It measures the discrepancy between feature representations learned by the model across different domains. The goal of minimizing dfl loss is to better align the feature representations across different domains so that the model can improve the performance in real-world scenarios where the testing data may differ from the training data.

From the plots included in the sixth figure, we can see that all of those three loss values decrease and the precision and recall scores increase as more epochs are trained.

### 4. Test the model on test data

Based on the results obtained from the test images, we can see a significant performance increase from the pre-trained model. YOLOv8 has performed very well after training and can detect most objects that we specified in the dataset. Here are some detections made by the final model in the test dataset:

<img src="images/thumbnail_images/ml_p0_figure9.png?raw=true"/>

### Conclusion

In this project, we utilized the YOLO model for traffic detection, starting with familiarization and testing of a pre-trained model. Then, we have fine-tuned the model with our dataset. The retrained model shows a significantly improved performance. We have also analyzed different metrics and plots obtained during the training process. All of those plots show the confirmation of enhanced accuracy.

#### Current Limitation & Future work

To improve the performance further, we could involve further optimization by adjusting parameters used in the YOLO model, for this project, I have only used default parameters mostly, but we can try out different parameter combinations to find the optional model to use.

During the analysis of the training results, we noticed that the model performance continued to increase in different metrics as the number of epochs increased. So we can continue to train the model with more epochs, this should result in a performance increase as well.

Last but not least, the provided dataset only contains ~3.5K training images. If we can expand the training dataset further by including more samples, we could obtain even better results.


For more details about this project, please visit my Kaggle notebook [Computer Vision: YOLOv8 on Traffic Detection](https://www.kaggle.com/code/binfeng2021/computer-vision-yolov8-on-traffic-detection)
