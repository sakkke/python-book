+++
title = "CSVファイルの操作"
weight = 9
+++

CSVファイルは、データを表形式で保存するための一般的なフォーマットです。Pythonの `csv` モジュールを使って、CSVファイルを簡単に操作できます。この章では、CSVファイルの読み書き方法や様々な操作について学びます。

---

### CSVファイルの書き込み

CSVファイルにデータを書き込むには、`csv.writer` オブジェクトを使用します。`writerow` メソッドを使って、1行ずつデータを書き込みます。

```python
import csv

# CSVファイルの書き込み
with open("example.csv", "w", newline='') as file:
    writer = csv.writer(file)
    writer.writerow(["Name", "Age"])
    writer.writerow(["Alice", 25])
    writer.writerow(["Bob", 30])
```

この例では、`example.csv` というファイルにデータを行単位で書き込んでいます。`newline=''` を指定することで、行の間に空行が挿入されるのを防ぎます。

---

### CSVファイルの読み込み

CSVファイルからデータを読み込むには、`csv.reader` オブジェクトを使用します。`reader` オブジェクトをイテレートして各行のデータを取得します。

```python
import csv

# CSVファイルの読み込み
with open("example.csv", "r") as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)
```

この例では、`example.csv` というファイルからデータを読み込み、各行をリストとして表示しています。

---

### 辞書形式でのCSVファイル操作

CSVファイルを辞書形式で操作するためには、`csv.DictWriter` と `csv.DictReader` を使用します。これにより、列名をキーとして各行を辞書として操作できます。

#### 辞書形式での書き込み

```python
import csv

# 辞書形式でのCSVファイルの書き込み
with open("example_dict.csv", "w", newline='') as file:
    fieldnames = ["Name", "Age"]
    writer = csv.DictWriter(file, fieldnames=fieldnames)

    writer.writeheader()  # ヘッダー行の書き込み
    writer.writerow({"Name": "Alice", "Age": 25})
    writer.writerow({"Name": "Bob", "Age": 30})
```

この例では、`example_dict.csv` というファイルに辞書形式でデータを書き込んでいます。`writeheader` メソッドを使ってヘッダー行を追加しています。

#### 辞書形式での読み込み

```python
import csv

# 辞書形式でのCSVファイルの読み込み
with open("example_dict.csv", "r") as file:
    reader = csv.DictReader(file)
    for row in reader:
        print(row)
```

この例では、`example_dict.csv` というファイルからデータを読み込み、各行を辞書として表示しています。

---

### CSVファイルの高度な操作

`csv` モジュールには、様々なオプションを指定してCSVファイルを操作する機能があります。

#### 区切り文字の変更

デフォルトでは、CSVファイルの区切り文字はカンマですが、他の区切り文字を使用することもできます。

```python
import csv

# セミコロン区切りのCSVファイルの書き込み
with open("example_semicolon.csv", "w", newline='') as file:
    writer = csv.writer(file, delimiter=';')
    writer.writerow(["Name", "Age"])
    writer.writerow(["Alice", 25])
    writer.writerow(["Bob", 30])

# セミコロン区切りのCSVファイルの読み込み
with open("example_semicolon.csv", "r") as file:
    reader = csv.reader(file, delimiter=';')
    for row in reader:
        print(row)
```

この例では、区切り文字としてセミコロンを使用してCSVファイルを読み書きしています。

#### クオートスタイルの設定

`csv` モジュールでは、フィールドのクオートスタイルを指定することができます。

```python
import csv

# クオートスタイルの設定
with open("example_quote.csv", "w", newline='') as file:
    writer = csv.writer(file, quoting=csv.QUOTE_ALL)
    writer.writerow(["Name", "Age"])
    writer.writerow(["Alice", 25])
    writer.writerow(["Bob", 30])

# クオートスタイルの読み込み
with open("example_quote.csv", "r") as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)
```

この例では、すべてのフィールドをクオートするように設定しています。

---

### pandasを使ったCSVファイル操作

`pandas` ライブラリを使うと、CSVファイルの読み書きがより簡単かつ強力になります。`pandas` はデータ解析のための強力なツールを提供しています。

#### pandasでのCSVファイル読み込み

```python
import pandas as pd

# CSVファイルの読み込み
df = pd.read_csv("example.csv")
print(df)
```

#### pandasでのCSVファイル書き込み

```python
import pandas as pd

# データフレームの作成
df = pd.DataFrame({"Name": ["Alice", "Bob"], "Age": [25, 30]})

# CSVファイルへの書き込み
df.to_csv("example_pandas.csv", index=False)
```

この例では、`pandas` を使ってCSVファイルを読み書きしています。`pandas` はデータの操作や解析に非常に便利です。

---

## まとめ

この章では、PythonでのCSVファイルの操作方法について学びました。`csv` モジュールや `pandas` ライブラリを使うことで、CSVファイルを簡単に読み書きすることができます。次の章では、JSONファイルの操作について学びます。JSONは、データを構造化して保存するための一般的なフォーマットです。
