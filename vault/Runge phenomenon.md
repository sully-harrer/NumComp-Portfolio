---
aliases:
  - Runge
  - Runge function
---
The Runge phenomenon refers to the wild oscillation near the ends of an interval when a smooth function is interpolated by a single polynomial at equally spaced points. Adding more points makes it worse, not better. 

# The idea
The classic example is the Runge function, a smooth bump on $[-1, 1]$:
$$f(x) = \frac{1}{1 + 10x^2}$$

With 20 equally spaced points, the interpolating polynomial matches the bump in the middle but swings far above and below it near $x = \pm 1$. The function itself is perfectly well-behaved, the problem is with the method.
![[Pasted image 20261018160401.png]]

# Role in Numerical Computation
Runge is the standard example of separating [[Conditioning]] from [[Stability]]. A stable algorithm (a good basis in this case) can't fix an ill-conditioned problem (bad points).

In [[Bias-variance tradeoff|bias–variance]] terms, the oscillation is variance, and polynomial fits have variance that piles up at the ends of the interval no matter which basis computes them. For periodic functions, the [[Discrete Fourier transform|Fourier basis]] on equally spaced points avoids the problem entirely.
