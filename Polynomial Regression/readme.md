# Polynomial Regression

## 1. What is Polynomial Regression?

Polynomial Regression is a supervised machine learning algorithm used to predict continuous numerical values when the relationship between input features and the target may be nonlinear.

It extends Linear Regression by adding polynomial features such as squared terms, cubed terms, and interactions between features.

**Example:** Predicting an esports player's performance score based on practice hours, reaction time, sleep hours, and gaming experience.

## 2. How Does It Work?

1. Prepare the dataset and separate input features (`X`) from the target (`y`).
2. Split the data into training and testing sets.
3. Train a Linear Regression model as a baseline.
4. Use `PolynomialFeatures` to generate additional features.
5. Train Linear Regression on the transformed features.
6. Evaluate both models using MAE, MSE, and R².
7. Apply Ridge regularization and use GridSearchCV to tune the `alpha` hyperparameter.

## 3. Mathematical Intuition

A simple Linear Regression model follows:

**y = b₀ + b₁x**

A degree-2 Polynomial Regression model follows:

**y = b₀ + b₁x + b₂x²**

For multiple features, polynomial transformation can also generate interaction terms such as **x₁ × x₂**.

The model still uses Linear Regression, but on the expanded feature set. This allows it to learn more complex relationships.

## 4. Implementation Summary

The project used a small, synthetic esports performance dataset containing 20 rows, four input features, and one continuous target variable: `PerformanceScore`.

- Separated features and target using Pandas.
- Split the dataset using an 80:20 train-test split.
- Trained a baseline Linear Regression model.
- Generated degree-2 polynomial features using `PolynomialFeatures`.
- Trained and evaluated Polynomial Regression.
- Applied Ridge Regression to reduce the effect of overly large coefficients.
- Used GridSearchCV with 4-fold cross-validation to search multiple `alpha` values.
- Compared models using MAE, MSE, and R².

## 5. Evaluation Metrics

- **MAE (Mean Absolute Error):** Measures the average absolute prediction error. Lower is better.
- **MSE (Mean Squared Error):** Penalizes larger errors more heavily. Lower is better.
- **R² Score:** Measures how well the model explains variation in the target. Higher is generally better; it can be negative.

## 6. Ridge Regularization and GridSearchCV

Polynomial features increase model complexity and can lead to overfitting, especially with small datasets.

Ridge Regression adds an L2 penalty to the loss function:

**Ridge Loss = MSE + α Σw²**

Here, `α` controls the strength of regularization. A higher value applies a stronger penalty to large coefficients.

GridSearchCV tests the specified hyperparameter values using cross-validation and selects the configuration with the best average validation score. In this project, `alpha` values of 0.01, 0.1, 1, 10, and 100 were tested using negative MAE as the scoring metric.

## 7. Advantages

- Captures nonlinear relationships.
- Easy to implement using Scikit-learn.
- Can improve predictions when the relationship is genuinely nonlinear.
- Supports multiple input features and interaction terms.

## 8. Disadvantages

- Higher polynomial degrees can cause overfitting.
- The number of features increases rapidly with degree.
- Sensitive to outliers and feature scales.
- May perform worse than simple Linear Regression when extra complexity is unnecessary.

## 9. Key Learning

Polynomial Regression does not always outperform Linear Regression. In this experiment, the baseline Linear Regression model performed better on the chosen test split. Ridge regularization improved the polynomial model's test metrics, but did not outperform the baseline.

Since the dataset contains only 20 rows, these results are preliminary. More data and robust validation are needed before drawing general conclusions.

**Conclusion:** Polynomial Regression extends Linear Regression by transforming input features to model nonlinear patterns. Comparing models, evaluating predictions, and tuning hyperparameters helps determine whether the added complexity is worthwhile.