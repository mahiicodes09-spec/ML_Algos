# Random Forest Regressor – Student Performance Prediction

## 1. About the Project

This project uses a **Random Forest Regressor** to predict students' final marks based on study hours, attendance, previous marks, and completed assignments.

## 2. What is Random Forest Regressor?

Random Forest Regressor is a supervised machine learning algorithm used to predict continuous numerical values.

It is an ensemble learning technique that combines multiple Decision Trees and averages their predictions to produce the final output.

Unlike Random Forest Classifier, which uses majority voting for classification, Random Forest Regressor calculates the average of numerical predictions.

## 3. How Random Forest Regressor Works

### Step 1: Bootstrap Sampling

Random Forest randomly selects rows from the training dataset with replacement to create different samples for individual trees.

A row may appear multiple times in a sample, while some rows may not be selected. This helps the trees learn different patterns.

### Step 2: Random Feature Selection

At each split, a tree considers a randomly selected subset of features rather than necessarily considering all features.

This introduces diversity among the trees and can help reduce their correlation.

### Step 3: Building Decision Trees

Each tree repeatedly splits the data into smaller groups based on feature values, such as Study Hours or Attendance.

For regression, a common splitting criterion is **Mean Squared Error (MSE)**.

\[
MSE=\frac{1}{N}\sum_{i=1}^{N}(y_i-\bar y)^2
\]

Here, \(y_i\) represents an actual target value and \(\bar y\) represents the mean target value within the node.

The tree searches for splits that reduce the weighted squared error of the resulting child nodes.

### Step 4: Averaging Predictions

Each tree predicts the final marks for a student. Random Forest calculates the average of all tree predictions.

For example, if three trees predict 70, 80, and 75 marks:

\[
\hat y=\frac{70+80+75}{3}=75
\]

The final predicted marks are **75**.

The general formula is:

\[
\hat y=\frac{1}{B}\sum_{b=1}^{B}T_b(x)
\]

Where:
- \(B\) is the total number of trees.
- \(T_b(x)\) is the prediction made by tree \(b\) for input \(x\).

## 4. How Random Forest Reduces Overfitting

A single Decision Tree may learn noise from the training data, resulting in high variance.

Random Forest combines predictions from trees trained on different samples and feature subsets. Averaging can reduce prediction variance, especially when the trees make different errors.

However, it does not guarantee that overfitting will always be eliminated.

## 5. Dataset Description

The dataset contains 150 rows and 5 columns.

| Feature | Description |
|---|---|
| Study_Hours | Hours spent studying |
| Attendance | Attendance percentage |
| Previous_Marks | Previous examination marks |
| Assignments_Completed | Number of assignments completed |
| Final_Marks | Target variable to predict |

The dataset is synthetically generated for learning purposes.

## 6. Implementation Workflow

1. Load the dataset using Pandas.
2. Separate input features (`X`) and target (`y`).
3. Split the data into 80% training and 20% testing sets.
4. Initialize and train `RandomForestRegressor`.
5. Generate predictions using the test data.
6. Evaluate performance using MAE, MSE, RMSE, and R² score.
7. Compare actual and predicted marks.

The split contains 120 training rows and 30 testing rows.

## 7. Evaluation Metrics

### Mean Absolute Error (MAE)

\[
MAE=\frac{1}{N}\sum_{i=1}^{N}|y_i-\hat y_i|
\]

Measures the average absolute difference between actual and predicted values.

### Mean Squared Error (MSE)

\[
MSE=\frac{1}{N}\sum_{i=1}^{N}(y_i-\hat y_i)^2
\]

Squares prediction errors, giving larger errors more influence.

### Root Mean Squared Error (RMSE)

\[
RMSE=\sqrt{MSE}
\]

Measures prediction error on the same scale as the target variable.

### R² Score

\[
R^2=1-\frac{\sum_{i=1}^{N}(y_i-\hat y_i)^2}{\sum_{i=1}^{N}(y_i-\bar y)^2}
\]

Measures model performance relative to predicting the mean of the actual target values. A score closer to 1 generally indicates a better fit.

## 8. Model Results

| Metric | Result |
|---|---:|
| MAE | 1.2767 |
| MSE | 3.2970 |
| RMSE | 1.8158 |
| Training R² | 0.9992 |
| Testing R² | 0.9855 |

### Interpretation

- The average absolute prediction error is approximately 1.28 marks.
- The RMSE is approximately 1.82 marks.
- The testing R² score of 0.9855 indicates that the model explains approximately 98.55% of the variation in test-set marks relative to the mean baseline.
- Both training and testing scores are high and relatively close, with no obvious indication of severe overfitting from these scores alone.

These results apply to the synthetic dataset and do not guarantee similar performance on real-world data.

## 9. Conclusion

This project demonstrates how Random Forest Regressor predicts continuous numerical values by combining multiple Decision Trees.

It covers bootstrap sampling, random feature selection, Decision Tree construction, MSE-based splitting, averaging predictions, and regression evaluation metrics.

The results demonstrate strong performance on the test dataset and highlight the importance of evaluating machine learning models on unseen data.