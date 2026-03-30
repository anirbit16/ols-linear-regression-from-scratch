# Ordinary Least Squares (OLS) Linear Regression — From Scratch

## Overview

This repository presents a first-principles implementation of Simple Linear Regression using the Ordinary Least Squares (OLS) method.

The objective of this work is to bridge the gap between mathematical derivation and practical implementation by building the regression model entirely from scratch and validating it against Scikit-Learn.

---

## Key Components

- Mathematical derivation of linear regression parameters  
- Closed-form solution for slope and intercept  
- Implementation using NumPy (no ML libraries used for training)  
- Visualization of regression fit  
- Residual analysis  
- Evaluation using Mean Squared Error (MSE) and R²  
- Validation against Scikit-Learn  

---

## Regression Model

The model is defined as:

$$
y = mx + b
$$

Where:

- $m$ is the slope  
- $b$ is the intercept  

The parameters are computed using the closed-form OLS solution.

---

## Results

### Regression Fit

![Regression Plot](images/regression_plot.png)

### Residual Analysis

![Residual Plot](images/residual_plot.png)

---

## Project Structure
```
.
├── notebooks/
│   └── linear_regression_from_scratch.ipynb
├── images/
│   ├── regression_plot.png
│   └── residual_plot.png
└── README.md
``````

 
---

## Validation

The manually computed parameters match those obtained from Scikit-Learn’s `LinearRegression`, confirming the correctness of the implementation.

---

## Conclusion

This project demonstrates the complete workflow of linear regression:

- From mathematical derivation  
- To implementation  
- To evaluation and validation  

It serves as a foundational step toward understanding optimization-based learning algorithms used in modern machine learning.

---

## Future Work

- Gradient Descent for Linear Regression  
- Multiple Linear Regression  
- Regularization (Ridge and Lasso)  
- Logistic Regression  
