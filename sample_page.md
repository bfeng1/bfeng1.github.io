## Data Analysis Project 1: Gait Analysis Performance Comparison

**Project description:** 
We have a running dataset that was collected using our proposed markerless gait analysis system, and another dataset was collected simultaneously by Qualisys(a marker-based gait analysis system that is the standard of the current market). We want to compare the accuracy of our system using the Qualisys system as the golden rule and find the areas of improvement. The main objectives for this analysis are:
* compare the knee angle measurements from two systems
* compare the ankle angle measurements from two systems
* create visualizations for both systems and angles

### 1. Smooth the data points collected by the markerless system using [Savitzky–Golay filter](https://en.wikipedia.org/wiki/Savitzky%E2%80%93Golay_filter)

Since the data points collected by the markerless system have a lot more noise compared to the marker-based system. To remove some of the noise, we have tried to apply a filter and this process has helped us get much better results.

```python
test_our['filtered our sys knee angle'] = savgol_filter(test_our['right knee angle'], 25, 2)
test_our['filtered our sys ankle angle'] = savgol_filter(test_our['right ankle angle'], 25, 2)
```

### 2. Resample the data samples collected by the marker-based system
During the data collection process, the marker-based system has a higher frequency than the marker-less system. To make the comparison accurate, we have decided to under-sample the data points collected by the marker-based system. 

```python
from sklearn.utils import resample

# resample the golden system dataset, and then smooth the data with a low-pass filter
resample_data = resample(test_gold, n_samples = 366, replace = False, random_state = 0).sort_index()
```

### 3. Compare the knee angles and the ankle angles obtained in two systems

<img src="images/dummy_thumbnail.jpg?raw=true"/>

### 4. Conclusion

Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. 

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
