---
layout: post
title: Some Notes
---
```python
def two_three_strings(x):
  return x*2, x*3

df4['twice'],df4['thrice'] = zip(*df4['int_col'].map(two_three_strings))

In [46]: df4
Out[46]:
   float_col  int_col str_col  twice  thrice
0        0.1        1       a      2       3
1        0.2        2       b      4       6
2        0.2        6    None     12      18
3       10.1        8       c     16      24
4        NaN       -1       a     -2      -3
```
