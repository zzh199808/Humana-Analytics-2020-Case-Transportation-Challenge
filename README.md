# Humana-Analytics-2020-Case-Transportation-Challenge
Team Imperial Data Force

## Problem Framing
Upon receiving the problem statement, we recognize it as a classic classification problem as the label to be predicted is a binary variable. To tackle a classification problem, we did extensive research on a variety of  classification techniques and compared their applicability against our dataset. Random Forest Classifier of Python sklearn is selected by us due to its advantages in the following aspects:
* Easy to handle high dimensionality data
* Robust to outliers
* Quick speed
* Low bias 
* Bootstrap class weighting for imbalanced class

The shape of the training dataset indicates a potential dimensionality reduction problem. Additionally, imbalanced class, the distribution of outliers, NAs and “others” tend to cause bias during the removal or imputation of those unspecified or unobserved data. All in all, random forest classification is the approach we believe will bring the best fit to the dataset we had.

## Data Cleaning and Preparation 
  In order to clean the training dataset to meet the tidy data standard, we first look at missing values and anomalies by row and column. We conclude that NAs are very likely to be missing-not-at-random, which means pure removal will cause bias. Then we come to the conclusion that imputation with K-nearest neighbours is difficult to realize due to high dimensionality. As a result, imputation with mean for numeric features is applied and one-hot encoding method is applied to deal with NAs and anomalies for object-type features. 
  
  Among numeric variables, binary ones were identified and dealt with the way as object variables to retain NAs and outliers. Others are considered continuous values by nature. Additionally, the location-related features, such as state, county and zip-code, are specially treated. They are linked with external data of the 2020 US hospital census. Hospitals throughout the US are grouped by county code. The number of hospitals in each county is calculated and then merged with the training dataset on the county code column, which is formulated by combining the cnty_cd and the state_cd of the training dataset.
  
  We also observe that the training dataset is imbalanced. Only 14.66% of the patients claim to have transportation challenges. Oversampling of the minority class is applied to make full use of the rich data volume. We then use the mean ROC-AUC score across all folds and repeats, confusion matrix, and f1-score to evaluate the performance of the model.

## Data Modeling
We first use train_test_split from sklearn to divide the training dataset into train dataset and test dataset by 0.7:0.3, of which higher than default test-data size is chosen to mitigate overfitting. The overall accuracy is 97.65%.

![alt text](https://github.com/zzh199808/Humana-Analytics-2020-Case-Transportation-Challenge/blob/main/Confusion%20Matrix.png)
