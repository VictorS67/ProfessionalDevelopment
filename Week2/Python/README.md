# Linalg module in NumPy and SciPy

## General introduction
Linear algebra is a branch of mathematics focusing on linear equations, linear maps, and their matrix representation in a vector space. Not only for convenienece purpose, also with some algorithms in linear algebra and with hardware (e.x., GPU) support for matrix representation in a computing device, we can complete fast computatio over arge scale of data, that is why linear algebra is popular in modern engineering and data science field like machine learning and data analysis. NumPy has a module called __linalg__, which contains a bunch of fast implementation for linear algebra operations, including:
 - Matrix and vector products
 - Decompositions (e.x., singular value decomposition)
 - Matrix eigenvalues
 - Norms and other numbers (e.x., condition number, trace, determinant)
 - Solving equations and inverting matrices

The implementation is based on:
1. Basic linear algebra algorithm
2. Fast numerical algorithm in computing field (e.x., LU decomposition for solving the inverse of a square matrix)
3. Hardware support (e.x., parallel computation)

## Example
I will share some examples on linear algebra operations with NumPy.

## Reference
- [Linear algebra](https://en.wikipedia.org/wiki/Linear_algebra)
- [Linear algebra (numpy.linalg)](https://numpy.org/doc/stable/reference/routines.linalg.html)
