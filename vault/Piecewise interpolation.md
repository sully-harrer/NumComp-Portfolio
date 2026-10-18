---
aliases:
---
Piecewise interpolation builds the interpolant from separate simple pieces, one per region between data points, instead of one global function across all of them.

# The idea
In [[Polynomial interpolation]] with a single polynomial, every data point influences the curve everywhere. The [[Runge phenomenon]] showed that that is what makes it ill-conditioned on badly placed points. A piecewise method keeps each data point's influence local, so the value at any location depends only on the data nearby.

# Nearest neighbor
At each evaluation point, simply copy the value of the nearest data point. The result is a staircase.

![[Pasted image 20261018155435.png]]

Every output is a copy of some input, so the method can never amplify the data because the largest output is never bigger than the largest input. 

# Piecewise linear
Connect neighboring data points with straight lines. This is still local and well-conditioned, and more accurate than a staircase but the result has a corner at every data point, where the slope jumps.

# Accuracy
Piecewise methods are well-conditioned but converge slowly. 

| Method                                             | Conditioning                                           | Convergence                               |
| -------------------------------------------------- | ------------------------------------------------------ | ----------------------------------------- |
| Nearest neighbor                                   | Well-conditioned on any set of points                  | Very slow; needs many points for accuracy |
| Global polynomial (e.g. [[Chebyshev polynomials]]) | Ill-conditioned unless the points are chosen carefully | Exponential for smooth enough functions   |

# Role in Numerical Computation
Piecewise interpolation makes the opposite trade from global polynomial interpolation. Global polynomials converge fast for smooth functions but need special points like [[Chebyshev points]] to stay [[Conditioning|well-conditioned]]. Piecewise methods are well-conditioned on any points but need many points for accuracy. [[Cubic splines]] are the compromise because they are still piecewise and well-conditioned, but smooth and much more accurate.
