+++
title = "matplotlibによるデータ可視化"
weight = 12
+++

matplotlibは、データの可視化を行うための強力なライブラリです。グラフやチャートを簡単に作成し、データの視覚化によって洞察を得ることができます。この章では、matplotlibの基本的な使い方について学びます。

---

### matplotlibのインポート

matplotlibを使用するには、まずライブラリをインポートします。通常、`pyplot` モジュールを `plt` という別名でインポートします。

```python
import matplotlib.pyplot as plt
```

---

### 基本的な折れ線グラフの作成

matplotlibを使って基本的な折れ線グラフを作成する例を示します。

```python
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

この例では、`plot` 関数を使ってデータをプロットし、`xlabel`、`ylabel`、`title` を使ってラベルとタイトルを設定しています。`show` 関数を呼び出してグラフを表示します。

---

### 散布図の作成

散布図は、データの分布を視覚的に表現するのに適しています。

```python
import matplotlib.pyplot as plt

# データの準備
x = [1, 2, 3, 4, 5]
y = [1, 4, 9, 16, 25]

# 散布図の作成
plt.scatter(x, y)
plt.xlabel("X軸")
plt.ylabel("Y軸")
plt.title("散布図")
plt.show()
```

この例では、`scatter` 関数を使って散布図を作成しています。

---

### 棒グラフの作成

棒グラフは、カテゴリごとの値を比較するのに適しています。

```python
import matplotlib.pyplot as plt

# データの準備
categories = ["A", "B", "C", "D", "E"]
values = [5, 7, 3, 8, 4]

# 棒グラフの作成
plt.bar(categories, values)
plt.xlabel("カテゴリ")
plt.ylabel("値")
plt.title("棒グラフ")
plt.show()
```

この例では、`bar` 関数を使って棒グラフを作成しています。

---

### ヒストグラムの作成

ヒストグラムは、データの分布を視覚的に表現するのに適しています。

```python
import matplotlib.pyplot as plt

# データの準備
data = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4, 5, 5, 5, 5, 5]

# ヒストグラムの作成
plt.hist(data, bins=5)
plt.xlabel("値")
plt.ylabel("頻度")
plt.title("ヒストグラム")
plt.show()
```

この例では、`hist` 関数を使ってヒストグラムを作成しています。`bins` パラメータを使って、ヒストグラムのビン（区間）の数を指定しています。

---

### 複数のグラフを一つの図に表示

複数のグラフを一つの図に表示するためには、`subplot` 関数を使用します。

```python
import matplotlib.pyplot as plt

# データの準備
x = [1, 2, 3, 4, 5]
y1 = [1, 4, 9, 16, 25]
y2 = [1, 2, 3, 4, 5]

# 図の作成
plt.figure(figsize=(10, 5))

# 最初のグラフ
plt.subplot(1, 2, 1)
plt.plot(x, y1)
plt.title("グラフ1")

# 二つ目のグラフ
plt.subplot(1, 2, 2)
plt.plot(x, y2)
plt.title("グラフ2")

plt.show()
```

この例では、`subplot` 関数を使って2つのグラフを1つの図に表示しています。`figure` 関数を使って図のサイズを設定しています。

---

### カスタマイズ

matplotlibでは、グラフのスタイルをカスタマイズするための様々なオプションが提供されています。色、線のスタイル、マーカー、凡例などを設定することができます。

```python
import matplotlib.pyplot as plt

# データの準備
x = [1, 2, 3, 4, 5]
y = [1, 4, 9, 16, 25]

# カスタマイズされたグラフの作成
plt.plot(x, y, color='green', linestyle='--', marker='o', label='データ')
plt.xlabel("X軸")
plt.ylabel("Y軸")
plt.title("カスタマイズされたグラフ")
plt.legend()
plt.grid(True)
plt.show()
```

この例では、`color`、`linestyle`、`marker` パラメータを使って線の色、スタイル、マーカーを設定し、`legend` 関数で凡例を表示し、`grid` 関数でグリッド線を表示しています。

---

## まとめ

この章では、matplotlibを使ったデータの可視化について学びました。matplotlibは、データの視覚化において強力なツールを提供し、様々な種類のグラフやチャートを作成できます。次の章では、ウェブスクレイピングについて学びます。ウェブスクレイピングを使って、ウェブサイトからデータを自動的に取得する方法を理解しましょう。
