+++
title = "NumPyの基本"
weight = 12
+++

NumPy（Numerical Python）は、数値計算を効率的に行うための強力なライブラリです。多次元配列（ndarray）の操作や数学的関数を提供し、科学技術計算やデータ解析で広く使用されています。この章では、NumPyの基本的な使い方について学びます。

---

### NumPyのインポート

NumPyを使用するには、まずライブラリをインポートします。通常、`np` という別名を使用してインポートします。

```python
import numpy as np
```

---

### 配列の作成

NumPy配列（ndarray）は、リストやタプルを使って作成できます。

```python
import numpy as np

# 1次元配列の作成
a = np.array([1, 2, 3, 4, 5])
print(a)  # 出力: [1 2 3 4 5]

# 2次元配列の作成
b = np.array([[1, 2, 3], [4, 5, 6]])
print(b)
# 出力:
# [[1 2 3]
#  [4 5 6]]
```

---

### 配列の基本操作

NumPyでは、配列の形状変更や基本的な演算を効率的に行うことができます。

```python
# 配列の形状
print(a.shape)  # 出力: (5,)
print(b.shape)  # 出力: (2, 3)

# 配列の型
print(a.dtype)  # 出力: int64（環境によって異なる場合があります）

# 配列の要素数
print(a.size)  # 出力: 5

# 配列の次元数
print(a.ndim)  # 出力: 1
print(b.ndim)  # 出力: 2
```

---

### 配列の基本演算

NumPy配列は、基本的な数学演算を要素ごとに効率的に行うことができます。

```python
# 配列の基本演算
b = a * 2
print(b)  # 出力: [ 2  4  6  8 10]

c = a + b
print(c)  # 出力: [ 3  6  9 12 15]
```

---

### 配列のスライシング

配列の部分配列を取得するためのスライシングも簡単に行えます。

```python
# 配列のスライシング
d = a[1:4]
print(d)  # 出力: [2 3 4]

# 2次元配列のスライシング
e = b[:, 1:3]
print(e)
# 出力:
# [[ 4  6]
#  [10 12]]
```

---

### 特殊な配列の作成

NumPyは、特殊な配列を簡単に作成するための関数を提供しています。

```python
# ゼロ配列の作成
zeros = np.zeros((2, 3))
print(zeros)
# 出力:
# [[0. 0. 0.]
#  [0. 0. 0.]]

# 1配列の作成
ones = np.ones((2, 3))
print(ones)
# 出力:
# [[1. 1. 1.]
#  [1. 1. 1.]]

# 単位行列の作成
identity = np.eye(3)
print(identity)
# 出力:
# [[1. 0. 0.]
#  [0. 1. 0.]
#  [0. 0. 1.]]

# 等差数列の配列の作成
range_array = np.arange(0, 10, 2)
print(range_array)  # 出力: [0 2 4 6 8]

# ランダム配列の作成
random_array = np.random.rand(2, 3)
print(random_array)
# 出力: （ランダムな値を含む2x3の配列）
```

---

### 配列の形状変更

配列の形状を変更するための `reshape` 関数も非常に便利です。

```python
# 1次元配列から2次元配列への変換
f = np.arange(6)
print(f)
# 出力: [0 1 2 3 4 5]

reshaped_f = f.reshape((2, 3))
print(reshaped_f)
# 出力:
# [[0 1 2]
#  [3 4 5]]
```

---

### 配列の結合と分割

NumPyでは、配列の結合や分割も簡単に行うことができます。

```python
# 配列の結合
g = np.array([1, 2, 3])
h = np.array([4, 5, 6])
concatenated = np.concatenate((g, h))
print(concatenated)  # 出力: [1 2 3 4 5 6]

# 配列の分割
split_array = np.split(concatenated, 3)
print(split_array)
# 出力: [array([1, 2]), array([3, 4]), array([5, 6])]
```

---

## まとめ

この章では、NumPyの基本的な使い方について学びました。NumPyは多次元配列の操作や数学的演算を効率的に行うための強力なツールです。次の章では、pandasライブラリを使ったデータ解析について学びます。pandasは、データの操作と分析のための高レベルのデータ構造と関数を提供します。
