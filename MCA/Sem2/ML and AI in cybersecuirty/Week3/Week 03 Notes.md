# 3.1
## Calculate the MSE manually on a tiny dataset.
- **~={red}What is Mean Squared Error=~** - **MSE** : is a measure that **~={yellow}calculates the avg of all the squared difference between ur predicted values and the actual values.=~**
- **COST FUNCTION** is the same thing as **MSE**
- **FUNCTION** is $$y=mx + c$$
- **Formula**
- $$MSE = \frac{1}{n}\sum_{i=1}^{n}(y_i - f(x_i))^2$$
# 3.3
## Gradient Descent Algorithm
- **What is it:** Gradient Descent is an optimization algorithm that automatically finds the best value of a parameter (like m) by repeatedly moving in the direction that reduces the cost function (MSE) the most.
- **Formula**
- $$ m=m-\alpha \nabla J(m, y) $$
# 3.6 Regularization 
## How can we control overfitting within algorithm

## Overfitting 
- Your model memorizes the training data too well, so it works great on training data but terrible on new test data.

## Underfitting
- Your model is too simple and doesn't learn the pattern well enough, so it performs poorly on both training and test data. It's like not studying enough for a test.