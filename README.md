# DS-Spark-EMR

### Introduction

Customer churn prediction is one of the most important real World use case scenarios for different kinds of businesses. In this article I analyze customer data of a music service company to build a model which can predict the customer churn rate. The full dataset is 12 GB in size and to be able to analyze such a large dataset, Amazon Elastic MapReduce service is leveraged. The service is used to create a cluster of nodes with preinstalled open source tool — Apache Spark.

### Setup

```
Release: emr-5.30.1
Applications: Spark: Spark 2.4.5 
Instance type: m5.xlarge
Number of instance: 4 (Master + 3 Core)
```

### Data

The full dataset has over 26 million rows of log data from 22,277 unique customers. The features are made up of numeric and categorical values which describe an event. Data is retrieved from AWS S3 bucket.

### Libraries

* `Spark Dataframe API`
* `Spark ML API`
* `pandas`
* `seaborn`
* `matplotlib`


### Analysis

Following are the steps involved:

* Exploratory Data Analysis
* Feature Engineering - Built 15 features using the user log data
* Over Sampling of the minority (positive) Class for modeling input.
* Modeling Pipeline:
  * StringIndexer — StringIndexerencodes string column of labels to a column of label indices. 
  * VectorAssembler — VectorAssembler is a transformer that combines a given list of columns into a single vector column
  * Normalizer — Normalizer is a Transformer which transforms a dataset of Vector rows, normalizing each Vector to have unit norm
  * Classifiers — Logistic Regression, Random Forest and GBT Classifier
  
### Results

GBT Classifier gave the best results compared to other classifiers with a very high F1 Score of 88.96%. The number of true positives is at a very decent 1083 with a low false positive number of 320. 

![Best Model Results](https://github.com/mallik3006/DS-Spark-EMR/blob/master/best_model_gbt.png)

![Feature Importance](https://github.com/mallik3006/DS-Spark-EMR/blob/master/feature_importance_gbt.png)

Please follow the blog [here](https://medium.com/@mallik30/customer-churn-prediction-using-amazon-emr-and-apache-spark-a6fd37126f0b?sk=76af45e4628c64eca9a27aebd9e93ad0) for more details.


### Repository Files 

* `Sparkify.ipynb`: Notebook with EDA, Feature engineering, Over-sampling and Modeling using Pyspark on Amazon EMR 
