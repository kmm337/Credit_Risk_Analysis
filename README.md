# Supervised Machine Learning and Unbalanced Classification on Credit Risk Data

## Overview

The purpose of this analysis is to predict credit risk using a dataset from LendingClub, a peer-to-peer lending services company. The
challenge is in handling the imbalance between the numbers of high and low risk loans in the dataset. 

Six different models will be assessed. Four will utilize different sampling algorithms followed by a logistic regression. Two models will employ emsemble classifiers. 

## Results

### Comparison of Sampling Algorithms

The comparison below shows the six different algorithms against various metrics: precision, recall, f1 and balanced accuracy score.

![comparison](/Images/comparison.PNG)

* Precision is a measure of: given a prediction of high risk, how likely is it that the loan is actually high risk? Low precision means a high likelihood of falsely predicting an actually low risk loan as high risk.

  All of our algorithms exhibit low precision.

* Recall is a measure of: given a loan is actually high risk, how likely is it that the algorithm identified it as high risk? High recall means a high likelihood of predicting a high risk loan correctly.

  Only the Easy Ensemble Classifier shows recall over 90%. All the other algorithms hover around 70%

  For this analysis, recall is more important than precision, assuming the loss associated with a bad loan is greater than the opportunity cost from missed good loans.

* F1 is a measure of balance between precision and recall. All of our algorithms have a low F1 score.

* The balanced accuracy score is amother measure of prediction ability, adjusted for the imbalance between high and low risk loans in the sample. It will tend to be inflated in highly imbalanced datasets such as the one used in this study.

Reviewing a combination of metrics is the best way to assess the various algorithms.

Notes: 
* In these analyses, high risk is coded as 0 and low risk is coded as 1.

* The confusion matrix is read as:
        
        predicted high risk     predicted low risk

  actually high

  actually low 

### Summary by Algorithm

#### Oversampling - Naive Random Algorithm

* Balanced Accuracy Score: .648
* Confusion Matrix

![random_over_sample](/Images/confusion_matrix_oversample_random.PNG)
* Imbalanced Classification Report
![random_over_sample](/Images/imbalanced_class_rpt_oversample_random.PNG)



#### Oversampling - SMOTE Algorithm

* Balanced Accuracy Score: .663
* Confusion Matrix
![SMOTE_over_sample](/Images/confusion_matrix_oversample_SMOTE.PNG)
* Imbalanced Classification Report
![SMOTE_over_sample](/Images/imbalanced_class_rpt_oversample_SMOTE.PNG)

#### Undersampling - Cluster Centroids Algorithm

* Balanced Accuracy Score: .544
* Confusion Matrix
![cc_under_sample](/Images/confusion_matrix_undersample_cc.PNG)
* Imbalanced Classification Report
![cc_under_sample](/Images/imbalanced_class_rpt_undersample_cc.PNG)

#### Combination (Over and Under Sampling) SMOTEENN Algorithm

* Balanced Accuracy Score: .640
* Confusion Matrix
![combo_sample](/Images/confusion_matrix_combo_sample.PNG)
* Imbalanced Classification Report
![combo_sample](/Images/imbalanced_class_rpt_combosample.PNG)

### Ensemble Classifiers

#### Balanced Random Forest Classifier

* Balanced Accuracy Score: .788
* Confusion Matrix
![random_forest](/Images/confusion_matrix_random_forest.PNG)
* Imbalanced Classification Report
![random_forest](/Images/imbalanced_class_rpt_random_forest.PNG)

#### Easy Ensemble Classifier (AdaBoost)

* Balanced Accuracy Score: .932
* Confusion Matrix
![easy_ensemble](/Images/confusion_matrix_adaboost.PNG)
* Imbalanced Classification Report
![easy_ensemble](/Images/imbalanced_class_rpt_adaboost.PNG)

## Summary

Of all the models created, the easy ensemble algorithm produced the highest recall at 92%, however, precision was very low at less than 10%. This means a large percentage of loans classified as high risk are actually low risk, meaning missed opportunities.

There may be opportunity to improve the models with a more rigorous review of the input data. For example, input values have different magnitudes. Rescaling to achieve better uniformity may help. The parameters used in developing the models should be reviewed. For example, these models did not stratify the samples, which may help improve performance.

Another analysis designed to quantify lost opportunity on misclassified high risk loans vs. the loss associated with a truly high risk loan would help clarify the situation.
