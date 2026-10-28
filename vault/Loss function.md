---

aliases:

- loss
- objective function

---

A loss function measures how poorly a model with coefficients $c$ fits the data. Fitting a model becomes minimizing its loss.

# The idea
Each prediction $f(x_i, c)$ misses its data point $y_i$ by some amount. The loss adds those misses into one score. Problems of fit can then be re-interpreted by thinking about minimizing the loss. 

$$L(c; x, y) = \sum_i \tfrac12 \big(f(x_i, c) - y_i\big)^2 = \tfrac12 \lVert f(x, c) - y \rVert^2$$

Each term in the sum is the error on one data point, squared. The [[Norm|norm]] form adds them all at once, where $f(x, c)$ is the vector of all the predictions. The $\tfrac12$ is only there so that the 2 cancels when you take the [[Gradient|gradient]]. The semicolon separates what we choose, the coefficients $c$, from what is fixed, the data $x$ and $y$.

# Role in Numerical Computation
For a [[Linear model|linear model]], minimizing squared error is [[Least squares|least squares]].

The loss is also the key to relaxing the assumptions of [[Linear model|linear models]] because we can change the model or the loss, and the same ideas still apply. Designing the loss to be differentiable in $c$ lets you use [[Gradient descent|gradient descent]] and other gradient-based methods, which is how [[Nonlinear regression|nonlinear regression]] works.