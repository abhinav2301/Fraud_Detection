# Fraud Detection
##**Anomaly Detection Implementation(Credit card fraud) - Random Forest Classifier :**

The credit card data set is heavily imbalanced with more than 99% Valid records. 

### **Feature Engineering** :

The first step is to Scale the "Time" and "Amount" column appropriately. The Robust Scaler has been used for transforming the due to the nature of the outliers.

This Scaler removes the median and scales the data according to the quantile range (defaults to IQR: Interquartile Range). The IQR is the range between the 1st quartile (25th quantile) and the 3rd quartile (75th quantile).

Centering and scaling happen independently on each feature by computing the relevant statistics on the samples in the training set. Median and interquartile range are then stored to be used on later data using the transform method.

![Image1](https://github.com/abhinav2301/Fraud_Detection/blob/master/images/Time%20distribution.png)
![Image2](https://github.com/abhinav2301/Fraud_Detection/blob/master/images/correlation%20matrix.png)


### **Balancing the Dataset** :

The imbalanced nature of the data means that directly modelling the given dataset will not provide an accurate model. There are 2 popular methods to deal with imbalanced datasets :

1.   **Undersampling** - down-sizing the majority class by removing observations until the dataset is balanced
2.   **Oversampling** - over-sizing the minority class by adding observations

Undersampling while helping balance the data, discards a lot of it. This means that the model may potentially loose out on valuable information. Thereby we've used **SMOTE** to oversample the minority class.


##### **SMOTE** :

> The SMOTE algorithm is one of the first and still the most popular algorithmic approach to generating new dataset samples. The algorithm, introduced and accessibly enough described in a 2002 paper, works by oversampling the underlying dataset with new synthetic points.
> The SMOTE algorithm is parameterized with k_neighbors (the number of nearest neighbors it will consider) and the number of new points you wish to create. Each step of the algorithm will:



1.   Randomly select a minority point.
2.   Randomly select any of its k_neighbors nearest neighbors belonging to the same class.
3.   Randomly specify a lambda value in the range [0, 1].
4.   Generate and place a new point on the vector between the two points, located lambda percent of the way from the original point.


### **Model** :

A random forest classifier with grid search hyper parameter tuning. An imbalanced pipeline is used to oversample the data and then the oversampled data is used to train the data. However the oversampled values are not used for the validation. 

### **Model Performance** :

With highly imbalanced models, accuracy is a bad measure to check a models performance due to majority bias. Recall and F1 score are a much better indicator of the models performance. 

Initial attempts to train the model on the unbalanced dataset resulted in a recall of 77% which improved to 86% on the model trained on the Oversampled data.

![Image3](https://github.com/abhinav2301/Fraud_Detection/blob/master/images/confusion%20matrix.png)
