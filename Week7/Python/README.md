# Introduction to Pandas

## Let's start!
First, let's talk about what is __Pandas__!
Maybe when I mentioned "Pandas", you may think about this:
<div align="center">
  <img src="cute_pandas.jpg" height=50% width=50%/>
</div>
However, I will actually talk about this,
<div align="center">
  <img src="pandas_logo.png" height=50% width=50%/>
</div>
a widely used data analysis package in Python.

Pandas is a free and open-source python library for data manipulation, it can provide an API object for data structures, and manipulations on the structure of the numerical table, this library also supports Time Series and some plotting operations (for example, boxplot). If you are familar with database operation (ex., SQL), you will find you can use some operations with pandas easily (ex., SELECT, FULL_JOIN, LEFT_JOIN, RIGHT_JOIN, MERGE). You can also export the dataframe to a CSV file. Also, this library allows importing data from a variety of file formats like JSON, EXCEL.

__NOTE:__ There are other languages supporting equivalent operations, such as:
- R
- SQL
- STATA
- SAS

## Code snippet
<pre>
  <code>
    import numpy as np
    import pandas as pd
  </code>
</pre>

1. view data
```python
>>> pd.Series([1, 3, 5, np.nan, 6, 8])

"""
0    1.0
1    3.0
2    5.0
3    NaN
4    6.0
5    8.0
dtype: float64
"""
```

```python
>>> dates = pd.date_range("20130101", periods=6)
>>> df = pd.DataFrame(np.random.randn(6, 4), index=dates, columns=list("ABCD"))

"""
                   A         B         C         D
2013-01-01  0.469112 -0.282863 -1.509059 -1.135632
2013-01-02  1.212112 -0.173215  0.119209 -1.044236
2013-01-03 -0.861849 -2.104569 -0.494929  1.071804
2013-01-04  0.721555 -0.706771 -1.039575  0.271860
2013-01-05 -0.424972  0.567020  0.276232 -1.087401
2013-01-06 -0.673690  0.113648 -1.478427  0.524988
"""
```

```python
>>> df2 = pd.DataFrame(
   ...:     {
   ...:         "A": 1.0,
   ...:         "B": pd.Timestamp("20130102"),
   ...:         "C": pd.Series(1, index=list(range(4)), dtype="float32"),
   ...:         "D": np.array([3] * 4, dtype="int32"),
   ...:         "E": pd.Categorical(["test", "train", "test", "train"]),
   ...:         "F": "foo",
   ...:     }
   ...: )

"""
     A          B    C  D      E    F
0  1.0 2013-01-02  1.0  3   test  foo
1  1.0 2013-01-02  1.0  3  train  foo
2  1.0 2013-01-02  1.0  3   test  foo
3  1.0 2013-01-02  1.0  3  train  foo
"""

>>> df2.dtypes
"""
A           float64
B    datetime64[ns]
C           float32
D             int32
E          category
F            object
dtype: object
"""
```

```python
>>> df.head()

"""
                   A         B         C         D
2013-01-01  0.469112 -0.282863 -1.509059 -1.135632
2013-01-02  1.212112 -0.173215  0.119209 -1.044236
2013-01-03 -0.861849 -2.104569 -0.494929  1.071804
2013-01-04  0.721555 -0.706771 -1.039575  0.271860
2013-01-05 -0.424972  0.567020  0.276232 -1.087401
"""

>>> df.tail(3)

"""
                   A         B         C         D
2013-01-04  0.721555 -0.706771 -1.039575  0.271860
2013-01-05 -0.424972  0.567020  0.276232 -1.087401
2013-01-06 -0.673690  0.113648 -1.478427  0.524988
"""
```

```python
>>> df.to_numpy()

"""
array([[ 0.4691, -0.2829, -1.5091, -1.1356],
       [ 1.2121, -0.1732,  0.1192, -1.0442],
       [-0.8618, -2.1046, -0.4949,  1.0718],
       [ 0.7216, -0.7068, -1.0396,  0.2719],
       [-0.425 ,  0.567 ,  0.2762, -1.0874],
       [-0.6737,  0.1136, -1.4784,  0.525 ]])
"""

>>> df2.to_numpy()

"""
array([[1.0, Timestamp('2013-01-02 00:00:00'), 1.0, 3, 'test', 'foo'],
       [1.0, Timestamp('2013-01-02 00:00:00'), 1.0, 3, 'train', 'foo'],
       [1.0, Timestamp('2013-01-02 00:00:00'), 1.0, 3, 'test', 'foo'],
       [1.0, Timestamp('2013-01-02 00:00:00'), 1.0, 3, 'train', 'foo']],
      dtype=object)
"""
```

```python
>>> df.T

"""
   2013-01-01  2013-01-02  2013-01-03  2013-01-04  2013-01-05  2013-01-06
A    0.469112    1.212112   -0.861849    0.721555   -0.424972   -0.673690
B   -0.282863   -0.173215   -2.104569   -0.706771    0.567020    0.113648
C   -1.509059    0.119209   -0.494929   -1.039575    0.276232   -1.478427
D   -1.135632   -1.044236    1.071804    0.271860   -1.087401    0.524988
"""

>>> df.sort_index(axis=1, ascending=False)

"""
                   D         C         B         A
2013-01-01 -1.135632 -1.509059 -0.282863  0.469112
2013-01-02 -1.044236  0.119209 -0.173215  1.212112
2013-01-03  1.071804 -0.494929 -2.104569 -0.861849
2013-01-04  0.271860 -1.039575 -0.706771  0.721555
2013-01-05 -1.087401  0.276232  0.567020 -0.424972
2013-01-06  0.524988 -1.478427  0.113648 -0.673690
"""
```

2. selection
```python
>>> df["A"]

"""
2013-01-01    0.469112
2013-01-02    1.212112
2013-01-03   -0.861849
2013-01-04    0.721555
2013-01-05   -0.424972
2013-01-06   -0.673690
Freq: D, Name: A, dtype: float64
"""

>>> df[0:3]

"""
                   A         B         C         D
2013-01-01  0.469112 -0.282863 -1.509059 -1.135632
2013-01-02  1.212112 -0.173215  0.119209 -1.044236
2013-01-03 -0.861849 -2.104569 -0.494929  1.071804
"""

>>> df["20130102":"20130104"]

"""
                   A         B         C         D
2013-01-02  1.212112 -0.173215  0.119209 -1.044236
2013-01-03 -0.861849 -2.104569 -0.494929  1.071804
2013-01-04  0.721555 -0.706771 -1.039575  0.271860
"""

>>> df[df["A"] > 0]

"""
                   A         B         C         D
2013-01-01  0.469112 -0.282863 -1.509059 -1.135632
2013-01-02  1.212112 -0.173215  0.119209 -1.044236
2013-01-04  0.721555 -0.706771 -1.039575  0.271860
"""
```

3. operation

```python
>>> df.mean()

"""
A   -0.004474
B   -0.383981
C   -0.687758
D    5.000000
F    3.000000
dtype: float64
"""

>>> s = pd.Series(["A", "B", "C", "Aaba", "Baca", np.nan, "CABA", "dog", "cat"])
>>> s.str.lower()

"""
0       a
1       b
2       c
3    aaba
4    baca
5     NaN
6    caba
7     dog
8     cat
dtype: object
"""
```

4. merge
```python
>>> df = pd.DataFrame(np.random.randn(10, 4))
>>> df

"""
          0         1         2         3
0 -0.548702  1.467327 -1.015962 -0.483075
1  1.637550 -1.217659 -0.291519 -1.745505
2 -0.263952  0.991460 -0.919069  0.266046
3 -0.709661  1.669052  1.037882 -1.705775
4 -0.919854 -0.042379  1.247642 -0.009920
5  0.290213  0.495767  0.362949  1.548106
6 -1.131345 -0.089329  0.337863 -0.945867
7 -0.932132  1.956030  0.017587 -0.016692
8 -0.575247  0.254161 -1.143704  0.215897
9  1.193555 -0.077118 -0.408530 -0.862495
"""


>>> pieces = [df[:3], df[3:7], df[7:]]
>>> pd.concat(pieces)

"""
          0         1         2         3
0 -0.548702  1.467327 -1.015962 -0.483075
1  1.637550 -1.217659 -0.291519 -1.745505
2 -0.263952  0.991460 -0.919069  0.266046
3 -0.709661  1.669052  1.037882 -1.705775
4 -0.919854 -0.042379  1.247642 -0.009920
5  0.290213  0.495767  0.362949  1.548106
6 -1.131345 -0.089329  0.337863 -0.945867
7 -0.932132  1.956030  0.017587 -0.016692
8 -0.575247  0.254161 -1.143704  0.215897
9  1.193555 -0.077118 -0.408530 -0.862495
"""
```

```python
>>> left = pd.DataFrame({"key": ["foo", "foo"], "lval": [1, 2]})
>>> right = pd.DataFrame({"key": ["foo", "foo"], "rval": [4, 5]})

>>> left
"""
   key  lval
0  foo     1
1  foo     2
"""

>>> right
"""
   key  rval
0  foo     4
1  foo     5
"""

>>> pd.merge(left, right, on="key")

"""
   key  lval  rval
0  foo     1     4
1  foo     1     5
2  foo     2     4
3  foo     2     5
"""
```

5. plot
```python
>>> ts = pd.Series(np.random.randn(1000), index=pd.date_range("1/1/2000", periods=1000))
>>> ts = ts.cumsum()
>>> ts.plot()
```

## Reference
- [wikipedia: pandas (software)](https://en.wikipedia.org/wiki/Pandas_(software))
- [Matplotlib VS Ggplot2](https://towardsdatascience.com/matplotlib-vs-ggplot2-c86dd35a9378)
- [Pandas official site](https://pandas.pydata.org/)
- [tutorial](https://pandas.pydata.org/docs/user_guide/10min.html#min)

