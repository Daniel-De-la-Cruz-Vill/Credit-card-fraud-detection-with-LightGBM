# Detecting fraudulent credit card transactions with LightGBM

![image](https://github.com/Daniel-De-la-Cruz-Vill/Credit-card-fraud-detection-with-LightGBM/assets/157164355/f0d46892-12e3-40b5-bde1-feb25ec34502)

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
