---
aliases:
  - bias
  - variance
  - overfitting
  - bias-variance
---
The bias–variance tradeoff describes how a fit to noisy data can go wrong. The model can be too simple to capture the true function (bias), or flexible enough to chase the noise (variance).

# The idea
Suppose the data are samples of a true function plus random noise, $y = f(x) + \epsilon$, and you fit a model $\hat f$ by [[Least squares]]. If you collected a fresh noisy sample and refit, you'd get a slightly different $\hat f$. Bias asks whether the fits are right on average, while variance asks how much the fits scatter from one sample to the next.

A low-degree polynomial gives nearly the same fit every time (low variance), but it's too stiff to follow a sharp peak, so it is consistently wrong there (high bias). A high-degree polynomial can follow the peak (low bias), but it also bends to follow whatever random wiggles a particular sample happened to have (high variance). Following the noise instead of the function is called overfitting.

# Role in Numerical Computation
Interpolation is the extreme case of this trade-off because there are as many basis functions as data points, zero training residual, and maximum variance. The [[Runge phenomenon]] is variance concentrated at the ends of the interval. It is a property of the polynomial space, not of the basis used to compute the fit, so switching to a better basis like [[Chebyshev polynomials]] affects [[Stability]] but not variance. Reducing variance requires changing the space, the points, or the objective.
