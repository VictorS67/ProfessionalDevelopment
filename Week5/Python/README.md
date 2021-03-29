# Introduction to PyTorch

## Introduction
<div align="center">
  <img src="./pytorch.jpg" alt="figure 1: logo" width=50% height=50%/>
</div>

**PyTorch** is an open source library in Python for machine learning developped by Facebook, based on the package *Torch*. Except for machine learning, this package is also used in computer vision and natural language processing. There are mainly two high-level features for PyTorch library:
- strong GPU acceleration by applying NumPy-like tensors
- Automatic differentiation system for deep neural neural network

## Features of PyTorch library
1. Tensors: vector in PyTorch (like NumPy array)
2. Datasets & DataLoaders: load and manipulate dataset
3. Transforms: transform and manipulate data representation in PyTorch (ex., Tensor)
4. Model: build models, like convolutional neural network (CNN), recurrent neural network (RNN), generative adversarial network (GAN)
5. Automatic differentiation: solving backpropagation - find gradient for loss with each parameter in the model in each turn of training
6. optimization: optimize the parameters (ex., gradient descent, stochastic gradient descent)
7. save and load model

## Code Snippet
- Tensor
```Python
>>> x = torch.tensor([1.0, 2.0, 3.0, 4.0])
>>> x
tensor([1., 2., 3., 4.])

>>> x_np = np.array([1.0, 2.0, 3.0, 4.0], dtype=np.float32)
>>> x = torch.from_numpy(x_np)

# Torch abstracts over NumPy but uses a NumPy-compatible representation under the hood
>>> x_np[0] = 100.0
>>> x[1] = 200.0
>>> x.data.numpy()[2] = 300

>>> x
tensor([100., 200., 300.,   4.])

# Broadcasting
>>> x.reshape(-1, 1) + x

tensor([[200., 300., 400., 104.],
        [300., 400., 500., 204.],
        [400., 500., 600., 304.],
        [104., 204., 304.,   8.]])

# Dot product
>>> x @ x.T
tensor(140016.)
```

## Reference
- [Wikipedia: PyTorch](https://en.wikipedia.org/wiki/PyTorch)
- [PyTorch official tutorial](https://pytorch.org/tutorials/beginner/basics/data_tutorial.html)
