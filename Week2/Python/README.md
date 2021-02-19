# Linalg module in NumPy and SciPy

## General introduction
Linear algebra is a branch of mathematics focusing on linear equations, linear maps, and their matrix representation in a vector space. Not only for convenienece purpose, also with some algorithms in linear algebra and with hardware (e.x., GPU) support for matrix representation in a computing device, we can complete fast computatio over arge scale of data, that is why linear algebra is popular in modern engineering and data science field like machine learning and data analysis. NumPy has a module called __linalg__, which contains a bunch of fast implementation for linear algebra operations, including:
 - Matrix and vector products (e.x., dot product)
 - Decompositions (e.x., singular value decomposition)
 - Matrix eigenvalues
 - Norms and other numbers (e.x., condition number, trace, determinant)
 - Solving equations and inverting matrices

The implementation is based on:
1. Basic linear algebra algorithm
2. Fast numerical algorithm in computing field (e.x., LU decomposition for solving the inverse of a square matrix in SciPy)
3. Hardware support (e.x., parallel computation)

## Introduction from official document
### Hardware library support
<i>The NumPy linear algebra functions rely on BLAS and LAPACK to provide efficient low level implementations of standard linear algebra algorithms. Those libraries may be provided by NumPy itself using C versions of a subset of their reference implementations but, when possible, highly optimized libraries that take advantage of specialized processor functionality are preferred. Examples of such libraries are OpenBLAS, MKL (TM), and ATLAS. Because those libraries are multithreaded and processor dependent, environmental variables and external packages such as threadpoolctl may be needed to control the number of threads or specify the processor architecture.</i>

__note:__ Libraries (e.x., MKL) above are from Intel device.

### SciPy Linalg vs. Numpy Linalg
<i>The SciPy library also contains a linalg submodule, and there is overlap in the functionality provided by the SciPy and NumPy submodules. SciPy contains functions not found in numpy.linalg, such as functions related to LU decomposition and the Schur decomposition, multiple ways of calculating the pseudoinverse, and matrix transcendentals such as the matrix logarithm. Some functions that exist in both have augmented functionality in scipy.linalg. For example, scipy.linalg.eig can take a second matrix argument for solving generalized eigenvalue problems. Some functions in NumPy, however, have more flexible broadcasting options. For example, numpy.linalg.solve can handle “stacked” arrays, while scipy.linalg.solve accepts only a single square array as its first argument.</i>

<i>numpy.linalg for more linear algebra functions. Note that although scipy.linalg imports most of them, identically named functions from scipy.linalg may offer more or slightly differing functionality.</i>

## Example
I will share some examples on linear algebra operations with NumPy.
```python
import numpy as np
import numpy.linalg as nla
import scipy
import scipy.linalg as sla

np.random.seed(0)

A = np.diag([3, 4, 5])
# output:
#[[3 0 0]
# [0 4 0]
# [0 0 5]]
print(A)

B = 2 * np.eye(3)
# output:
#[[2. 0. 0.]
# [0. 2. 0.]
# [0. 0. 2.]]
print(B)

# Matrix and vector products
# <A, B>: inner product/dot product
# of real matrices
C1 = np.dot(A, B)
C2 = A @ B
C3 = np.inner(A, B)
C4 = np.matmul(A, B)
C5 = nla.multi_dot([A, B])
# output
#[[ 6.  0.  0.]
# [ 0.  8.  0.]
# [ 0.  0. 10.]]
print(C1)
print(C2)
print(C3)
print(C4)
print(C5)

# Matrix eigenvalues
C = nla.eig(A)
# eigenvalues: array([3., 4., 5.])
# eigenvactors:
#array([[1., 0., 0.],
#       [0., 1., 0.],
#       [0., 0., 1.]])
print(C)


# interesting tricks
# upper/lower triangular matrices with no
# 0 diag entries are always invertible
D = np.triu(np.random.uniform(1, 2, [3, 3]))
E = np.tril(np.random.uniform(1, 2, [3, 3]))
print(D)
print(E)

# Norms and other numbers
norm1 = nla.norm(A, ord=2)
norm2 = nla.norm(A, ord=np.inf)
norm3 = nla.norm(B, ord=2)
norm4 = nla.norm(B, ord=np.inf)
# output: 5.0, 5.0, 2.0, 2.0
print(norm1)
print(norm2)
print(norm3)
print(norm4)

# condition: robustness of output w.r.t. input perturbation
cond1 = nla.cond(A)
cond2 = nla.cond(B)
# output: 1.6666666666666667, 1.0
print(cond1)
print(cond2)

det1 = nla.det(A)
det2 = nla.det(B)
# output: 59.999999999999986 (60), 7.999999999999998 (8)
# not to integer because of floating point representation (binary)
# in Python
print(det1)
print(det2)

# since invertible
# rank = dim = 3
rank1 = nla.matrix_rank(D)
rank2 = nla.matrix_rank(E)
# output: 3, 3
print(rank1)
print(rank2)

trace1 = np.trace(A)
trace2 = np.trace(B)
# output: 12, 6.0
print(trace1)
print(trace2)

# Solving equations and inverting matrices
b = np.array([2, 2, 2])
# solve the linear system Ax = b
x1 = nla.solve(A, b)
x2 = nla.solve(B, b)
# output:
# x1 = [0.66666667 0.5        0.4       ]
# x2 = [1. 1. 1.]
print(x1)
print(x2)

# find the inverse of two triangular matrices
D_inv = sla.inv(D)
E_inv = sla.inv(E)

# both approximate identity matrix I
# not exactly I because of floating point
# representation in Python

# output:
#[[1.00000000e+00 1.20161995e-16 6.36029629e-17]
# [0.00000000e+00 1.00000000e+00 5.95554906e-17]
# [0.00000000e+00 0.00000000e+00 1.00000000e+00]]

#[[1.00000000e+00 0.00000000e+00 0.00000000e+00]
# [8.78986329e-17 1.00000000e+00 0.00000000e+00]
# [6.66350615e-17 7.80748077e-17 1.00000000e+00]]

print(D_inv @ D)
print(E_inv @ E)

# Decompositions
# Cholesky decomposition
cho1 = sla.cholesky(A)
cho2 = sla.cholesky(B)
# output:
# cho1 = 
#[[1.73205081 0.         0.        ]
# [0.         2.         0.        ]
# [0.         0.         2.23606798]]
# cho2 =
#[[1.41421356 0.         0.        ]
# [0.         1.41421356 0.        ]
# [0.         0.         1.41421356]]
print(cho1)
print(cho2)

# singular value decomposition
svd1 = nla.svd(A)
svd2 = nla.svd(B)
# output (in the form U, s: singular values, V.T)
# svd1 =
#(array([[0., 0., 1.],
#       [0., 1., 0.],
#       [1., 0., 0.]]), array([5., 4., 3.]), array([[0., 0., 1.],
#       [0., 1., 0.],
#       [1., 0., 0.]]))
# svd2 =
#(array([[1., 0., 0.],
#       [0., 1., 0.],
#       [0., 0., 1.]]), array([2., 2., 2.]), array([[1., 0., 0.],
#       [0., 1., 0.],
#       [0., 0., 1.]]))
print(svd1)
print(svd2)
```

## Reference
- [Linear algebra](https://en.wikipedia.org/wiki/Linear_algebra)
- [Linear algebra (numpy.linalg)](https://numpy.org/doc/stable/reference/routines.linalg.html)
- [Linear algebra (scipy.linalg)](https://docs.scipy.org/doc/scipy/reference/linalg.html)
