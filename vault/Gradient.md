---

aliases:

- gradients
- partial derivatives

---
The gradient of a scalar function of several variables collects all of its partial derivatives into one vector. It points in the direction the function increases fastest.

# The idea
A partial derivative is an ordinary derivative with respect to one variable while holding all the others constant. Geometrically, slice the surface along one coordinate direction and take the slope of that slice. A function of $n$ variables has $n$ of these slopes, one per direction, and the gradient lists them together.

# Role in Numerical Computation
For [[Linear model|linear models]] $f(x, c) = V(x)c$, the gradient of the squared-error [[Loss function|loss]] with respect to the coefficients is

$$\nabla_c L = V(x)^T\big(V(x)c - y\big)$$

This is the prediction errors $V(x)c - y$, weighted by how much each coefficient affects each prediction. In general, the gradient tells [[Gradient descent|gradient descent]] which way is downhill. For a function with several outputs, the gradient generalizes to the [[Jacobian]].