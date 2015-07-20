---
layout: post
title: Some Notes
---
### Generate new column(s) from existing column(s)
[***Source](http://manishamde.github.io/blog/2013/03/07/pandas-and-python-top-10/)

#### 1. Multiple columns from a single column
```python
In [43]: df4 = df.copy()

In [44]: def two_three_strings(x):
   ....:   return x*2, x*3
   ....:

In [45]: df4['twice'],df4['thrice'] = zip(*df4['int_col'].map(two_three_strings))

In [46]: df4
Out[46]:
   float_col  int_col str_col  twice  thrice
0        0.1        1       a      2       3
1        0.2        2       b      4       6
2        0.2        6    None     12      18
3       10.1        8       c     16      24
4        NaN       -1       a     -2      -3
```

#### Single column from multiple columns
```python
In [48]: def sum_two_cols(series):
   ....:   return series['int_col'] + series['float_col']
   ....:

In [49]: df5['sum_col'] = df5.apply(sum_two_cols,axis=1)

In [50]: df5
Out[50]:
   float_col  int_col str_col  sum_col
0        0.1        1       a      1.1
1        0.2        2       b      2.2
2        0.2        6    None      6.2
3       10.1        8       c     18.1
4        NaN       -1       a      NaN
```

#### Multiple columns from multiple columns
```python
In [51]: import math

In [52]: def int_float_squares(series):
   ....:   return pd.Series({'int_sq' : series['int_col']**2, 'flt_sq' : series['float_col']**2})
   ....:

In [53]: df.apply(int_float_squares, axis = 1)
Out[53]:
   flt_sq  int_sq
0    0.01       1
1    0.04       4
2    0.04      36
3  102.01      64
4     NaN       1
```
