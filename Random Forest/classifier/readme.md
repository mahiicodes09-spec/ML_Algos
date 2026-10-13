# Random Forest Classifier – Student Performance Prediction

## 1. About the Project

This project uses a **Random Forest Classifier** to predict whether a student will Pass or Fail based on study habits and academic performance.

## 2. What is Random Forest?

Random Forest is a supervised machine learning algorithm used for classification and regression. It is an **ensemble learning technique** that combines multiple Decision Trees to make a final prediction.

A single Decision Tree may overfit the training data. Random Forest reduces this risk by building multiple trees on different samples and combining their predictions.

## 3. How Random Forest Works

### Step 1: Bootstrap Sampling

Random Forest creates different training samples by randomly selecting rows from the dataset with replacement. A row may appear multiple times in a sample.

This helps different trees learn different patterns.

### Step 2: Random Feature Selection

At each split, a tree considers a randomly selected subset of features instead of necessarily considering all features.

This creates diversity among trees.

### Step 3: Building Decision Trees

Each tree repeatedly splits the data using feature-based conditions, such as Attendance greater than 75%.

For classification, a common splitting criterion is **Gini Impurity**:

\[
Gini=1-\sum_{i=1}^{k}p_i^2
\]

Here, \(p_i\) is the proportion of samples belonging to class \(i\).

For example, if a node contains 5 Pass and 5 Fail students:

\[
Gini=1-(0.5^2+0.5^2)=0.5
\]

A lower Gini value means less mixing of classes. The tree chooses splits that reduce the weighted impurity of the resulting child nodes.

### Step 4: Majority Voting

Each tree predicts Pass or Fail for a new student. The class receiving the most votes becomes the final prediction.

\[
\hat{y}=\operatorname{mode}\{T_1(x),T_2(x),\ldots,T_B(x)\}
\]

Here, \(T_i(x)\) is the prediction of a tree and \(B\) is the total number of trees.

**Complete flow:** Bootstrap Sampling → Random Feature Selection → Building Decision Trees → Majority Voting → Final Prediction.

## 4. Dataset Description

The dataset contains 150 rows and 5 columns.

| Feature | Description |
|---|---|
| Study_Hours | Hours spent studying |
| Attendance | Attendance percentage |
| Previous_Marks | Previous examination marks |
| Assignments_Completed | Number of completed assignments |
| Result | Target variable: Pass or Fail |

The dataset is synthetically generated for learning purposes.

## 5. Implementation

1. Load the dataset using Pandas.
2. Separate the input features (`X`) and target (`y`).
3. Split the data into 80% training and 20% testing sets.
4. Train a `RandomForestClassifier`.
5. Predict results on the test data.
6. Evaluate using accuracy, precision, recall, F1-score, and confusion matrix.
7. Tune hyperparameters using GridSearchCV.

The split contains 120 training rows and 30 testing rows.

## 6. Hyperparameter Tuning

GridSearchCV tests different parameter combinations using 5-fold cross-validation. The model is selected using macro F1-score.

**Best hyperparameters:**

| Parameter | Value | Meaning |
|---|---:|---|
| `n_estimators` | 200 | Number of trees |
| `max_depth` | 5 | Maximum tree depth |
| `min_samples_split` | 2 | Minimum samples needed to split a node |

## 7. Results

- Best cross-validation macro F1-score: **0.817**
- The tuned model had lower test accuracy than the original model.
- Tuning does not guarantee better test performance because hyperparameters are selected using cross-validation, not the test set.

## 8. Conclusion

This project demonstrates Random Forest classification, including bootstrap sampling, random feature selection, Decision Tree construction, Gini Impurity, majority voting, and hyperparameter tuning.

It highlights how combining multiple Decision Trees can help reduce overfitting and why model performance should be evaluated on unseen data.