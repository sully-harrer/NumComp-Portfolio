---
aliases:
  - FFT
---
The Fast Fourier Transform (FFT) is an algorithm that computes the [[Discrete Fourier transform]] in $O(n \log n)$ operations instead of $O(n^2)$, by splitting the transform in half recursively.

# The idea
A transform of length $n$ can be rebuilt from two transforms of length $n/2$, one of the even-indexed samples and one of the odd-indexed samples. Each half-size transform splits again, and so on, down to transforms of length 1. Recombining at each level costs about $n$ work, and there are $\log_2 n$ levels.

# Role in Numerical Computation
Because the DFT matrix is unitary, the Fourier basis is perfectly [[Conditioning|conditioned]], and with the FFT it is nearly as cheap as reading the data. That combination makes it central to signal processing, weather and climate models, molecular dynamics, and turbulence simulation.

The trick extends to [[Chebyshev polynomials]]. [[Chebyshev points|Cosine-spaced points]] are the shadows, on the $x$-axis, of equally spaced points on a circle, so a Chebyshev transform can also be computed with an FFT in $O(n\log n)$.

Fast transforms are also the main escape from the cost of interpolating in many dimensions. A grid with 10 points per dimension in $d$ dimensions has $10^d$ points, so an $O(n^3)$ solve becomes impossible within a few dimensions, while $O(n\log n)$ stays feasible much longer.
