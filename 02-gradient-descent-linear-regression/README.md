# Gradient Descent for Linear Regression

This module demonstrates how Gradient Descent can be used to optimize a Simple Linear Regression model from scratch.

Unlike the closed-form solution, Gradient Descent approaches the optimization problem iteratively. The model starts with initial values for the slope and intercept, then updates them step by step to minimize the Mean Squared Error loss.

---

## Topics Covered

- Simple Linear Regression recap
- Mean Squared Error loss function
- Gradient Descent intuition
- Batch Gradient Descent
- Learning rate
- Parameter updates for slope and intercept
- Loss reduction over iterations
- Python implementation from scratch
- Regression line and loss curve visualization

---

## Mathematical Formulation

The loss function is:

$$
J(m,b)=\frac{1}{n}\sum_{i=1}^{n}\left(y_i-(mx_i+b)\right)^2
$$

The parameters are updated using:

$$
m := m-\alpha \frac{\partial J}{\partial m}
$$

$$
b := b-\alpha \frac{\partial J}{\partial b}
$$

where $\alpha$ is the learning rate.
## Module Structure 
```
02-gradient-descent-linear-regression/
├── README.md
├── theory.md
├── notebooks/
│   └── gradient_descent_linear_regression.ipynb
└── images/
    ├── initial_fit.png
    ├── final_fit.png
    └── loss_curve.png
```
## Objective

The objective of this module is to understand Gradient Descent as an optimization method for Linear Regression.

The implementation focuses on how the slope and intercept are gradually updated using gradients, and how these updates reduce the loss over multiple iterations.

In this module, Gradient Descent refers to **Batch Gradient Descent** unless stated otherwise.
