# KNN Classification:-

KNN (K-Nearest Neighbors) is a supervised machine learning algorithm used for classification and regression.

It works on the idea that similar data points are usually close to each other. For classification, KNN finds the K nearest data points and assigns the class based on majority voting.

## Important Concepts:

K → Number of nearest neighbors considered for prediction.

Distance → Used to find how close two data points are.

Majority Voting → The class with the most votes among the neighbors is selected.

Lazy Learning → KNN does not build a complex model during training. It mainly stores the training data and performs calculations when making predictions.

Feature Scaling → Important because KNN is distance-based. Features with larger numerical ranges can otherwise dominate the distance calculation.

### Distance Measures:-

Two important distance measures used in KNN are:

1. Euclidean Distance

It calculates the straight-line distance between two points. It is one of the most commonly used distance measures in KNN.

2. Manhattan Distance

Also called Taxicab distance. It calculates distance by adding the absolute differences between the coordinates.

In Scikit-learn, the distance measure can be selected using the metric parameter of KNeighborsClassifier.

### Choosing and Tuning K:-

The value of K has a major effect on the performance of KNN.

Small K → More sensitive to noise and individual data points.

Large K → Smoother predictions but may ignore local patterns.

Good K → Provides a balance between noise and generalization.

Instead of randomly selecting K, we can tune K by trying different K values and comparing their performance.

### Cross-Validation:-

Cross-validation can be used to test different K values more reliably.

A common approach is GridSearchCV. It tests multiple K values using cross-validation and helps select the best-performing K.

For this project:

K = 3

### Evaluation Metrics for KNN Classification:-

After training the model, we need to check how well it performs.

1. Accuracy

Measures the percentage of total predictions that are correct.

2. Precision

Out of all the observations predicted as a particular class, precision tells us how many were actually that class.

3. Recall

Out of all the observations that actually belong to a particular class, recall tells us how many the model correctly identified.

4. F1-Score

F1-score provides a balance between precision and recall. It is useful when both precision and recall are important.

5. Confusion Matrix

A confusion matrix shows the number of True Positives, True Negatives, False Positives and False Negatives. It helps us understand where the model is making correct and incorrect predictions.

Dataset

Dataset: knn_classification.csv

Features:
Age
EstimatedSalary

Target:
Buy

Target Encoding:

No → 0
Yes → 1

What I Did:-

1. Loaded the dataset using Pandas.
2. Checked the dataset using shape, info, describe and missing-value checks.
3. Separated the features and target variable.
4. Converted the categorical target into numerical values.
5. Split the dataset into 75% training and 25% testing.
6. Used stratify=y to maintain the class distribution in the split.
7. Applied StandardScaler because KNN depends on distance.
8. Created a KNN classifier with K = 3.
9. Trained the model using the training data.
10. Predicted the classes of the test data.
11. Evaluated the model using accuracy and confusion matrix.
12. Visualized the confusion matrix using a heatmap.
13. Used the trained model to predict the class of a new person.

---Additional KNN Steps---

In a complete KNN workflow, K can also be tuned using cross-validation or GridSearchCV.

The model can be evaluated using Accuracy, Precision, Recall, F1-Score and Confusion Matrix.

Results

Training samples: 12

Testing samples: 4

K value: 3

Accuracy: 1.0 (100%)

Confusion Matrix: [[1, 0], [0, 3]]

New person: Age = 37, Estimated Salary = 48000

Prediction: Yes

----Key Takeaways----

1. KNN is a distance-based algorithm.

2. KNN can be used for both classification and regression.

3. Feature scaling is important before applying KNN.

4. K determines how many neighbors participate in the prediction.

5. K-value tuning helps find a suitable value of K.

6. Cross-validation and GridSearchCV can be used for K tuning.

7. Euclidean and Manhattan are important distance measures.

8. KNN classification can be evaluated using Accuracy, Precision, Recall, F1-Score and Confusion Matrix.

9. stratify=y helps maintain class proportions during classification splitting.

10. Accuracy can be misleading when the test dataset is very small, so other evaluation metrics should also be considered.
