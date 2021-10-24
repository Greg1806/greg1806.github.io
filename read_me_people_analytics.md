# People Analytics, end-of-year clustering and prediction

## Context
At the end of each year managers are asked to bucket team members as high/medium/low performers. Idea is to try to understand if this bucketing/clustering could be done with ML clustering technics.

## Objectives
**Primary:** Analyze impact of key metrics on end-of-year performance
<br> **Secondary:** Predict end-of-year cluster based on full year performance

## Content
* **EDA**
* **Analysis**
  * Scatter plot
  * Boxplot
  * Correlation

<img src="images/peopleanalytics_boxplots.jpg?raw=true"/>
<img src="images/peopleanalytics_correlation.jpg?raw=true"/>

* **ML tasks**
  * Encoding, Scaler, Train_test_split
  * Models: Baseline, DecisionTreeClassifier, LogisticRegression, RandomForest, K-NN
  * Dimensionality reduction (PCA)

<img src="images/peopleanalytics_scatter.jpg?raw=true"/>

**Can any patterns be identified for high performers** – Yes, they are over-performing across selected input metrics
<br> **Are daily business expectations aligned with end-of-year review** – Yes, generally, a high performer will have out-performed on input metrics.
<br> **Could high performers be identified solely from a this set of input metrics?** – No, while a high performer will have generally out-performed on those input metrics, the inverse does NOT hold.  Out-performance on input metrics did not predict high placement. We can assume that this is due to the fact that input metircs are measuring the WHAT but not the HOW (how many glasses do you break when getting the job done?) which also plays an important role.
