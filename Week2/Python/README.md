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

## Example
I will share some examples on linear algebra operations with NumPy.

## Reference
- [Linear algebra](https://en.wikipedia.org/wiki/Linear_algebra)
- [Linear algebra (numpy.linalg)](https://numpy.org/doc/stable/reference/routines.linalg.html)
