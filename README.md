# Credit Risk Analysis
## Overview of the analysis
The objective of the following analysis is to determine the best supervised learning algorythm to determine if a subject is high-risk or low-risk for a bank who gives credits. 
## Results
Six methods were tested to determine which one is the best. The first four are logistic regressions, each one with different sampling methods and the other two are ensemble learners (BalancedRandomForest and EasyEnsembleClassifier).

- ### Logistic Regression Naive Random Oversampling
    Balanced Accuracy Score: 63%
    #### Confusion Matrix
    |  | Predicted High Risk | Predicted Low Risk |
    | ----------- | ----------- | ----------- |
    | Actually High Risk | 50 | 37 |
    | Actually Low Risk | 5408 | 11710 |
    
    Precision (High Risk): 1%
    
    Precision (Low Risk): 100%
    
    Recall (High Risk): 57%
    
    Recall (Low Risk): 68%
    
    F1-score (High Risk): 2%
    
    F1-score (Low Risk): 81%
    
    For this method the BAS is a bit low, we would want to aim for something higher. From our CM we find that we missed 42% of real High Risk people, and would lose on 5408 people who would actually be good. 
    
- ### Logistic Regression SMOTE Oversampling
    Balanced Accuracy Score: 63%
    #### Confusion Matrix
    |  | Predicted High Risk | Predicted Low Risk |
    | ----------- | ----------- | ----------- |
    | Actually High Risk | 54 | 33 |
    | Actually Low Risk | 6253 | 10865 |
    
    Precision (High Risk): 1%
    
    Precision (Low Risk): 100%
    
    Recall (High Risk): 62%
    
    Recall (Low Risk): 63%
    
    F1-score (High Risk): 2%
    
    F1-score (Low Risk): 78%
    
    For this one, our BAS remains the same as the previous, but their is a slight increase in our Recall (High Risk), meaning that we are able to catch more High Risk people. As a downside our Recall (Low Risk) is lower.
    
- ### Logistic Regression Cluster Centroids Undersampling
    Balanced Accuracy Score: 51%
    #### Confusion Matrix
    |  | Predicted High Risk | Predicted Low Risk |
    | ----------- | ----------- | ----------- |
    | Actually High Risk | 50 | 37 |
    | Actually Low Risk | 9158 | 7960 |
    
    Precision (High Risk): 1%
    
    Precision (Low Risk): 100%
    
    Recall (High Risk): 57%
    
    Recall (Low Risk): 47%
    
    F1-score (High Risk): 1%
    
    F1-score (Low Risk): 63%
    
    Without doubt the worst method so far, every metric is lower than the previous methods.
- ### Logistic Regression SMOTEENN Combination (Over and Under) Sampling
    Balanced Accuracy Score: 64%
    #### Confusion Matrix
    |  | Predicted High Risk | Predicted Low Risk |
    | ----------- | ----------- | ----------- |
    | Actually High Risk | 61 | 26 |
    | Actually Low Risk | 7170 | 9948 |
    
    Precision (High Risk): 1%
    
    Precision (Low Risk): 100%
    
    Recall (High Risk): 70%
    
    Recall (Low Risk): 58%
    
    F1-score (High Risk): 2%
    
    F1-score (Low Risk): 73%
    
    With this method, we are able to better detect High Risk people with the downside being that our Low Risk detection is not as good as the Naive Random Oversampling method.
- ### Balanced Random Forest Classifier
    Balanced Accuracy Score: 78%
    #### Confusion Matrix
    |  | Predicted High Risk | Predicted Low Risk |
    | ----------- | ----------- | ----------- |
    | Actually High Risk | 58 | 29 |
    | Actually Low Risk | 1560 | 15558 |
    
    Precision (High Risk): 4%
    
    Precision (Low Risk): 100%
    
    Recall (High Risk): 67%
    
    Recall (Low Risk): 91%
    
    F1-score (High Risk): 7%
    
    F1-score (Low Risk): 95%
    
    This method gives us a huge boost into the detection of Low Risk people and the High Risk people detection is not as good as the SMOTEENN one but it is pretty close.
 - ### Easy Ensemble AdaBoost Classifier
    Balanced Accuracy Score: 93%
    #### Confusion Matrix
    |  | Predicted High Risk | Predicted Low Risk |
    | ----------- | ----------- | ----------- |
    | Actually High Risk | 79 | 8 |
    | Actually Low Risk | 979 | 16139 |
    
    Precision (High Risk): 7%
    
    Precision (Low Risk): 100%
    
    Recall (High Risk): 91%
    
    Recall (Low Risk): 94%
    
    F1-score (High Risk): 14%
    
    F1-score (Low Risk): 97%
    
    Without doubt the best method of all, has a BAS of 93%, all of our detection metrics for Low Risk and High Risk are the highest of all the methods and  only missing on 8 High Risk people makes this the best one.
## Summary
So from all the methods tested the best one for this dataset is the Easy Ensemble AdaBoost Classifier, which is the one with the best metrics of all. Through the analysis of each method pros and cons were found for each one. Would I recommend the method, yes because the probabilities of a High Risk person slipping through the cracks is of 0.04%. Perhaps, as a further analysis could be comparing this percentage to the percentage of High Risk people detected by a normal person.   
