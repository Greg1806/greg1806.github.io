# Learning to Rank, Hotel Ranking exercise - Kaggle

## Context
For each searches done by customers expedia wants to show the most relevant hotel first. Using data from previous bookings the objective is to rank hotels based on their relevancy to each customers.

<img src="images/ranking_hcom.jpg?raw=true"/>

## Objectives
**Primary:** Predict best rankings with hotels on top which have the highest chances of being booked
<br> **Secondary:** Compare performance of pointwise and pairwise models for ranking

## Content
* **EDA and feature engineering**
  * Handling NULLs
  * Update data types
  * reducing cardinality for features with high number of categories (keeping only Top X categories and setting others to "other")
* **Analysis**
  * Correlation matrix
  * Charts of features most correlated to target

<img src="images/ranking_corr.jpg?raw=true"/>

* **ML tasks**
  * Encoding of categorical features, Scaling of continuous features, Train_test_split
  * Models: 
    * pointwise: Logistic Regression (linear) and RandomForest (non-linear) including GridSearchCV => result of 0.44
    * pairwise: XGBRanker from XGBoost => result of 0.47


### Conclusion
* **Pairwise overperforming pointwise** – For this specific exercises I could see XGBRanker overperforming RandomForestClassifier even if the RF was tuned and XGBRanker.
