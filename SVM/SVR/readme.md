# Support Vector Regression (SVR)

## 1. SVR:

Support Vector Regression (SVR) is a supervised machine learning algorithm used for predicting continuous numerical values, such as house prices, salaries, and temperatures.

SVR is based on the Support Vector Machine (SVM) concept. Instead of trying to minimize every prediction error, it attempts to fit a function within an acceptable error margin called the **epsilon (ε) tube**.

Only certain data points, called **support vectors**, influence the final regression function.

## 2. Mathematical Intuition

SVR tries to find a function:

**f(x) = wᵀx + b**

Where:
- **x:** Input features
- **w:** Model weights
- **b:** Bias or intercept

The objective is to keep predictions within an acceptable error margin while maintaining a simple, smooth model.

### Epsilon-Insensitive Loss

**Lε(y, f(x)) = max(0, |y − f(x)| − ε)**

Where:
- **y:** Actual value
- **f(x):** Predicted value
- **ε (epsilon):** Acceptable error margin

If the prediction error is less than or equal to ε, the loss is zero. Errors outside this margin are penalized.

### Optimization Objective

**Minimize: ½‖w‖² + C Σ Lε(yᵢ, f(xᵢ))**

- **½‖w‖²:** Encourages a simpler, flatter regression function.
- **C Σ Lε:** Penalizes errors outside the epsilon tube.
- **C:** Controls the trade-off between model simplicity and training errors.

## 3. Kernel Trick

SVR can model nonlinear relationships using kernels, which allow it to learn complex patterns without explicitly transforming the data into a higher-dimensional feature space.

Common kernels include:
- **Linear:** For approximately linear relationships.
- **Polynomial:** For polynomial-shaped relationships.
- **RBF (Radial Basis Function):** For flexible, nonlinear relationships.

In this implementation, the **RBF kernel** is used.

## 4. Data Preprocessing

1. Separate the dataset into features (X) and target (y).
2. Split the data into training and testing sets using an 80:20 ratio.
3. Apply StandardScaler to the input features.
4. Scale the target values separately for SVR training.
5. Transform predictions back to the original target scale before evaluation.

Scaling is important because SVR depends on distances and feature magnitudes. During cross-validation, preprocessing must be fitted separately within each training fold to avoid data leakage.

## 5. Hyperparameter Tuning Using GridSearchCV

GridSearchCV tests different hyperparameter combinations using 5-fold cross-validation and selects the combination with the best average validation score.

The parameters tuned in this project are:

- **C:** Controls the penalty for errors outside the epsilon tube. A larger value penalizes these errors more strongly.
- **Gamma:** Controls the influence of individual training points for the RBF kernel. A larger value creates more localized influence.
- **Epsilon:** Defines the width of the error-insensitive tube. A larger value allows a wider range of errors without penalty.

The best combination is selected using the average cross-validation R² score.

## 6. Model Evaluation

The trained model is evaluated using:

- **MAE (Mean Absolute Error):** Average absolute difference between actual and predicted values.
- **MSE (Mean Squared Error):** Average squared prediction error.
- **RMSE (Root Mean Squared Error):** Square root of MSE, expressed in the target's units.
- **R² Score:** Measures how well the model explains variation in the target. Higher values generally indicate better performance.

Training and testing R² scores are also compared to assess generalization and potential overfitting.

## 7. Advantages

- Effective for high-dimensional datasets.
- Can model nonlinear relationships using kernels.
- Uses an epsilon-insensitive loss that ignores small errors within the specified margin.
- Regularization helps control model complexity.

## 8. Disadvantages

- Requires feature scaling in most practical applications.
- Hyperparameter and kernel selection can be challenging.
- Training can become computationally expensive for large datasets.
- Performance can be sensitive to the choice of C, gamma, and epsilon.

## 9. Conclusion

SVR is a regression algorithm that balances model simplicity with prediction errors using an epsilon-insensitive loss function. In this project, StandardScaler and GridSearchCV are used to improve the model's performance, while MAE, MSE, RMSE, and R² measure its predictive accuracy and generalization.