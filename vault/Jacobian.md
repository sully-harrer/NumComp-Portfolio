---

aliases:

- Jacobian matrix

---
The Jacobian of a vector-valued function is the matrix of all its partial derivatives, with one row per output and one column per input. Each row is the [[Gradient|gradient]] of one output.

# The idea
A function $\mathbf f(\mathbf x)$ with several outputs has a gradient for each output. Stacking those rows gives a matrix whose entry in row $i$, column $j$ answers: if I nudge input $j$, how fast does output $i$ change?

# Role in Numerical Computation
In regression, the model's predictions at all the data points form a vector $f(x, c)$. Its Jacobian with respect to the coefficients, $\nabla_c f$, sets the gradient of the [[Loss function|loss]].

For a [[Linear model|linear model]], this Jacobian is the [[Vandermonde matrix]] $V(x)$, which doesn't depend on $c$. For [[Nonlinear regression|nonlinear regression]], it changes with $c$.