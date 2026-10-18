---
aliases:
---
A cubic spline is a [[Piecewise interpolation|piecewise]] cubic polynomial that passes through every data point and has continuous first and second derivatives, so the pieces join into one smooth curve.

# The idea
As we saw with the [[Runge phenomenon]], a single high-degree polynomial passing through many points is ill-conditioned. We could instead use straight lines or [[Piecewise interpolation|nearest neighbor]], but the interpolant then becomes rough. 

A spline takes the middle path between rough lines and high degree polynomials. It uses a low-degree polynomial on each interval between data points, and spends each piece's leftover freedom on making the joins smooth. With cubics, the joins are smooth enough that you can't see them.

The spline is a cubic $s_i(x)$ on each interval $[x_i, x_{i+1}]$, for $n$ pieces total.

# Role in Numerical Computation
Splines are built for an arbitrary distribution of points, where interpolating with a single polynomial is not robust. On equally spaced points, polynomial interpolation is [[Conditioning|ill-conditioned]] no matter which basis computes it, because the problem comes from the polynomial space rather than the basis. Splines change the space, and their interpolation operator is well-conditioned.

The smoothness conditions tie each piece to its neighbors, so the spline is globally coupled and all the pieces are solved for together. Compared with [[Piecewise interpolation|nearest neighbor]] interpolation, which is well-conditioned but converges very slowly, splines stay well-conditioned while improving accuracy and giving a smooth curve.
