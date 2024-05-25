+++
title = "pandasの基本"
weight = 12
+++

pandasは、データ操作や分析を簡単に行うためのライブラリです。DataFrameを使ってデータを操作し、データの読み込み、書き込み、変換、フィルタリングなどを行います。この章では、pandasの基本的な使い方について学びます。

---

### pandasのインポート

まず、pandasライブラリをインポートします。通常、`pd` という別名を使用してインポートします。

```python
import pandas as pd
```

---

### DataFrameの作成

DataFrameは、pandasでデータを扱うための主要なデータ構造です。辞書やリストからDataFrameを作成することができます。

```python
# 辞書からDataFrameを作成
data = {"Name": ["Alice", "Bob"], "Age": [25, 30]}
df = pd.DataFrame(data)
print(df)
# 出力:
#     Name  Age
# 0  Alice   25
# 1    Bob   30
```

リストやタプルを使ってもDataFrameを作成できます。

```python
# リストからDataFrameを作成
data = [["Alice", 25], ["Bob", 30]]
df = pd.DataFrame(data, columns=["Name", "Age"])
print(df)
# 出力:
#     Name  Age
# 0  Alice   25
# 1    Bob   30
```

---

### データの読み込みと書き込み

pandasは、CSV、Excel、SQL、JSONなど、さまざまな形式のデータを読み込むことができます。

```python
# CSVファイルの読み込み
df = pd.read_csv("data.csv")
print(df)

# CSVファイルへの書き込み
df.to_csv("output.csv", index=False)

# Excelファイルの読み込み
df = pd.read_excel("data.xlsx", sheet_name="Sheet1")
print(df)

# Excelファイルへの書き込み
df.to_excel("output.xlsx", index=False, sheet_name="Sheet1")
```

---

### データのフィルタリング

DataFrameを使ってデータをフィルタリングすることで、特定の条件に一致する行を抽出できます。

```python
# 条件に一致する行の抽出
filtered_df = df[df["Age"] > 25]
print(filtered_df)
# 出力:
#   Name  Age
# 1  Bob   30
```

---

### データの選択と抽出

pandasでは、列や行を選択してデータを抽出する方法がいくつかあります。

```python
# 列の選択
names = df["Name"]
print(names)
# 出力:
# 0    Alice
# 1      Bob
# Name: Name, dtype: object

# 複数の列の選択
subset = df[["Name", "Age"]]
print(subset)
# 出力:
#     Name  Age
# 0  Alice   25
# 1    Bob   30

# 行の選択（ラベルで指定）
first_row = df.loc[0]
print(first_row)
# 出力:
# Name    Alice
# Age        25
# Name: 0, dtype: object

# 行の選択（インデックスで指定）
first_row = df.iloc[0]
print(first_row)
# 出力:
# Name    Alice
# Age        25
# Name: 0, dtype: object
```

---

### データの追加と削除

新しい列を追加したり、既存の列を削除したりすることができます。

```python
# 新しい列の追加
df["City"] = ["New York", "Los Angeles"]
print(df)
# 出力:
#     Name  Age         City
# 0  Alice   25     New York
# 1    Bob   30  Los Angeles

# 列の削除
df = df.drop("City", axis=1)
print(df)
# 出力:
#     Name  Age
# 0  Alice   25
# 1    Bob   30

# 行の削除
df = df.drop(0, axis=0)
print(df)
# 出力:
#   Name  Age
# 1  Bob   30
```

---

### データの集計と統計

pandasは、データの集計や統計計算のための便利なメソッドを提供しています。

```python
# 基本統計量の計算
print(df.describe())
# 出力:
#              Age
# count   2.000000
# mean   27.500000
# std     3.535534
# min    25.000000
# 25%    26.250000
# 50%    27.500000
# 75%    28.750000
# max    30.000000

# グループ化と集計
grouped_df = df.groupby("City").mean()
print(grouped_df)
# 出力:
#                   Age
# City                
# Los Angeles  30.000000
# New York     25.000000
```

---

### 欠損値の処理

pandasでは、データの欠損値を検出し、処理するためのメソッドも豊富に用意されています。

```python
# 欠損値の検出
print(df.isnull())
# 出力:
#     Name    Age
# 0  False  False
# 1  False  False

# 欠損値の除去
df = df.dropna()
print(df)

# 欠損値の埋める
df = df.fillna({"Age": 0})
print(df)
```

---

## まとめ

この章では、pandasの基本的な使い方について学びました。pandasは、データの操作と分析のための強力なツールを提供します。次の章では、matplotlibによるデータの可視化について学びます。データを視覚的に表現することで、洞察を得ることができます。
