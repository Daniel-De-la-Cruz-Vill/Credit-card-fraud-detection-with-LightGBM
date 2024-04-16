# Detecting fraudulent credit card transactions with LightGBM

![image](https://github.com/Daniel-De-la-Cruz-Vill/Credit-card-fraud-detection-with-LightGBM/assets/157164355/695fba8d-d929-4043-b59e-ebe293856d81)

## Fraud detection and imbalanced data
Fraud detection is one of the most common problems addressed with Machine Learning. An ML model can detect frauds in data by training itself on a large number
of samples and understanding their common patterns, thus being able to detect anomalies. Usually, these anomalies represent a very small minority in the data,
which leads to an imbalance problem. ML models have trouble training on imbalanced data because they make it so that, if the model simply predicts that none
of the data is fraudulent, the model obtains high accuracy scores without learning to detect frauds. Therefore, various techniques have been developed to handle
this case.

## The project

This project utilizes python code to build a LightGBM model that is able to predict fraudulent credit card transactions. The dataset used for this 
presents transactions that occurred in two days, where there are only 492 frauds out of 284,807 transactions. This means that more than 99% of the
data are legitimate transactions, causing an imbalance problem.

The following sections explain how the project was developed.

### Data exploration

This segment involved general exploratory analysis of the data set. We observed factors such as the type of features that would be worked with, the presence of outliers
in them, and their means and medians. However, aside from the class (fraud or not fraud), all data was numerical, and almost all features were the the result of 
PCA transformations and their background and meaning was not provided. This made this section short and simple as no conclusions could be drawn about customer behavior.

### Feature selection

There were 30 feautures in the dataset that could possibly help the model predict whether a transaction is fraudulent or not. There are several ways to determine whether a
feature should be used as a predictor. In this case,the Pearson correlation coefficient was used to eliminate the feautres with low correlation from the dataset. This led
to better performance because it makes the model learn from features that we know are useful instead of letting it determine it by itself. After feature selection, we only work
with 15 features.

### Outlier removal

An outlier is a data point that differs significantly from other points in the dataset. These outliers be consecuence of several factors, some of which are natural and some that
involve errors. However, extreme outliers make it difficult for ML models to generalize because they add training points that differ too much from the norm and "confuse" the model.
This is why it is important to identify the presence of outliers and treat them if they lower performance.

The dataset used in this project contained a large number of outliers that were hindering model performance. Therefore, we removed outliers by using the interquartile range (IQR).
After doing this, model performance increased considerably. That being said, removing outliers is not the only way of handling them. Other techniques might perform better.

### Handling data imbalance

The prepared dataset was then split into a train and test set. At this point is where three techniques were employed for handling the data imbalance problem: random undersampling,
random oversampling, and SMOTE. The techniques consist in the following:

* Random undersampling: removing random samples of the majority class until its number equals that of the minority class.
* Random oversampling: repeating random samples of the minority class until its number equals that of the majority class.
* Synthetic minority oversampling technique (SMOTE): creating new samples of the minority class that belong to the same feature space of the original samples.

After applying these techniques, four pairs (1 fore each technique plus an unmodified version) of train and test sets were created. A LightGBM model was trained and evaluated on
each one to determine which technique offered the best performance.

### Model optimization

After determining the data imbalance handling technique that provided the best results, we proceeded to perform hyperparameter tuning of the LightGBM model. This was done using
the hyperopt library, which provides tools for performing Bayesian optimization. After tuning, the precision of the model increased considerably, completely eliminating false 
positives on the test set evalutation.
