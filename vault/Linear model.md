---

aliases:

- linear models
- linear regression

---

A linear model is a predictive model $f(x, c)$ that is linear in its coefficients $c$. It does not have to be linear in $x$.

# The idea
Fitting a polynomial to data means finding coefficients $c$ such that

$$V(x),c \approx y$$

where $V(x)$ is a [[Vandermonde matrix]] and $y$ is the data. Each prediction is a weighted sum of basis functions, and the coefficients only enter by multiplying and adding. So even though $x^7$ is nothing like a straight line in $x$, the model is linear in the thing we're solving for.

# Standard assumptions
1. The $x$ values have no error.
2. The model $f(x, c)$ is linear in $c$.
3. The noise in each $y$ is independent of the others.
4. The noise in $y$ has constant variance.

Any of these can fail in practice. Relaxing them means changing the model or the [[Loss function|loss function]], which leads to [[Nonlinear regression|nonlinear regression]].

# Role in Numerical Computation
Linearity in $c$ is what turns fitting into a linear algebra problem. Fitting a linear model with squared error is a [[Least squares|least squares]] problem, which has a single minimum and a direct, stable solution with [[QR Factorization|QR]].

Choosing the basis functions, such as [[Chebyshev polynomials]] instead of monomials, changes the [[Conditioning|condition number]] of $V$ and the [[Stability|stability]] of the computation, but not which functions the model can represent. How flexible the model should be is a separate question, governed by the [[Bias-variance tradeoff|bias–variance tradeoff]].