## 1. Problem Formulation

Given a set of observed data points:

$$
\{(x_1, y_1), (x_2, y_2), \dots, (x_n, y_n)\}
$$

the objective is to model the relationship between the input variable \( x \) and the output variable \( y \) using a linear function.

Rather than simply fitting a line heuristically, the problem is formulated as an optimization task. The goal is to determine the parameters of a linear model such that the predicted values are as close as possible to the observed values.

This is achieved by defining a function that measures the discrepancy between the observed outputs and the model's predictions, and then finding the parameters that minimize this discrepancy.

Thus, linear regression can be viewed as the problem of finding the optimal parameters of a linear function that minimize the prediction error over the given dataset.

## 2. Linear Hypothesis

To model the relationship between the input variable $$x$$ and the output variable \( y \), we assume a linear form:

$$
\hat{y}_i = mx_i + b
$$

where:

- $\hat{y}_i$ is the predicted value corresponding to input $x_i$ 
- $m$ is the slope of the line, representing the rate of change of $y$ with respect to $x$
- $b$ is the intercept, representing the predicted value of $y$ when $x = 0$

This formulation defines a hypothesis space consisting of all possible lines parameterized by $m$ and $b$.

The objective is to determine the specific values of $m$  and $b$ that best approximate the observed data.

## 3. Residual Definition

For each observed data point, the discrepancy between the actual value and the predicted value is called the residual.

For the $i^{th}$ data point, the residual is defined as:

$$
e_i = y_i - \hat{y}_i
$$

Substituting the linear hypothesis, this becomes:

$$
e_i = y_i - (mx_i + b)
$$

The residual represents the error made by the model in predicting $y_i$ from $x_i$.

A good model is one in which these residuals are collectively small across all data points. Therefore, the problem of fitting a linear model reduces to minimizing these residual errors in a systematic way.

## 4. Loss Function

Since each data point produces a residual, we require a single quantity that aggregates these individual errors into a measure of overall model performance.

A common choice is the Mean Squared Error (MSE), defined as:

$$
J(m, b) = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2
$$

Substituting the linear hypothesis:

$$
J(m, b) = \frac{1}{n} \sum_{i=1}^{n} (y_i - (mx_i + b))^2
$$

This function quantifies the average squared difference between the observed values and the predicted values.

The objective is to find the parameters $m$ and $b$ that minimize this loss function. In this way, the problem of fitting a linear model is reduced to an optimization problem over the parameter space.

## 5. Why Mean Squared Error?

The choice of Mean Squared Error (MSE) as the loss function is not arbitrary. It possesses several properties that make it particularly suitable for optimization in linear regression.

First, the squared error function is continuous and differentiable with respect to the parameters $m$ and $b$. This allows the use of calculus-based methods, such as partial derivatives, to find the optimal solution.

Second, the loss function is convex with respect to the parameters in the case of linear regression. This ensures that any local minimum is also a global minimum, guaranteeing a unique optimal solution.

Third, squaring the residuals penalizes larger errors more heavily than smaller ones. This property makes the model more sensitive to significant deviations, encouraging a better overall fit to the data.

These properties make Mean Squared Error a mathematically convenient and effective choice for formulating the linear regression problem as an optimization task.

An alternative choice could be the Mean Absolute Error (MAE), which uses the absolute value of residuals instead of squaring them. However, the absolute value 
function is not differentiable at zero, which complicates the use of standard calculus-based optimization techniques. In contrast, the squared error is smooth and differentiable everywhere, making it more suitable for analytical solutions such as the closed-form derivation used in linear regression.

## 6. Partial Derivatives of the Loss

To find the values of $m$ and $b$ that minimize the loss function $J(m, b)$, we compute the partial derivatives of the loss with respect to each parameter and set them equal to zero.

The loss function is:

$$
J(m, b) = \frac{1}{n} \sum_{i=1}^{n} (y_i - (mx_i + b))^2
$$

### Partial derivative with respect to $m$:

$$
\frac{\partial J}{\partial m} = \frac{-2}{n} \sum_{i=1}^{n} x_i \left(y_i - (mx_i + b)\right)
$$

### Partial derivative with respect to $b$:

$$
\frac{\partial J}{\partial b} = \frac{-2}{n} \sum_{i=1}^{n} \left(y_i - (mx_i + b)\right)
$$

To minimize the loss, we set both partial derivatives to zero:

$$
\frac{\partial J}{\partial m} = 0 \quad \text{and} \quad \frac{\partial J}{\partial b} = 0
$$

This results in a system of equations whose solution gives the optimal values of $m$ and $b$.

## 7. Solving for the Optimal Parameters

From the previous section, the optimal values of \( m \) and \( b \) are obtained by setting the partial derivatives of the loss function equal to zero.

From

$$
\frac{\partial J}{\partial b} = \frac{-2}{n} \sum_{i=1}^{n} \left(y_i - (mx_i + b)\right) = 0
$$

we get:

$$
\sum_{i=1}^{n} y_i = m \sum_{i=1}^{n} x_i + nb
$$

which gives:

$$
b = \bar{y} - m\bar{x}
$$

where

$$
\bar{x} = \frac{1}{n}\sum_{i=1}^{n} x_i
\quad \text{and} \quad
\bar{y} = \frac{1}{n}\sum_{i=1}^{n} y_i
$$

Similarly, from

$$
\frac{\partial J}{\partial m} = \frac{-2}{n} \sum_{i=1}^{n} x_i \left(y_i - (mx_i + b)\right) = 0
$$

we obtain:

$$
\sum_{i=1}^{n} x_i y_i = m \sum_{i=1}^{n} x_i^2 + b \sum_{i=1}^{n} x_i
$$

Substituting $b = \bar{y} - m\bar{x}$ into this equation and simplifying yields the closed-form solution for the slope:

$$
m = \frac{\sum_{i=1}^{n}(x_i - \bar{x})(y_i - \bar{y})}{\sum_{i=1}^{n}(x_i - \bar{x})^2}
$$

Once $m$ is obtained, the intercept follows as:

$$
b = \bar{y} - m\bar{x}
$$

Thus, the parameters of the best-fitting line can be computed directly from the observed data using these expressions.

## 9. Interpretation of the Solution

The closed-form expressions for $m$ and $b$ provide more than just a computational method—they offer insight into how the model fits the data.

The slope $m$ captures the strength and direction of the linear relationship between $x$ and $y$. It represents the average change in the output variable for a unit change in the input variable.

The intercept $b$ represents the predicted value of $y$ when $x = 0$. Together, $m$ and $b$ define the line that best approximates the observed data under the chosen loss function.

An important property of the solution is that the regression line passes through the point $(\bar{x}, \bar{y})$, which corresponds to the mean of the observed inputs and outputs. This reflects the balancing nature of the least squares solution.

Overall, the derived line minimizes the sum of squared residuals, ensuring that the total squared deviation between predicted and observed values is as small as possible under the linear model assumption.


## 9. Closing Remark

The derivation of linear regression from first principles demonstrates how a simple predictive model can be rigorously formulated as an optimization problem. By minimizing the Mean Squared Error, the model arrives at a closed-form solution that directly depends on the statistical properties of the data.

This formulation highlights the connection between classical statistics and modern machine learning, where models are defined through objective functions and optimized with respect to their parameters.

The ideas developed here extend naturally to more complex settings, including multiple linear regression, gradient-based optimization methods, and regularized models. As such, linear regression serves as a foundational example for understanding the principles underlying a wide range of learning algorithms.
