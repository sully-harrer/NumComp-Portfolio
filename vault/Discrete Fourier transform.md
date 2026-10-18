---
aliases:
  - DFT
  - Fourier basis
  - Fourier transform
---
The discrete Fourier transform (DFT) rewrites $n$ equally spaced samples of a periodic signal as a combination of $n$ complex waves of different frequencies. It is [[Polynomial interpolation|interpolation]] with waves in place of polynomials.

# The idea
Polynomials are a natural basis for functions on an interval. For periodic functions, the natural basis is waves. Euler's formula, $e^{i\theta x} = \cos\theta x + i\sin\theta x$, packs each cosine–sine pair into one complex exponential, so the basis becomes $e^{i\theta_k x}$ for a set of frequencies $\theta_k$.

Each coefficient $\hat f_k$ says how much of frequency $\theta_k$ is in the signal. The transform answers the question: which mix of pure waves adds up to these samples?

# As a Vandermonde matrix
Evaluating the wave basis at the sample points gives a [[Vandermonde matrix]] whose columns are waves:
$$\mathcal F = \Big[\, e^{i\theta_1 x} \,\Big|\, e^{i\theta_2 x} \,\Big|\, \cdots \Big]$$

Finding the coefficients means solving $\mathcal F\hat f = f$, the same kind of system as in polynomial interpolation.

What makes this case special is that with $n$ equally spaced samples and frequencies, the scaled matrix is unitary, which is the complex version of an [[Orthogonality#Orthonormal vectors and orthogonal matrices|orthogonal matrix]]. Its columns are orthonormal, and its inverse is its conjugate transpose $\mathcal F^H$ whereby you transpose, then flip the sign of every imaginary part. 

So the system never has to be solved. The coefficients are
$$\hat f_k = \sum_{\ell=0}^{n-1} e^{-2\pi i k\ell/n} f_\ell$$
Each coefficient is an [[Inner product|inner product]] of the samples with one wave, measuring how well the signal lines up with that frequency. The minus sign in the exponent comes from the conjugate.

# Role in Numerical Computation
For periodic data on equally spaced points, the Fourier basis is perfectly conditioned, since a unitary matrix has [[Conditioning|condition number]] $1$. Scaling a matrix doesn't change its condition number, so $\mathcal F$ itself also has $\kappa = 1$. Equally spaced points are exactly [[Runge phenomenon|where polynomial interpolation fails]], so for periodic functions, Fourier interpolation sidesteps the problem.

Computing the coefficients by applying $\mathcal F^H$ directly is a matrix–vector product costing $O(n^2)$, already far cheaper than the $O(n^3)$ of a general solve. The [[Fast Fourier Transform]] cuts the cost to $O(n \log n)$.

Working in the Fourier basis also makes calculus easy, because differentiating $e^{i\theta_k x}$ just multiplies it by $i\theta_k$. To differentiate a periodic signal, transform it, multiply each coefficient by $i\theta_k$, and transform back.
