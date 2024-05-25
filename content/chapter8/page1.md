+++
title = "ファイルの読み書き"
weight = 9
+++

Pythonでは、ファイルの読み書きを簡単に行うことができます。ファイルの操作はデータの保存や取得に不可欠であり、Pythonの組み込み関数を使うことで容易に実行できます。この章では、ファイルの書き込みと読み込みの基本的な方法を学びます。

---

### ファイルの書き込み

ファイルにデータを書き込むためには、`open` 関数を使用してファイルを開き、`write` メソッドを使ってデータをファイルに書き込みます。ファイルを開くときのモードとしては、書き込みモード（`"w"`）を使用します。

```python
# ファイルの書き込み
with open("example.txt", "w") as file:
    file.write("Hello, World!")
```

この例では、`example.txt` というファイルを開き、"Hello, World!" という文字列を書き込んでいます。`with` ステートメントを使うことで、ファイルのクローズ処理を自動的に行います。

---

### ファイルの読み込み

ファイルからデータを読み込むためには、`open` 関数を使用してファイルを開き、`read` メソッドを使ってデータを読み込みます。ファイルを開くときのモードとしては、読み込みモード（`"r"`）を使用します。

```python
# ファイルの読み込み
with open("example.txt", "r") as file:
    content = file.read()
    print(content)
```

この例では、`example.txt` というファイルを開き、その内容を読み込んで表示しています。

---

### 追記モードでのファイル操作

ファイルにデータを追加するためには、追記モード（`"a"`）を使用します。

```python
# ファイルへの追記
with open("example.txt", "a") as file:
    file.write("\nAppend this line.")
```

この例では、`example.txt` に新しい行を追加しています。既存の内容は保持されたまま、新しいデータが追加されます。

---

### 行単位でのファイル読み込み

ファイルの内容を行単位で読み込むためには、`readline` メソッドまたは `readlines` メソッドを使用します。

```python
# readlineを使って一行ずつ読み込む
with open("example.txt", "r") as file:
    line = file.readline()
    while line:
        print(line.strip())
        line = file.readline()

# readlinesを使ってすべての行をリストとして読み込む
with open("example.txt", "r") as file:
    lines = file.readlines()
    for line in lines:
        print(line.strip())
```

---

### ファイルのモード

ファイルを開くときには、以下のようなモードを指定することができます：

- `"r"`：読み込みモード（デフォルト）
- `"w"`：書き込みモード（ファイルが存在する場合は内容を消去）
- `"a"`：追記モード
- `"b"`：バイナリモード
- `"t"`：テキストモード（デフォルト）
- `"+"`：読み書きモードの併用

例：

```python
# バイナリモードでのファイル操作
with open("example.bin", "wb") as file:
    file.write(b"\x00\x01\x02\x03")
```

---

### ファイルの位置操作

ファイルの読み書きの際に、ファイルの現在の位置を操作するためのメソッドも用意されています。

- `seek(offset, whence)`：ファイルの現在の位置を設定する
- `tell()`：ファイルの現在の位置を返す

例：

```python
# ファイルの位置操作
with open("example.txt", "r") as file:
    print(file.read(5))  # 最初の5文字を読み込む
    print(file.tell())   # 現在の位置を表示
    file.seek(0)         # ファイルの先頭に戻る
    print(file.read(5))  # 再び最初の5文字を読み込む
```

---

### CSVファイルの読み書き

CSVファイルは、カンマ区切りのデータを扱うためのファイル形式です。Pythonの `csv` モジュールを使って簡単に読み書きができます。

```python
import csv

# CSVファイルの書き込み
with open("example.csv", "w", newline='') as file:
    writer = csv.writer(file)
    writer.writerow(["Name", "Age"])
    writer.writerow(["Alice", 25])
    writer.writerow(["Bob", 30])

# CSVファイルの読み込み
with open("example.csv", "r") as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)
```

---

### JSONファイルの読み書き

JSONファイルは、データを構造化して保存するためのファイル形式です。Pythonの `json` モジュールを使って簡単に読み書きができます。

```python
import json

data = {
    "name": "Alice",
    "age": 25,
    "city": "New York"
}

# JSONファイルの書き込み
with open("example.json", "w") as file:
    json.dump(data, file)

# JSONファイルの読み込み
with open("example.json", "r") as file:
    data = json.load(file)
    print(data)
```

---

## まとめ

この章では、Pythonでのファイルの読み書きについて学びました。ファイル操作は、データの保存と取得に不可欠なスキルです。次の章では、エラー処理について学びます。エラー処理を理解することで、プログラムの信頼性と安定性を向上させることができます。
