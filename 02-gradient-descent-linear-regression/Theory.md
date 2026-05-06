# Gradient Descent for Linear Regression

## 1. Problem Setup
Simple linear regression models the relationship between an input variable and an $x$ and an output variable $y$ using a straight line.</br>
The prediction for the $i^{th}$ data point is: 

$$
\hat{y}_i = mx_i + b
$$

where:

- $x_i$ is the input value
- $y_i$ is the actual output value
- $\hat{y}_i$ is the predicted output value
- $m$ is the slope
- $b$ is the intercept
## 2. Loss Function

To measure how well the model is performing, we use a loss function.

For Linear Regression, a common choice is Mean Squared Error.

$$
J(m,b) = \frac{1}{n}\sum_{i=1}^{n}(y_i - \hat{y}_i)^2
$$

Since the predicted value is:

$$
\hat{y}_i = mx_i + b
$$

the loss can also be written as:

$$
J(m,b) = \frac{1}{n}\sum_{i=1}^{n}(y_i - (mx_i+b))^2
$$

This loss function gives a single value that represents the average squared difference between the actual and predicted values.

The objective is:

$$
\min_{m,b} J(m,b)
$$

This means we want to find the values of \(m\) and \(b\) that make the loss as small as possible.


## 3. From Closed-Form Solution to Gradient Descent
In Simple Linear Regression, the optimal values of \(m\) and \(b\) can be found directly using the closed-form solution.

The slope is given by:

$$
m =
\frac{\sum_{i=1}^{n}(x_i-\bar{x})(y_i-\bar{y})}
{\sum_{i=1}^{n}(x_i-\bar{x})^2}
$$

and the intercept is:

$$
b = \bar{y} - m\bar{x}
$$

This gives the best-fitting line directly for Simple Linear Regression. Gradient Descent approaches the same </br>
optimization problem differently.

Instead of calculating the best parameters in one step, it starts with initial values for \(m\) and \(b\), then updates them repeatedly to reduce the loss.

So the main difference is:

- Closed-form solution solves for the optimal parameters directly
- Gradient Descent learns the parameters step by step through repeated updates

This makes Gradient Descent important because many machine learning models do not have simple closed-form solutions, or direct computation may become expensive for large datasets.
## 4. Basic Idea of Gradient Descent
Gradient descent is an iterative optimization algorithm. It starts with initial values for the parameters </br>
and improves them step by step.

For Simple Linear Regression, the parameters are:

$$
m
\quad \text{and} \quad
b
$$

At the beginning, these values may not fit the data well, so the loss may be high.

Gradient Descent repeatedly performs the following steps:
1. Make predictions using the current values of \(m\) and \(b\)
2. Calculate the loss
3. Calculate how the loss changes with respect to \(m\) and \(b\)
4. Update \(m\) and \(b\) in a direction that reduces the loss
5. Repeat the process for multiple iterations

The core idea is that the model does not find the best parameters immediately.  
Instead, it gradually moves toward better parameter values by using information from the loss function.


## 5. Gradient Descent Update Rule
Gradient Descent updates model parameters by moving them in the opposite direction of the gradient.</br>

The general idea is:

$$
\text{new parameter} = \text{old parameter} - \alpha \times \text{gradient}
$$

For this Linear Regression model, the parameters are \(m\) and \(b\). Therefore, the update rules become:

$$
m_{\text{new}} = m_{\text{old}} - \alpha \frac{\partial J}{\partial m}
$$

where:

- $m_{\text{old}}$ and $b_{\text{old}}$ are the current parameter values
- $m_{\text{new}}$ and $b_{\text{new}}$ are the updated parameter values
- $J(m,b)$ is the loss function
- $\frac{\partial J}{\partial m}$ is the gradient of the loss with respect to \(m\)
- $\frac{\partial J}{\partial b}$ is the gradient of the loss with respect to \(b\)
- $\alpha$  is the learning rate

The gradients tell us how the loss changes when the parameters are changed.</br>
The learning rate controls the size of each update step.



## 6. Why Move Opposite to the Gradient?
The gradient points in the direction where the loss increases the fastest.</br>
Since the goal of training is to reduce the loss, Gradient Descent moves in the opposite direction of the gradient.</br>
For example, consider the update rule for \(m\):

$$
m_{\text{new}} = m_{\text{old}} - \alpha \frac{\partial J}{\partial m}
$$

If:

$$
\frac{\partial J}{\partial m} > 0
$$

then increasing \(m\) increases the loss. So Gradient Descent decreases \(m\).

If:

$$
\frac{\partial J}{\partial m} < 0
$$

then increasing \(m\) decreases the loss. So Gradient Descent increases \(m\).

## 7. Deriving the Gradients

The loss function is:

$$
J(m,b) = \frac{1}{n}\sum_{i=1}^{n}(y_i - (mx_i+b))^2
$$

To update \(m\) and \(b\), we need the gradients:

$$
\frac{\partial J}{\partial m}
\quad \text{and} \quad
\frac{\partial J}{\partial b}
$$

Let the error term be:

$$
e_i = y_i - (mx_i+b)
$$

So the loss becomes:

$$
J(m,b) = \frac{1}{n}\sum_{i=1}^{n}e_i^2
$$

For one data point, the squared error is:

$$
e_i^2 = (y_i - (mx_i+b))^2
$$

Differentiating with respect to \(m\):

$$\frac{\partial}{\partial m}(y_i - (mx_i+b))^2 = 2(y_i - (mx_i+b)) \cdot \frac{\partial}{\partial m}(y_i - (mx_i+b))$$

Differentiating with respect to \(b\):

$$\frac{\partial}{\partial b}(y_i - (mx_i+b))^2=2(y_i - (mx_i+b))(-1)$$


Therefore, for the full loss function:

$$
\frac{\partial J}{\partial m} =
-\frac{2}{n}\sum_{i=1}^{n}x_i(y_i - (mx_i+b))
$$

$$
\frac{\partial J}{\partial b} =
-\frac{2}{n}\sum_{i=1}^{n}(y_i - (mx_i+b))
$$

These gradients are used in the update rules to adjust \(m\) and \(b\).


## 8. Learning Rate

The learning rate, denoted by $\alpha$, controls the size of each update step in Gradient Descent.

The update rule is:

$$
\text{new parameter} = \text{old parameter} - \alpha \times \text{gradient}
$$

If the learning rate is too small, the model updates very slowly and may take many iterations to reach a good solution.

If the learning rate is too large, the updates may become unstable. The model may overshoot the minimum and the loss may increase instead of decreasing.

A suitable learning rate allows the parameters to move steadily toward values that reduce the loss.

In practice, the learning rate is chosen experimentally by observing how the loss changes over iterations.

## 9. Algorithm Summary

In this module, Gradient Descent refers to **Batch Gradient Descent**.  
This means the gradients are calculated using the entire training dataset before each parameter update.

The algorithm follows these steps:

1. Initialize the parameters \(m\) and \(b\)
2. Choose a learning rate \(\alpha\)
3. Make predictions using the current parameters:

$$
\hat{y}_i = mx_i + b
$$

4. Calculate the loss:

$$
J(m,b) = \frac{1}{n}\sum_{i=1}^{n}(y_i - \hat{y}_i)^2
$$

5. Calculate the gradients:

$$
\frac{\partial J}{\partial m} =
-\frac{2}{n}\sum_{i=1}^{n}x_i(y_i - (mx_i+b))
$$

$$
\frac{\partial J}{\partial b} =
-\frac{2}{n}\sum_{i=1}^{n}(y_i - (mx_i+b))
$$

6. Update the parameters:

$$
m_{\text{new}} = m_{\text{old}} - \alpha \frac{\partial J}{\partial m}
$$

$$
b_{\text{new}} = b_{\text{old}} - \alpha \frac{\partial J}{\partial b}
$$

7. Repeat the process for multiple iterations until the loss becomes small or stops decreasing significantly.

Gradient Descent gradually improves the model by using the gradients to reduce the loss step by step.

## 8. Learning Rate

The learning rate, denoted by $\alpha$, controls the size of each update step in Gradient Descent.

The update rule is:

$$
\text{new parameter} = \text{old parameter} - \alpha \times \text{gradient}
$$

If the learning rate is too small, the model updates very slowly and may take many iterations to reach a good solution.

If the learning rate is too large, the updates may become unstable. The model may overshoot the minimum and the loss may increase instead of decreasing.

A suitable learning rate allows the parameters to move steadily toward values that reduce the loss.

In practice, the learning rate is chosen experimentally by observing how the loss changes over iterations.

## 9. Algorithm Summary

In this module, Gradient Descent refers to **Batch Gradient Descent**.  
This means the gradients are calculated using the entire training dataset before each parameter update.

The algorithm follows these steps:

1. Initialize the parameters \(m\) and \(b\)
2. Choose a learning rate \(\alpha\)
3. Make predictions using the current parameters:

$$
\hat{y}_i = mx_i + b
$$

4. Calculate the loss:

$$
J(m,b) = \frac{1}{n}\sum_{i=1}^{n}(y_i - \hat{y}_i)^2
$$

5. Calculate the gradients:

$$
\frac{\partial J}{\partial m} =
-\frac{2}{n}\sum_{i=1}^{n}x_i(y_i - (mx_i+b))
$$

$$
\frac{\partial J}{\partial b} =
-\frac{2}{n}\sum_{i=1}^{n}(y_i - (mx_i+b))
$$

6. Update the parameters:

$$
m_{\text{new}} = m_{\text{old}} - \alpha \frac{\partial J}{\partial m}
$$

$$
b_{\text{new}} = b_{\text{old}} - \alpha \frac{\partial J}{\partial b}
$$

7. Repeat the process for multiple iterations until the loss becomes small or stops decreasing significantly.

Gradient Descent gradually improves the model by using the gradients to reduce the loss step by step.
