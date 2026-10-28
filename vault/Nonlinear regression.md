---

aliases:

- nonlinear least squares
- nonlinear models

---
Nonlinear regression fits a model to data when the model is not linear in its coefficients. The goal is to minimize [[Loss function|loss]], but the coefficients can't be solved for and have to be found iteratively. 

# The idea
A [[Linear model|linear model]] is a weighted sum of fixed basis functions. The coefficients control how much of each basis function to use, so the shapes the model can make are limited to combinations of those functions. To capture a shape the basis doesn't naturally produce, you have to add more basis functions.

A nonlinear model lets the coefficients change the shape itself, such as where a peak sits, how wide it is, or how fast something decays. If the form of the model matches the kind of behavior in the data, a few coefficients can describe what a linear model would need many for.

# What changes
For a nonlinear model, the gradient is still each prediction's error weighted by how sensitive that prediction is to each coefficient. Those sensitivities form the [[Jacobian]] of the model. In a linear model the sensitivities are fixed, but in a nonlinear model they depend on the current coefficients. Setting the gradient to zero gives nonlinear equations that usually have no closed-form solution.

Instead of trying to solve, start from a guess, use the gradient to find which way is downhill, step, and repeat, as in [[Gradient descent|gradient descent]].

That has two consequences:
- The loss surface no longer has to be a single bowl. It can have several valleys and flat saddle points, so a zero gradient is necessary for a minimum but no longer sufficient. Which minimum you reach depends on where you start, as with the initial guess in [[Newton's method]].
- Every step needs derivatives of the model, evaluated at the current coefficients. For complicated models, working these out by hand gets tedious and error-prone.

# Role in Numerical Computation
Nonlinear regression trades a harder optimization problem for a better model. Matching the form of the model to the data can lower bias without adding many coefficients, and fewer coefficients means less variance, so it shifts the [[Bias-variance tradeoff|bias–variance tradeoff]]. The cost is an iterative method that depends on a good starting point and on derivatives at every step.