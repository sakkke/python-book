+++
title = "matplotlibによるデータ可視化"
weight = 12
+++

matplotlibは、データの可視化を行うためのライブラリです。グラフやチャートを作成できます。

```python
import matplotlib.pyplot as plt

# データの準備
x = [1, 2, 3, 4, 5]
y = [1, 4, 9, 16, 25]

# グラフの作成
plt.plot(x, y)
plt.xlabel("X軸")
plt.ylabel("Y軸")
plt.title("XとYの関係")
plt.show()
```
