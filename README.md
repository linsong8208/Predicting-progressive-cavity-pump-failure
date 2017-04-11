Welcome to the Predicting-progressive-cavity-pump-failure wiki!
## Objective
To predict below-mentioned issues in progressive cavity pump using historical data and thereby reducing unplanned downtime. 
* Rod string failure
* Flowline blockage
* Overheating of motor
* Entry of sand slugs into pipe

## Problem approach
* Per subject matter experts the predictor variables of different issues have been identified as shown on the right
* The solution to this problem requires “multiclass classification model “, that alerts the user about a specific issue. 
* This has been simplified to a binary class classification model that alerts the user about any abnormal condition, without stating the specific issue.
![](https://github.com/thiagunagu/Prediciting-progressive-cavity-pump-failure/raw/master/pumpapp.jpg)

## Methodology
### Data Extraction
Time series data for torque, pressure, and current were extracted from PI Asset Framework
### Data cleansing and preparation
* Interpolated values for uniform time intervals were obtained using PI datalink
* Dataset was classified into 2-day subsequences
### Feature Extraction
Median and standard deviation features that best represent the data set were computed. This is because a dataset comprising 576 values for 2 days can be represented by just three values: median, standard deviation, principal component
### Labeling
The provided dataset was unlabeled. Based on maintenance log, data points in respective time frames were labeled as "normal" or "abnormal"
### Training
The training dataset was provided as input to Matlab machine learning module. Several classifiers were trained to compare performances of different algorithms.
### Validation
The classifiers were validated and compared based on 10 fold cross validation.

## Conclusion
* The confusion matrix shown below summarizes the accuracy of the model. 
* The diagonal elements and the non-diagonal elements show the number of times the model was right and wrong respectively

![](https://github.com/thiagunagu/Prediciting-progressive-cavity-pump-failure/raw/master/pump.jpg)
### Ways to improve the accuracy of the model:
* In a span of 400 days, failures occur 1 - 3 times. Due to the rarity of failure events, the model doesn’t get adequate negative examples. This can be solved by providing synthetic failure data in order for the model to have more examples of negative datasets
* Extract and use other features such as range, mean in addition to median, standard deviation, and principal component to represent the subsequence
* Use different length of subsequence (i.e. 3 or 4 days instead of 2 days)
