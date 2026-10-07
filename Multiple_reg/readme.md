# Multiple Linear Regression

## 1. What is Multiple Linear Regression?

Multiple Linear Regression is a supervised machine learning algorithm used to predict a continuous numerical value using more than one input feature.

In simple linear regression, we use one input variable to predict the output. In multiple linear regression, we use two or more input variables together.

For this project, the goal was to predict a student's **Final Score** using:

* Hours Studied
* Attendance
* Assignments
* Sleep Hours
* Previous Score

The model looks at all these factors together and learns their relationship with the Final Score.

## 2. Dataset

The dataset contains **43 students** and **6 columns**.

The columns are:

* Hours_Studied
* Attendance
* Assignments
* Sleep_Hours
* Previous_Score
* Final_Score

All columns contained numerical values and there were no missing values.

## 3. Understanding the Data

First, the dataset was loaded and basic information was checked.

The shape of the dataset was **(43, 6)**, meaning there were 43 rows and 6 columns.

The describe() function was also used to understand the mean, minimum, maximum and other basic statistics of the numerical columns.

## 4. Selecting Features and Target

The five input features selected for the model were:

* Hours_Studied
* Attendance
* Assignments
* Sleep_Hours
* Previous_Score

The target variable was **Final_Score**.

The input features were stored in X, while the target was stored in y.

## 5. Train Test Split

The dataset was divided into training and testing data using train_test_split().

The test size was set to **20%**, which means 80% of the data was used for training and 20% for testing.

This resulted in:

* Training data: 34 students
* Testing data: 9 students

random_state=42 was used so that the same split could be reproduced.

## 6. Model Training

The LinearRegression algorithm from Scikit-learn was used.

The model was trained using the training data. During training, the model learned how the five input features are related to the Final Score.

## 7. Making Predictions

After training the model, predictions were made on the test data.

The model predicted the Final Scores for the 9 students in the test set.

The original decimal predictions were kept for calculating the evaluation metrics, while rounded values were used when displaying the predictions.

## 8. Model Evaluation

The model was evaluated using MAE, MSE, RMSE and R².

The results were:

* **MAE = 1.0553**
* **MSE = 1.7894**
* **RMSE = 1.3376**
* **R² = 0.9921**

### MAE

Mean Absolute Error tells us the average difference between the actual and predicted values.

The MAE was approximately **1.06 marks**, meaning the predictions were on average around 1 mark away from the actual scores.

### MSE

Mean Squared Error calculates the squared difference between the actual and predicted values.

A lower MSE generally means the predictions are closer to the actual values.

### RMSE

Root Mean Squared Error is the square root of MSE.

The RMSE was **1.34**, meaning the typical prediction error was around 1.34 marks.

### R² Score

R² tells us how much of the variation in the target variable is explained by the model.

The R² score was **0.9921**, meaning the model explained approximately **99.21% of the variation** in Final Score on the test set.

The score is very high, but the dataset is small, with only 43 rows, so this result should not automatically be expected on a larger dataset.

## 9. Understanding the Coefficients

The model learned the following coefficients:

* Hours_Studied = 1.2268
* Attendance = -0.1883
* Assignments = 0.2642
* Sleep_Hours = 0.4602
* Previous_Score = 0.7765

The intercept was **6.8059**.

A coefficient tells us how the predicted Final Score changes when that particular feature increases by 1 unit, while keeping the other features constant.

For example, the coefficient for Hours_Studied is 1.2268. This means that, according to the model, increasing Hours_Studied by 1 unit is associated with an increase of about 1.23 marks in the predicted Final Score, while the other features remain constant.

The negative Attendance coefficient does not mean that attendance is actually bad for students. It is simply the relationship learned by the model from this particular dataset while considering the other features.

## 10. Actual vs Predicted Visualization

An Actual vs Predicted scatter plot was created to visually check the model's predictions.

The X-axis represents the **Actual Final Score**, while the Y-axis represents the **Predicted Final Score**.

A diagonal reference line was also added. This line represents perfect predictions, where the actual score and predicted score are the same.

Points closer to this line indicate better predictions.

## 11. Final Prediction

After training the model, it can also be used to predict the Final Score of a new student.

For example, if a student has 7 hours of study, 90 attendance, 85 assignments, 7 hours of sleep and a previous score of 80, these values can be given to the trained model to predict the student's Final Score.

## 12. Conclusion

In this project, Multiple Linear Regression was used to predict a student's Final Score using five different features.

The model achieved an **R² score of 0.9921** and an **RMSE of 1.3376** on the test set, showing very good performance on this dataset.

However, the dataset contains only 43 records, so using a larger dataset would give a better idea of how well the model performs on new and unseen data.
