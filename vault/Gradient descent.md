---

aliases:

- steepest descent
- learning rate

---
Gradient descent minimizes a function by repeatedly taking a small step in the direction of the negative [[Gradient|gradient]], which is downhill.

# The idea
Stand somewhere on the [[Loss function|loss]] surface, find the steepest way downhill, take a step that way, and repeat. Stop when the gradient is nearly zero, meaning the ground is flat, or after a fixed number of steps.

A step needs only the gradient, with no matrix factorization, so it costs about as much as evaluating the model once. That is why it's used for models that have no direct way to solve them, such as [[Nonlinear regression|nonlinear regression]], and for problems too large to reasonably factor.

# Role in Numerical Computation
For a [[Linear model|linear model]] with squared error, the condition number is $\kappa(V)^2$, which is why gradient descent is slow for linear regression and [[Least squares|QR]] is the better. 

Gradient descent can get stuck at local minima. For a linear model the loss is a single bowl, so this can't happen. For [[Nonlinear regression|nonlinear regression]], the starting point matters, like the initial guess in [[Newton's method]].