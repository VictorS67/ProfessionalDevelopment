# General introduction about NumPy & SciPy

## Overall introduction
Python is a powerful language for rich source of data science tools. And NumPy and SciPy family is one of the packages frequently used in mathematical computation in Python, which is a good replacement for MatLab. If you are seeking for free and efficient software, SciPy might be a good choice.

<div align='center'>
    <img src="symbol.png" alt="Figure 1: SciPy familily symbol">
</div>

SciPy family has a modules for linear algebra, optimization, interpolation, image processing and so on, which are often used in fields like statistics, data secience & analysis, machine learning and engineering. The NumPy array is strong in time and memory efficiency, which supports fast computation, and much more efficient than barely using iterations. The NumPy array is strong because it has been optimized by parallel programming and more advanced algorithm, I will list examples later. Also, other Python modules, like Matplotlib, Pandas, Autograd and PyTorch extend NumPy array to support their functionality, which makes the array very portable.

"(from scipy official webpage) SciPy (pronounced “Sigh Pie”) is a Python-based ecosystem of open-source software for mathematics, science, and engineering. In particular, these are some of the core packages:"
<div align="center">
    <img src="family.png" alt="Figure 2: SciPy family">
</div>

## Code snippet
In this section, I will show some interesting code snippets for SciPy and NumPy functionality.
```python
# from Python Numpy Tutorial (with Jupyter and Colab) by CS231n: Convolutional Neural Networks for Visual Recognition
# of Stanford
from scipy.misc import imread, imsave, imresize

# Read an JPEG image into a numpy array
img = imread('assets/cat.jpg')
print(img.dtype, img.shape)  # Prints "uint8 (400, 248, 3)"

# We can tint the image by scaling each of the color channels
# by a different scalar constant. The image has shape (400, 248, 3);
# we multiply it by the array [1, 0.95, 0.9] of shape (3,);
# numpy broadcasting means that this leaves the red channel unchanged,
# and multiplies the green and blue channels by 0.95 and 0.9
# respectively.
img_tinted = img * [1, 0.95, 0.9]

# Resize the tinted image to be 300 by 300 pixels.
img_tinted = imresize(img_tinted, (300, 300))

# Write the tinted image back to disk
imsave('assets/cat_tinted.jpg', img_tinted)
```

## References
- Figure 1: [SciPy](https://se.ewi.tudelft.nl/desosa2019/chapters/scipy/)
- [SciPy](https://en.wikipedia.org/wiki/SciPy)
- [SciPy.org](https://www.scipy.org)
- [Python Numpy Tutorial (with Jupyter and Colab)](https://cs231n.github.io/python-numpy-tutorial/)
